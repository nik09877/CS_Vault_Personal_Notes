## Show Drop Down Table Data

##### Solution
Reduced 12 queries to single query 80% reduction, reduced, DAO impl code by 60%


## query optimization pagination and caching

Infinite API calls -> if spinnerCount == 1 show table, but it was stuck in infinite loop, removed the spinnerCount condition then it worked

used index scan approach for pagination instead of LIMIT and OFFSET, which improved the performance very much

4.96s ----> 3.28ms (units)
2.92s -----> 2.45s (portfolios)
7.21s -----> 3.97s (projects)
2.51s ------> 2.38s (Applications)
			(vulnerability)
4.7s -------> 2.5s (assessment)


## UI Problem 

In Hello Canada work the backend was sending the html template for the mail section in icici which had links, so while converting to IOS app the links were not opening in a new window, so what we did was we sent header,body and links as api response to ffrontend and there used another library so that for ios the links will open in new window

## Notification Feature End to End 

- CREATE, UPDATE, DELETE by admin
- For each User **Clear** a particular notification, **Clear ALL** notifications
- Used 2 tables , notification table another one has user id , cleared notification id
- while creating notification if we attach image , every image size is diff, so before sending to backend i added width and height to it
- Thought of using websocket, but notifications are created rarely once in a month, so
- notification count is fetched based on timestamp stored in localstorage, seen till timestamp is stored in localstorage, after that using query fetch notification count having timestamp greater than current seen timestamp

## PT and ARM integration using RestTemplate

## Dynamic Configuration Management using Netflix Archaius
without restarting the server or redploying it , we are updating the UI by simply changing the config.properties file

#### challenges
- It was difficult to match the versions with the spring boot version, lastly used 0.6.0 which was depricated
- followed netflix github repo, it was difficult as well to find the specific version code

## Batch schedule processing

there is armId, documentId, closure date and list of persons to send mail to 7 days prior to closure date everyday till the closure date.

-  Fetch documents whose closure date is within the next 7 days


#### Explanation of `@Scheduled` Annotation

The `@Scheduled` annotation is used in Spring Boot to schedule tasks to be executed at specific intervals or times. It uses cron expressions to define when the scheduled task should run. Here’s a breakdown of the cron expression you provided :

`@Scheduled(cron = "0 0 8 * * ?")`

This cron expression translates to:

- **`0`** - The seconds field. The task starts at the 0th second.
- **`0`** - The minutes field. The task starts at the 0th minute.
- **`8`** - The hour field. The task starts at 8 AM.
- **`*`** - The day of the month field. The task runs every day of the month.
- **`*`** - The month field. The task runs every month.
- **`?`** - The day of the week field. The task runs every day of the week, without specifying a particular day.

So the expression `0 0 8 * * ?` means the task will run **every day at 8:00 AM**.

#### Explanation of the Configuration Class

The configuration class is where the scheduling is set up:


```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.annotation.EnableScheduling;
import org.springframework.scheduling.annotation.Scheduled;

@Configuration
@EnableScheduling
public class SchedulerConfig {

    @Autowired
    private EmailNotificationService emailNotificationService;

    // Run the task every day at 8:00 AM
    @Scheduled(cron = "0 0 8 * * ?")
    public void scheduleEmailNotifications() {
        emailNotificationService.sendReminderEmails();
    }
}

```

- **`@Configuration`**: This annotation indicates that the class is a configuration class, where beans and settings are defined for the Spring application context.
    
- **`@EnableScheduling`**: This annotation enables Spring's scheduled task execution capability, allowing the application to run methods annotated with `@Scheduled`.
    
- **`@Scheduled(cron = "0 0 8 * * ?")`**: As explained above, this annotation specifies that the `scheduleEmailNotifications` method will be executed every day at 8:00 AM.
    
- **`scheduleEmailNotifications()`**: This method calls the `sendReminderEmails` method of the `EmailNotificationService` class, which handles the logic for fetching documents nearing their closure dates and sending reminder emails.
    

#### Modifying the Code to Send Emails for Closure Dates <= 7 Days in the Future

To send emails to individuals whose document closure date is less than or equal to 7 days in the future, we need to modify the query logic to include documents that are within this range.

##### Step 1: Update the Repository Query

Modify the `ArmRepository` to fetch documents with a closure date within the next 7 days:

```java
package com.example.emailbatch.repository;

import com.example.emailbatch.entity.Arm;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;
import java.time.LocalDate;
import java.util.List;

public interface ArmRepository extends JpaRepository<Arm, Long> {
    // Fetch documents with closure date within the next 7 days
    @Query("SELECT a FROM Arm a WHERE a.closureDate BETWEEN :today AND :targetDate")
    List<Arm> findDocumentsWithClosureDateInRange(@Param("today") LocalDate today, @Param("targetDate") LocalDate targetDate);
}

```
##### Step 2: Update the Service Logic

Modify the `EmailNotificationService` to use the updated query:

```java
package com.example.emailbatch.service;

import com.example.emailbatch.entity.Arm;
import com.example.emailbatch.entity.DocumentClosureResponsible;
import com.example.emailbatch.repository.ArmRepository;
import com.example.emailbatch.repository.DocumentClosureResponsibleRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.mail.SimpleMailMessage;
import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.util.List;

@Service
public class EmailNotificationService {

    @Autowired
    private ArmRepository armRepository;

    @Autowired
    private DocumentClosureResponsibleRepository responsibleRepository;

    @Autowired
    private JavaMailSender mailSender;

    public void sendReminderEmails() {
        LocalDate today = LocalDate.now();
        LocalDate targetDate = today.plusDays(7);

        // Fetch documents whose closure date is within the next 7 days
        List<Arm> arms = armRepository.findDocumentsWithClosureDateInRange(today, targetDate);

        for (Arm arm : arms) {
            List<DocumentClosureResponsible> responsibles = responsibleRepository.findByDocumentId(arm.getDocumentId());
            for (DocumentClosureResponsible responsible : responsibles) {
                sendEmail(responsible.getResponsibleEmail(), arm);
            }
        }
    }

    private void sendEmail(String to, Arm arm) {
        try {
            SimpleMailMessage message = new SimpleMailMessage();
            message.setTo(to);
            message.setSubject("Closure Reminder for Document ID: " + arm.getDocumentId());
            message.setText(
                    "Dear User,\n\n" +
                    "This is a reminder that the closure date for document ID " + arm.getDocumentId() +
                    " is approaching. The closure date is " + arm.getClosureDate() + ".\n\n" +
                    "Please ensure all necessary actions are completed before this date.\n\n" +
                    "Thank you."
            );
            message.setFrom("your_email@example.com");

            mailSender.send(message);
            logger.info("Reminder email sent to: {}", to);
        } catch (Exception e) {
            logger.error("Failed to send email to {}: {}", to, e.getMessage());
        }
    }
}

```

#### Code Walkthrough

- **Query Update**: The `findDocumentsWithClosureDateInRange` query now retrieves documents whose closure dates are between today and 7 days from today. This ensures you only send reminders to documents with upcoming closure dates within the next 7 days.
    
- **Service Logic**: The service method `sendReminderEmails` iterates over the list of documents returned by the updated query and sends emails to each responsible individual for those documents.
    
- **Email Content**: The email includes the document ID and closure date, providing a clear reminder to the recipient.
    

#### Complete Working Example

Here's the full implementation with all the pieces put together:

##### Entity Classes

```java
package com.example.emailbatch.entity;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.Table;
import jakarta.persistence.Column;
import java.time.LocalDate;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@Entity
@Table(name = "arm")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Arm {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long armId;

    private Long documentId;

    @Column(name = "closure_date")
    private LocalDate closureDate;

    // other fields
}

@Entity
@Table(name = "document_closure_responsibles")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class DocumentClosureResponsible {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private Long documentId;

    private String responsibleEmail;

    // other fields
}

```
##### Repositories

```java
package com.example.emailbatch.repository;

import com.example.emailbatch.entity.Arm;
import com.example.emailbatch.entity.DocumentClosureResponsible;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;
import java.time.LocalDate;
import java.util.List;

public interface ArmRepository extends JpaRepository<Arm, Long> {
    // Fetch documents with closure date within the next 7 days
    @Query("SELECT a FROM Arm a WHERE a.closureDate BETWEEN :today AND :targetDate")
    List<Arm> findDocumentsWithClosureDateInRange(@Param("today") LocalDate today, @Param("targetDate") LocalDate targetDate);
}

public interface DocumentClosureResponsibleRepository extends JpaRepository<DocumentClosureResponsible, Long> {
    // Fetch responsible individuals for a document
    List<DocumentClosureResponsible> findByDocumentId(Long documentId);
}

```


##### Service

```java
package com.example.emailbatch.service;

import com.example.emailbatch.entity.Arm;
import com.example.emailbatch.entity.DocumentClosureResponsible;
import com.example.emailbatch.repository.ArmRepository;
import com.example.emailbatch.repository.DocumentClosureResponsibleRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.mail.SimpleMailMessage;
import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.util.List;

@Service
public class EmailNotificationService {

    @Autowired
    private ArmRepository armRepository;

    @Autowired
    private DocumentClosureResponsibleRepository responsibleRepository;

    @Autowired
    private JavaMailSender mailSender;

    public void sendReminderEmails() {
        LocalDate today = LocalDate.now();
        LocalDate targetDate = today.plusDays(7);

        // Fetch documents whose closure date is within the next 7 days
        List<Arm> arms = armRepository.findDocumentsWithClosureDateInRange(today, targetDate);

        for (Arm arm : arms) {
            List<DocumentClosureResponsible> responsibles = responsibleRepository.findByDocumentId(arm.getDocumentId());
            for (DocumentClosureResponsible responsible : responsibles) {
                sendEmail(responsible.getResponsibleEmail(), arm);
            }
        }
    }

    private void sendEmail(String to, Arm arm) {
        try {
            SimpleMailMessage message = new SimpleMailMessage();
            message.setTo(to);
            message.setSubject("Closure Reminder for Document ID: " + arm.getDocumentId());
            message.setText(
                    "Dear User,\n\n" +
                    "This is a reminder that the closure date for document ID " + arm.getDocumentId() +
                    " is approaching. The closure date is " + arm.getClosureDate() + ".\n\n" +
                    "Please ensure all necessary actions are completed before this date.\n\n" +
                    "Thank you."
            );
            message.setFrom("your_email@example.com");

            mailSender.send(message);
            logger.info("Reminder email sent to: {}", to);
        } catch (Exception e) {
            logger.error("Failed to send email to {}: {}", to, e.getMessage());
        }
    }
}

```

##### Scheduler Configuration

```java
package com.example.emailbatch.config;

import com.example.emailbatch.service.EmailNotificationService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.annotation.EnableScheduling;
import org.springframework.scheduling.annotation.Scheduled;

@Configuration
@EnableScheduling
public class SchedulerConfig {

    @Autowired
    private EmailNotificationService emailNotificationService;

    // Run the task every day at 8:00 AM
    @Scheduled(cron = "0 0 8 * * ?")
    public void scheduleEmailNotifications() {
        emailNotificationService.sendReminderEmails();
    }
}
```

##### Application Properties

Configure the email sender in your `application.properties` file:

properties

Copy code

```java
spring.mail.host=smtp.example.com
spring.mail.port=587
spring.mail.username=your_email@example.com
spring.mail.password=your_password
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

```

#### Conclusion

With this setup, your application will:

- Fetch documents with closure dates less than or equal to 7 days from today.
- Send daily reminder emails to responsible individuals until the closure date is reached.
- Execute this logic every day at 8:00 AM using Spring's scheduling capabilities.

This solution provides a robust way to ensure timely reminders for document closures, keeping all parties informed and prepared ahead of time.

### EMAIL SENDING PART
In the provided code, variables in the HTML template are dynamically set using the Apache Velocity template engine. Velocity allows you to define placeholders in the template, which are later replaced with actual values at runtime. Here's an explanation of how this works in your specific example:

### 1. **Velocity Context and Placeholders**:

- **Placeholders**: The HTML template contains placeholders (e.g., `${UNITNAME}`, `${DOMAIN}`, `${APPLICATIONNAME}`) that represent values to be filled in at runtime.
- **VelocityContext**: The `VelocityContext` object is a key-value map where the keys are the placeholder names (without the `${}`), and the values are the corresponding dynamic content that will replace the placeholders.

### 2. **Setting Values in the VelocityContext**:

- The `VelocityContext` is populated with key-value pairs using the `put` method. Each key corresponds to a placeholder in the HTML template, and each value is the dynamic data that will be inserted into the template.

#### Example:

- **Placeholder in Template**: `${UNITNAME}`
- **VelocityContext Mapping**: `velocityContext.put("UNITNAME", mailDTO.getIOU());`
    - This means that wherever `${UNITNAME}` appears in the HTML template, it will be replaced by the value returned by `mailDTO.getIOU()`.

### 3. **Specific Variables Explained**:

- **`${STATUS}`**:
    
    - **Context**: Not directly shown being set in the provided code snippet. It's likely set earlier in the process.
    - **Usage**: Used to describe the status of the review request (e.g., "Open" or "Resubmitted").
- **`${UNITNAME}`**:
    
    - **Context**: `velocityContext.put("UNITNAME", mailDTO.getIOU());`
    - **Usage**: Represents the name of the unit associated with the application.
- **`${DOMAIN}`**:
    
    - **Context**: `velocityContext.put("DOMAIN", mailDTO.getDomainName());`
    - **Usage**: Represents the domain name associated with the application.
- **`${APPLICATIONNAME}`**:
    
    - **Context**: `velocityContext.put("APPLICATIONNAME", validapplicationName);`
    - **Usage**: Represents the name of the application, which is validated using ESAPI.
- **`${APPURL}`**:
    
    - **Context**: `velocityContext.put("APPURL", mailDTO.getStringJoiner());`
    - **Usage**: Represents the URL of the application.
- **`${USERID}`**:
    
    - **Context**: Set based on conditions involving `ptApplicationDTO`, `revDetails`, and `recentRevIdDetails`.
    - **Usage**: Represents the ID of the user associated with the application.
- **`${REVIEWERID}`**:
    
    - **Context**: `velocityContext.put("REVIEWERID", recentRevIdDetails.getReviewerId());`
    - **Usage**: Represents the ID of the reviewer.
- **`${REVIEWSTATUS}`**:
    
    - **Context**: `velocityContext.put("REVIEWSTATUS", recentRevIdDetails.getReviewStatus());`
    - **Usage**: Represents the status of the review.
- **`${USERREMARKS}`**:
    
    - **Context**: `velocityContext.put("USERREMARKS", recentRevIdDetails.getUserRemarks());`
    - **Usage**: Represents remarks made by the user.
- **`${REVIEWERREMARKS}`**:
    
    - **Context**: `velocityContext.put("REVIEWERREMARKS", recentRevIdDetails.getReviewerRemarks());`
    - **Usage**: Represents remarks made by the reviewer.
- **`${APPTYPE}`**:
    
    - **Context**: `velocityContext.put("APPTYPE", recentRevIdDetails.getApplicationtype());`
    - **Usage**: Represents the type of the application.
- **`${EXPIRYDT}`**:
    
    - **Context**: `velocityContext.put("EXPIRYDT", chngStrtDateFormat.format(recentRevIdDetails.getReapprovaldate()));`
    - **Usage**: Represents the expiry date of the review.
- **`${SSAREMARKS}`**:
    
    - **Context**: `velocityContext.put("SSAREMARKS", recentRevIdDetails.getSsareviewerremarks());`
    - **Usage**: Represents the remarks from the SSA COE reviewer.

### 4. **Merging the Template**:

- After setting all the values in the `VelocityContext`, the `mergeTemplate` method is called to merge the template with the context. This process replaces the placeholders in the template with the corresponding values from the context.
- The merged output (an HTML string) is stored in the `stringWriter` and then used as the email content (`dto.setNotificationDescriptionEmail(stringWriter.toString());`).

### 5. **Email Sending**:

- The final email content is created with all placeholders replaced by actual data.
- This content is then sent using the `clientNotificationService.addNotification(notificationDTOs);` method, which handles the actual sending of the email.

## Worked on InstaBiz UK finger print scanner, API integration and cross currency transfer screen .

## Fault Tolerance