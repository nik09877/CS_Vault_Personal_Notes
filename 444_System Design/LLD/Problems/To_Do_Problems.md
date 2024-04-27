# AI Generated LLD Problems
## Booking Apps
- [ ] Car Rental System
- [ ] Online Hotel Booking System
- [ ] Car Booking Service like Ola, Uber
- [ ] Food delivery app like Swiggy and Zomato
- [ ] BookMyShow & Concurrency handling
- [ ] IRCTC (Indian Railway Catering and Tourism Corporation)

## Management Apps
- [ ] Pizza Billing System
- [ ] Inventory Management System
- [ ] Library Management System
- [ ] Restaurant Management System

## Social Media Apps
- [ ] Community Discussion Platform
- [ ] LinkedIn
- [ ] Google Docs

## E-commerce Apps
- [ ] Amazon

## Games
- [ ] Snake n Ladder game
- [ ] Tic-Tac-Toe game
- [ ] Chess game
- [ ] Bowling Alley Machine

## Infrastructure
- [ ] Parking Lot
- [ ] Elevator System
- [ ] File System
- [ ] Cache Mechanism
- [ ] Traffic Light System

## Utilities
- [ ] Notify-Me Button Functionality
- [ ] Logging System
- [ ] Vending Machine
- [ ] ATM

## Data Processing
- [ ] Splitwise
- [ ] Splitwise Simplify Algorithm / Optimal Accounting Balancing
- [ ] CricBuzz / CricketInfo
- [ ] True Caller
- [ ] Airline Management System
- [ ] Stock Exchange System
- [ ] Learning Management System
- [ ] Online Voting System
- [ ] Payment System
- [ ] Chat-based system
- [ ] Meeting Scheduler
- [ ] Calendar Application
- [ ] Rate Limiter
- [ ] Online Coding Platform and Judge


# Problem Solving with Design Patterns
## Booking Apps
### Car Rental System
- **Design Patterns**:
  - **Factory Method**: Use it to create different types of vehicles (e.g., cars, SUVs) based on user preferences.
  - **Decorator**: Apply it to add optional features or accessories to rental vehicles dynamically.
- **Approach**:
  - Use Factory Method to create instances of vehicles based on user requests.
  - Apply Decorator to add features like GPS, child seats, or insurance to the selected vehicle.

### Online Hotel Booking System
- **Design Patterns**:
  - **Observer**: Implement it to notify users of room availability and price changes.
  - **State**: Use it to manage the booking process (e.g., booking, payment, confirmation).
- **Approach**:
  - Apply Observer to notify users of available rooms and special offers.
  - Utilize State to model the different states of a booking, from reservation to confirmation.

### Car Booking Service like Ola, Uber
- **Design Patterns**:
  - **Strategy**: Use it to define various transportation strategies (e.g., car, bike, shared) and switch between them.
  - **Observer**: Implement it for tracking the location of drivers and notifying users.
- **Approach**:
  - Apply Strategy to handle different types of transportation services.
  - Use Observer to track driver locations and provide real-time updates to users.

### Food Delivery App like Swiggy and Zomato
- **Design Patterns**:
  - **Observer**: Use it to track the order status and notify users.
  - **Decorator**: Apply it to customize food orders with optional items (e.g., extra cheese, toppings).
- **Approach**:
  - Implement Observer to keep users informed about the status of their food orders.
  - Use Decorator to allow users to customize their food orders with extra options.

### BookMyShow & Concurrency Handling
- **Design Patterns**:
  - **Singleton**: Use it to ensure a single instance of a booking system to prevent overbooking.
  - **Observer**: Implement it to notify users of ticket availability and show updates.
- **Approach**:
  - Apply Singleton to create a single booking system instance.
  - Use Observer to notify users of available seats and showtime changes.

### IRCTC (Indian Railway Catering and Tourism Corporation)
- **Design Patterns**:
  - **State**: Use it to manage the booking process (e.g., checking availability, reservation, payment).
  - **Observer**: Implement it to notify users of train availability and booking updates.
- **Approach**:
  - Apply State to model different stages of the booking process.
  - Use Observer to notify users of train availability and booking status.

## Management Apps

### Pizza Billing System
- **Design Patterns**:
  - **Strategy**: Use it to handle various billing strategies (e.g., discounts, promotions).
  - **Observer**: Implement it to update customers on order status and billing changes.
- **Approach**:
  - Apply Strategy for flexible billing methods.
  - Use Observer to keep customers informed about their orders.

### Inventory Management System
- **Design Patterns**:
  - **Observer**: Use it to notify users of inventory changes and low stock.
  - **Command**: Apply it for managing inventory operations (e.g., add, remove, update).
- **Approach**:
  - Implement Observer to notify users of inventory updates.
  - Use Command to encapsulate inventory operations for flexibility.

### Library Management System
- **Design Patterns**:
  - **Observer**: Implement it for notifying users of book availability and due dates.
  - **State**: Use it to manage the status of books (e.g., available, checked out).
- **Approach**:
  - Apply Observer to notify users of book availability and due dates.
  - Use State to track the status of books in the library.

### Restaurant Management System
- **Design Patterns**:
  - **Observer**: Use it to notify customers of table availability and order status.
  - **Command**: Apply it to handle restaurant orders and kitchen operations.
- **Approach**:
  - Implement Observer to keep customers informed about table availability and orders.
  - Use Command to manage restaurant orders and kitchen tasks.

## Social Media Apps

### Community Discussion Platform
- **Design Patterns**:
  - **Observer**: Use it to notify users of new posts and comments.
  - **Decorator**: Apply it for customizing user profiles and content formatting.
- **Approach**:
  - Implement Observer to update users on community activity.
  - Use Decorator for profile customization and content styling.

### LinkedIn
- **Design Patterns**:
  - **Observer**: Use it for job notifications and connection updates.
  - **State**: Apply it for managing user profiles and job application processes.
- **Approach**:
  - Implement Observer to keep users informed about job opportunities.
  - Use State to represent different user profile states and job application stages.

### Google Docs
- **Design Patterns**:
  - **Observer**: Use it for real-time collaboration and document updates.
  - **Command**: Apply it to manage document editing operations.
- **Approach**:
  - Implement Observer for real-time collaboration.
  - Use Command to handle document editing and revision history.

## E-commerce Apps

### Amazon
- **Design Patterns**:
  - **Observer**: Use it to notify users of product availability and price changes.
  - **Strategy**: Apply it for various payment and shipping options.
- **Approach**:
  - Implement Observer to inform users about product updates.
  - Use Strategy for flexible payment and shipping methods.

## Games

### Snake n Ladder Game
- **Design Patterns**:
  - **State**: Use it to manage the game state (e.g., player turns, board positions).
  - **Observer**: Implement it for notifying players of game events.
- **Approach**:
  - Apply State to control game flow and player actions.
  - Use Observer to keep players updated on game progress.

### Tic-Tac-Toe Game
- **Design Patterns**:
  - **Strategy**: Use it for defining player strategies and game rules.
  - **Observer**: Implement it for tracking moves and game outcomes.
- **Approach**:
  - Apply Strategy to handle different player strategies.
  - Use Observer to monitor moves and determine the game winner.

### Chess Game
- **Design Patterns**:
  - **Strategy**: Use it for defining chess piece behaviors and movements.
  - **Observer**: Implement it for tracking game events and notifying players.
- **Approach**:
  - Apply Strategy to model piece behaviors and moves.
  - Use Observer to handle game events and player interactions.

### Bowling Alley Machine
- **Design Patterns**:
  - **State**: Use it to manage the game state (e.g., player turns, scores).
  - **Observer**: Implement it for real-time score updates and game events.
- **Approach**:
  - Apply State to control game flow and scoring.
  - Use Observer to keep players informed about their scores.

## Infrastructure

### Parking Lot
- **Design Patterns**:
  - **Factory Method**: Use it for creating different types of parking spots.
  - **Observer**: Implement it for tracking parking spot availability.
- **Approach**:
  - Apply Factory Method for creating parking spots.
  - Use Observer to notify users of available parking spots.

### Elevator System
- **Design Patterns**:
  - **State**: Use it to manage elevator states (e.g., moving, stopped).
  - **Observer**: Implement it for tracking elevator positions and notifying passengers.
- **Approach**:
  - Apply State to control elevator behavior and states.
  - Use Observer to update passengers on elevator positions.

### File System
- **Design Patterns**:
  - **Composite**: Use it to represent files and directories in a hierarchical structure.
  - **Observer**: Implement it for real-time file system updates.
- **Approach**:
  - Apply Composite for representing files and directories.
  - Use Observer for real-time file system monitoring.

### Cache Mechanism
- **Design Patterns**:
  - **Singleton**: Use it to ensure a single cache instance.
  - **Decorator**: Apply it for adding caching layers and expiration policies.
- **Approach**:
  - Apply Singleton to create a single cache instance.
  - Use Decorator to add caching layers and control cache expiration.

### Traffic Light System
- **Design Patterns**:
  - **State**: Use it to manage traffic light states (e.g., red, green, yellow).
  - **Observer**: Implement it for notifying drivers of state changes.
- **Approach**:
  - Apply State to control traffic light behavior and transitions.
  - Use Observer to inform drivers of state changes.

## Utilities

### Notify-Me Button Functionality
- **Design Patterns**:
  - **Observer**: Use it to notify users or subscribers when events occur.
  - **Command**: Apply it for encapsulating and handling event-related actions.
- **Approach**:
  - Implement Observer to notify subscribers of events.
  - Use Command to encapsulate event-related actions.

### Logging System
- **Design Patterns**:
  - **Singleton**: Use it to ensure a single logging instance.
  - **Decorator**: Apply it for adding log message formatting and filtering.
- **Approach**:
  - Apply Singleton to create a single logging instance.
  - Use Decorator to format and filter log messages as needed.

### Vending Machine
- **Design Patterns**:
  - **State**: Use it to manage vending machine states (e.g., idle, dispensing).
  - **Observer**: Implement it for notifying users of product availability and transactions.
- **Approach**:
  - Apply State to control vending machine behavior and transitions.
  - Use Observer to inform users about product availability and transactions.

### ATM
- **Design Patterns**:
  - **State**: Use it to model ATM states (e.g., card insertion, withdrawal).
  - **Observer**: Implement it for notifying users of account balances and transaction history.
- **Approach**:
  - Apply State to manage ATM behavior and user interactions.
  - Use Observer to keep users informed about account details and transactions.

## Data Processing

### Splitwise
- **Design Patterns**:
  - **Observer**: Use it to notify users of expense updates and settlements.
  - **Command**: Apply it for managing expense-related operations (e.g., add, settle).
- **Approach**:
  - Implement Observer to inform users of expense changes and settlements.
  - Use Command to encapsulate and execute expense-related actions.

### Splitwise Simplify Algorithm / Optimal Accounting Balancing
- **Design Patterns**:
  - **Strategy**: Use it for defining expense settlement strategies.
  - **Observer**: Implement it for tracking expense changes and notifying users.
- **Approach**:
  - Apply Strategy to define various settlement strategies.
  - Use Observer to monitor changes in expenses and notify users.

### CricBuzz / CricketInfo
- **Design Patterns**:
  - **Observer**: Use it to provide real-time cricket score updates.
  - **Singleton**: Apply it to ensure a single source for score updates.
- **Approach**:
  - Implement Observer to provide real-time score updates to users.
  - Apply Singleton to maintain a single source for cricket scores.

### True Caller
- **Design Patterns**:
  - **Observer**: Use it for identifying and notifying users of incoming calls.
  - **Decorator**: Apply it to enhance caller information with additional data.
- **Approach**:
  - Implement Observer to identify and notify users of incoming calls.
  - Use Decorator to enrich caller information with additional details.

### Airline Management System
- **Design Patterns**:
  - **Observer**: Use it to notify passengers of flight status and delays.
  - **State**: Apply it to manage flight and booking states.
- **Approach**:
  - Implement Observer to keep passengers informed about flight status.
  - Use State to represent different flight and booking states.

### Stock Exchange System
- **Design Patterns**:
  - **Observer**: Use it to provide real-time stock price updates.
  - **Singleton**: Apply it to ensure a single source for stock prices.
- **Approach**:
  - Implement Observer to deliver real-time stock price updates.
  - Apply Singleton to maintain a single source for stock price data.

### Learning Management System 
- **Design Patterns**:
  - **Observer**: Use it for notifying users of course updates and announcements.
  - **Strategy**: Apply it to define different learning strategies and materials.
- **Approach**:
  - Implement Observer to notify users of course updates and announcements.
  - Apply Strategy to offer various learning materials and approaches.

### Online Voting System
- **Design Patterns**:
  - **Observer**: Use it for tracking voter activities and notifying authorities.
  - **State**: Apply it to manage the voting process (e.g., registration, casting votes).
- **Approach**:
  - Implement Observer to monitor voter activities and ensure a fair election.
  - Use State to model the various stages of the voting process.

### Payment System 
- **Design Patterns**:
  - **Strategy**: Use it for handling various payment methods (e.g., credit cards, digital wallets).
  - **Observer**: Implement it to track payment transactions and notify users.
- **Approach**:
  - Apply Strategy to support multiple payment methods with a common interface.
  - Use Observer to monitor payment transactions and inform users of transaction status.

### Chat-based System
- **Design Patterns**:
  - **Observer**: Use it for real-time message delivery and user notifications.
  - **Command**: Apply it to manage user commands and actions.
- **Approach**:
  - Implement Observer to enable real-time chat communication.
  - Use Command to handle user commands and actions within the chat system.

### Meeting Scheduler
- **Design Patterns**:
  - **Observer**: Use it for scheduling notifications and updates.
  - **Factory Method**: Apply it for creating different types of meetings (e.g., one-time, recurring).
- **Approach**:
  - Implement Observer to notify participants about scheduled meetings.
  - Use Factory Method to create various types of meetings with appropriate scheduling options.

### Calendar Application
- **Design Patterns**:
  - **Observer**: Use it for event notifications and reminders.
  - **Decorator**: Apply it for customizing event details and formatting.
- **Approach**:
  - Implement Observer to provide event notifications and reminders.
  - Use Decorator to allow users to customize event details and appearance.

### Rate Limiter
- **Design Patterns**:
  - **Decorator**: Use it for adding rate-limiting functionality to different operations.
  - **Singleton**: Apply it to ensure a single rate limiter instance.
- **Approach**:
  - Implement Decorator to add rate-limiting logic to various operations or APIs.
  - Apply Singleton to maintain a single rate limiter instance for consistent rate control.

### Online Coding Platform and Judge
- **Design Patterns**:
  - **Strategy**: Use it to define various programming language support and evaluation strategies.
  - **Observer**: Implement it for notifying users of code execution results and feedback.
- **Approach**:
  - Apply Strategy to support multiple programming languages and evaluation methods.
  - Use Observer to provide real-time feedback to users regarding their code submissions.





# Concept and Coding
- [ ] Design Notify-Me Button Functionality
- [x] Null Object Pattern
- [ ] Design Pizza Billing System
- [ ] Design Parking Lot
- [ ] Design Snake n Ladder game
- [ ] Design Elevator System
- [ ] Design Car Rental System
- [ ] Design Logging System
- [ ] Design Tic-Tac-Toe game
- [ ] Design BookMyShow & Concurrency handling
- [ ] Design Vending Machine
- [ ] Design ATM
- [ ] Design Chess game
- [ ] Design File System
- [ ] Design Splitwise
- [ ] Splitwise Simplify Algorithm / Optimal Accounting Balancing
- [ ] Design CricBuzz / CricketInfo
- [ ] Design True Caller
- [ ] Design Car Booking Service like Ola, Uber
- [ ] Design Online Hotel Booking System
- [ ] Design Library Management System
- [ ] Design Traffic Light System
- [ ] Design Meeting Scheduler
- [ ] Design Online Voting System
- [x] Design Inventory Management System / Order Management System like Zepto 
- [ ] Design Cache Mechanism
- [ ] Design LinkedIn
- [ ] Design Amazon
- [ ] Design Airline Management System
- [ ] Design Stock Exchange System
- [ ] Design Learning Management System
- [ ] Design a Calendar Application
- [ ] Design (LLD) Payment System
- [ ] Design (LLD) Chat based system
- [ ] Design Food delivery app like Swiggy and Zomato
- [ ] Design Community Discussion Platform
- [ ] Design Restaurant Management System
- [ ] Design Bowling Alley Machine
- [ ] Design (LLD) Rate Limiter
- [ ] Design Apply Coupon on Shopping Cart 
# Prompts
1. For each design pattern Provide me 5 different questions that can be solved using the design pattern
2. For each design pattern Provide me 5 different problem statements that can be solved using that design pattern
# LLD Primer
- Design subscription-based sports website which can display scores, game status, history for any games.
    
- Design for online card game say like poker or any other game.
    
- Design Truecaller.
    
- Design a geographically partitioned multi-player card game, that supports multiple players, multiple games at a time. Each game will have one contractor like ones we have in a bar, He can play a game or just watch it. Integrate payment systems.
    
- design a system to fast lookup cars on the market according to the user's geo-position.
    
- Design an airport service that will be used to allocate a free runway when the plane is about to land. Data structure for the same. What if the runway is not available? Message passing between control center and the plane. Focus on low-level design and code. Can the same runway be allocated to two different planes (locking)? Database storage needed?
    
- Design a Ride Sharing Application where drivers can offer rides (origin, destination, no of seats), riders can request rides ( origin, destination, no of seats) and there is an algo to decide which driver should be given the trip in case of a collision ( maximum overlapping one).
    
- Design a task planner. Different types of tasks are present – bug, feature and story. And their attributes are given. Also a Sprint which is a collection of tasks.
    
- Implement a finite state machine. – The machine should have one start state and can have multiple end states.
    
    - It should be extensible (I should be able to add any number of states or transitions at any time)
    - I should be able to set notifications on or off for any state or for the whole state machine
- Design a system like Jira. It should have the following functionalities :
    
    - User should be able to create Task of type Story, Feature, Bugs. Each can have their own status.
    - Stories can further have subtracts.
    - Should be able to change the status of any task.
    - User should be able to create any sprint. Should be able to add any task to sprint and remove from it.
        - User should be able to print
        - Delayed task
        - Sprint details
        - Tasks assigned to the user
- Design a stock exchange system. There is a list of stocks given with following attributes
    
    - order_id
    - time
    - stock name
    - type(BUY/SELL)
    - quantity
    - price
    
    You need to output list of stocks in the following format sell_id, buy_id, quantity, price which will get executed.
    
- code a TextPad with following functionality:
    
    - display() – to display the entire content
    - display(n, m) – to display from line n to m
    - insert(n, text) – to insert text at line n
    - delete(n) – delete line n
    - delete(n, m) – delete from line n to m
    - copy(n, m) – copy contents from line n to m to clipboard
    - paste(n) – paste contents from clipboard to line n
    - undo() – undo last command
    - redo() – redo last command
    
    expected the textpad to be in memory(not as file) and also expected to handle error gracefully and the program to be menu driven.
    
- Design Car Rental System like Zoomcar.
    
- Design a billing and auctioning system similar to EBay. Ebay is a multinational e-commerce corporation, facilitating online consumer-to-consumer and business-to-consumer sales. The website is free to use for buyers, but sellers are charged fees for listing items and again when those items are sold. The sellers aution their items and buyers bid on items.
    
- Design Q&A application as in Amazon,Walmart has it for each product.
    
- Design push notification :
    
    - Which sends the notification to the registered users
    - Which receives an event from promotions team
    - Sends notification to iOS, android or sends an email or all three
- Design a suggestion system
    
- Design and Implement a Simple Java GC (Java 7+)
    
    - A heap which represents JVM when a Java program starts.
    - At least three parts in the heap that represent Eden Space, Tenured Space and Perm Space.
    - Different rounds of garbage collecting in these above three spaces (checking all objects to see if they have any live references at all, if not, kill them, reclaim the allocated memory, otherwise, move them to later spaces..)
- Design LinkedIn.
    
- Design a video upload system for a user with low network bandwidth
    
    User has to upload video which is more than 1GB. Users network bandwidth is too low. Network get dropped after 50% upload. User tries again and same thing happens. Now to design an optimized efficient solution to address this issue.
    
- Design Learning Management System
    
- Design Survey similar to Google Forms / SurveyMonkey.
    
- Design Logging Framework
    
- Design a locker
    
    To monitor the process of how to put the package into a right locker. and one locker for one package. your package and locker have different size, you need to make sure the locker size > package.
    
- Design a calendar Application (similar like Google Calendar) -Ability to create, update, delete an Event
    
    - An event would typically consist of {start, end, location, Owner, user-list, title}.
    - Events can either be like meetings(with a dedicated location and appropriate guest-list) or as well be like holidays, birthdays, reminders etc.
    - An event once created, can be either accepted or rejected by the constituent users - if neither it should be in neutral state.
    - Get Calendar for a user Ui
    - Get Event details.
    - For a given set of users[U1, U2,....Un] identity a common free slot of time.
- Design Guitar Inventory System
    
- Desing Payment System
    
- Design a stock trading system
    
- Design Payment Gateway like Razorpay.
    
- Design a Json Parser from scratch
    
    - It is coming from untrusted source (meaning validation of json is required)
    - the key will always be string the value can be string or another key value pair.
    - Sample input {'abc':{'d':'ef','r':'er'}} -- map.get("abc").get("d") should return "ef".
    - No other type i.e. integer or boolean or array in the json
    - Validation and parsing must in done simultaneously
    - In case of invalid json string throw exception
- Design Chat Based application like whatsapp/wechat.
    
- Design a home automation sytem to remotely control all the switches, devices in a home.
    
- Design Maps Navigator Client for different transportation types
    
    - Design a maps path-building navigator client.
    - User should be able to build path from point A to point B using your code.
    - design should support different transportation methods for example: walk, car, bus, bike.
- Design Meeting Scheduler
    
    - Here there are n given meeting rooms. Book a meeting in any meeting room at given interval(starting time, end time). Also send notifications to all person who are invited for meeting.
    - You should use calender for tracking date and time. And also history of all the meetings which are booked and meeting room. write an API for client who will give date and time and API should return meeting room with booked scheduled time. client should also query for history of last 20 booked meetings.
    - Is meeting room available? etc
- Design and Implement a logger library that applications can use to log messages.
    
- Design a configuration management system
    
    - User should be able to add configuration
    - User should be able to delete configuration
    - User should be able to search for configuration
    - User should be able to subscribe to Configuration So that any updates in configuration will gets notfied to user
- Design Amazon comments filtering system
    
- Design a Vending Machine
    
    - Add items to the vending machine in fixed number of slots
    - Payment using card or cash
    - Select item to dispense
- Design Splitwise.
    
- Design Mock Interview System like pramp.
    
- Design Application Tracking System (ATS) like greenhouse
    
- Design a Logistics System
    
- Design CSV parser
    
- Design message queueing system
    
    - Create your own queue that will hold messages in form of JSON. Standard library queues were not allowed.
    - There was one publisher that can generate messages.
    - There are mutiple suscribers that will listen messages satisfying a particular regex.
    - Suscribers should not be tighly coupled to system and can be added or removed at runtime.
    - When a suscriber is added to the system, it registers callback function along with it. And this callback function will be invoked in case some message arrives.
    - There can be dependency relationship among suscribers i.e if there are two suscribers say A and B and A knows that B has to listen and process first, then only A can listen and process. There was many to many dependency relationship among suscribers.
    - There must a retry mechanism for handling error cases when some exception occurs in listening/ processing messages, that must be retried.
- Design Employee Management Platform which includes payroll,IT,employee benefits and all other employee operations in one place.
    
- Design User Engagment platform.
    
- Design product experience platform like pendo.
    
- Design Chess Game.
    
- Design Live Auction platform for IPL / EPL.
    
- Design Unit Testing Application
    
- Design Browser testing Application like browserstack / sauce labs.
    
- Design Real time collaboration application for the teams.
    
- Design Visual workplace for remote teams.
    
- Design Online UML Diagram Tool like lucidchart.
    
- Design Parking Lot.
    
- Design online audio/video file downloader.
    
- Design Inventory System.
    
- Design Warehouse Management System.
    
- Design Game Streaming platform.
    
- Design Real-Time Translation platform.
    
- Design Community based discussion platform.
    
- Design application for restaurant / malls to efficiently handle waiting queue and optimizely assign the table.
    
- Design online assesment platform for exam's like gre / tofel.
    
- Design online customer verifaction platform for digital on-boarding(KYC) of the users for bank and others client's.
    
- Design Secure Content Management platform.
    
- Design Freelancing hiring platform.
    
- Design monitoring and alert system for the production as well and other enviroments.
    
- Design digital-video KYC (know your customer) verification system.
    
- Design online e-fiiling online income tax returns service.
    
- Design job posting system dedicated to blue and grey collar workers. (multiple langs / native lang)
    
- Design System Simiar to the Product-hunt (share and discover new products)
    
- Design service like Clipboard. (try to store the maximum clips)
    
- Design system for salary info,comparsion and other info similar to the glassdoor salary / salarry.level.
    
- Design pricing / product comparision system.
    
- Design Virtual Event Platform for Communities / Enterprise.
    
- Design system for short video/content sharing like Tiktok.
    
- Design Short Story Telling (Text/Images) platform like Terribly Tiny Tales.
    
- Design a user activity tracking system for user on mobile.
    
- Design in-memory (Questions like write to add,remove the table,etc).
    
- Design a login API which is secure even if SSL certification is compromised.
    
- How to design an API whose response will have the response from 3 other different microservices.
    
- Design system which exposes two APIs:
    
    1. Save Numbers : which takes N integers and saves in backend
    2. GetMedian: Returns median of the numbers stored so far. [Most Frequent Op]
- Design a torrent service, end to end.
    
- Design system like Bigbasket (local retailer's).
    
- Design a limit order book for trading system.
    
- Design a Cache Mechanism.
    
- Design a personal stock / investment protfolio system.
    
- Design a electronic signature system like DocuSign / EasySign.
    
- Design a generic coupon/promocode system.
    
    - Coupon can give minimum Z% off upto X amount (with or without min cart size)
    - Coupon can give flat discount of X (with or without min cart size)
    - Coupon can be applicable for one/few/all customers
    - Coupon can be applicable on one/few/all merchants
    - Coupon can be used only one time/few time/everytime.
- Design of a quizzing app.
    
- Design a system (initially one node/server) that could handle requests on the scale of millions. It should return a unique id for each request (The id should be unique in sense that there would be only one such id ever generated).
    
- Order-Management-System-or-System-Design.
    
- Implementation of Kafka.
    
- Design and Implement Rocksdb.
    
- Design and Develop the Zookeeper using Rocksdb and Google's BigTable.
    
- Developing a message queueing system.
    
    - Create your own queue that will hold messages in the form of JSON(Standard library with queue implementation were not allowed).
    - There can be more than one queue at any given point of time.
    - There will be one publisher that can generate messages to a queue.
    - There are multiple subscribers that will listen to queues for messages.
    - Subscribers should not be tightly coupled to the system and can be added or removed at runtime.
    - When a subscriber is added to the system, It registers a callback function which makes an API call to the given end point with the json payload, this callback function will be invoked in case some message arrives.
    - Subscriber can consume the messages in batches if the queue has more than one message and it should be configurable.
    - There must be a retry mechanism for handling error cases when some exception occurs in listening/processing a message, that must be retried.
- Design a service to view/add/remove viewers of a document (like the feature in google doc).
    
- Design an Online Auction.
    
    - An auction is initiated by a seller and consists of a single product. It starts from 0$ and buyers can keep bidding(always at least current_winner + a predefined increment) until it expires.
    - The seller can define a reserve price. Its presence is visible, but the actual amount is not. If defined and the final bid is less than the reserve price, the auction will fail with a separate status.
    - Bidders might also make use of an autobidding system. Given a maximum value, each time the user is outbid, the system will automatically try to bid on behalf of the user with the smallest value possible(the predefined increment above will be used to reach this value; calculation must strictly follow it), up until the maximum value has been reached.
    - The autobidding algorithm must be efficient time complexity wise.
    - Once an auction completes, an external system will be notified of the result together with the winner(if any).
- Design for storing chemicals with their constituents in an efficiently retrievable format.
    
- Design and Architecture - Appointment booking for a hospital where each doctor can open slots independently of any time period.
    
- Design Online Exam Portal.
    
    - On exam completion total score and subject wise score calculation (make sure u consider negative marking).
    - On exam completion Rank calculation.
    - Provision for MOCK tests (users should get hypothetical ranks by comparing previous year results)
    - A pre-exam (with limited users ~10k) to mimic actual exam and then give generalised ranks for more users(in millions).
- Build the Google Stock Wizard.
    
- Design the Food Ordering System like Swiggy/Zomato.
    
- Design the Bill Summary Feature.
    
- Design Learning app (Design system where teachers can upload the content and stuedents can view that content.)
    
    - Teachers should be notified once their content is uploaded.
    - Upload should continue even if browser is closed in case it is a browser upload.
- Design Navigation Alerts System. (Similar like Google Map Functionality.)
    
- Design a system which improves the quality of the data.
    
    - A system which takes a large amount of data, cleans it, adds specified properties to it and sends the results so that the other services can filter the data with the newly added properties.
- Design a Plagiarism checker.
    
- Design a distributed Cache.
    
- Design a business rule based engine.
    
- Design Authentication/Authorization Service which supports(otp,OAuth, etc.).
    
- Design a SMS validator system.
    
- Design(HLD) Zipkin - A request tracing system for distributed applications. Example - A request is flowing through multiple microservices, system should be able to trace the time spent by the request and sequence followed by it.
    
- Design Ads system for a website.
    
- Design an online code judge.
    
- Design Splunk like log manager system supporting queries with filters on last min, hr, day, week etc.
    
- Design Linkedin Suggest connections feature.
    
- Implement a wide column store like Cassandra (bonus : support secondary indexes).
    
- Create an online music recommendation system which suggests songs according to user taste.
    
    - Application has two major things : - The songs, which are cataloged in the app’s data store. Songs can be described by attributes such as genre, tempo, singer. - The people : Each person has a playlist of songs that they can choose to play from.
        
        ```
         - Design a system that recommends a set of songs from our music library to the user based on his preferences (matching genre / singer/ tempo)             taking into account his current playlist.
         - Pick a song based on the following order:
         - One which matches with maximum matching attributes.
         - When only one attribute is matching, pick one in the following order : genre > singer > tempo.
         - To decide priority between two genres\singer\tempo, consider the number of songs in each category in the user's playlist to decide which               song gets more priority. One with a higher number of songs gets high priority. If the number of songs are the same, show in any order. 
         - 
        ```
        
- Design a test taking website type service where user can register/login,
    
    - give the test and can see their past test score and rankings.
    - Test can be of multiple types and questions in test can be of multiple type (mcq, yes/no, fill in the blanks, multiple correct options) with the questions can being both image and direct string.
    - Questions should be unique to every user in a particular test and in case of user being dropped from the test (bad internet or anything) he can resume the test from where he left provided he came before his test timer was off.
- Design a service for showing HeatMap of Swiggy / Zomato agents at a time.
    
- Design Webhook Dispatcher.
    
- Implement service to Find the recently viewed listings on the website by the user. Example a user looked for hotels in Bangalore. Design a system responsible to return the recent listings for a user.
    
- Design a Jackpot Machine.
    
- Designing a ID card system which employees use to access any zone/premises.
    
- Design a Bar Graph Library.
    
- Notification Service design.
    
    - Design a notification service for swiggy which takes in a list of users and message and notifies them . Users could be of different types like delivery men , swiggy employees, end user of App.
- Gym Managment System.
    
    - Design a backend system for a new enterprise application that Flipkart is launching, FlipFit. Flipkart is partnering up with gyms across Bangalore to enter into the fitness space. For the Beta launch the requirements are as follows:
        - There are only 2 centers for now - Koramangala and Bellandur. We might expand to multiple others if we get traction. Each center has 6 slots. 3 in the morning of an hour each from 6am to 9am and similarly 3 in the evening from 6pm to 9pm. The centers are open. 7 days a week.
            
        - Each slot at a center can have only 2 possible workout variations for now - Weights and Cardio.
            
        - The number of people that can attend each workout at each slot for a given station is fixed. Assume default slot capacity as 3(for every workout type across centers).
            
        - Same User cannot book at the same center at the same slot and the same workout type twice.
            
        - User can perform the following operations:
            
        - Register onto the platform
            
        - View the workouts for a particular day
            
        - Book a workout for a user if seats are available in that time slot at that center
            
        - View his/her plan based on day as input
            
        - For simplicity’s sake you can assume that the workout info will be entered by the Admin only once.
            
        - Bonus : Build an Admin view as well to modify the workout info at a center/slot level.
            
- Design an concurrent History tracking system where we can store and track history of registered entities. We should be able to onboard service and their entities to our system and start tracking changes being made to them.
    
- Design a scheduler, that takes in 10 scheduling requests at a time and can execute 100 jobs at a time.(The scheduler executes http requests.)
    
- Design a system which keeps track of leaders for some contest. Like referrals leader.
    
- Design a key value store and an Index.
    
- Design an analytics to display machines which have valid certificates,Design the system with valid dashboard with all the machines with good/bad certificates.
    
- Design a service that calls any passed endpoint at a fixed interval.
    
- Design System where User can create alerts on StockOptions.
    
    - Raise an Alert When "APPL" stock transaction happens for more than $100.
        
    - Raise an Alert When "GOOGL" stock transaction happens for less than $40.
        
    - ou have one black-box Api say market-api
        
    - you can call for particular stockoption and data will keep on flowing for that stockoption in form of say json , and will keep on flowing ; like below json
        
        ```
           	{
           		string company;// Apple
           		double price; // 134.22
           		int nb_shares;//100
           		long timestamp;//24542212
           	},...
        ```
        
- Design a UUID generator.
    
    - Design a system that is incrementally scallable upto 1000 unique ID requests per second each by 1000 devices per person, for every human on the earth for 100 years.
        
    - Consider:
        
        ```
          10^10 - number of people on the planet
          10^10 - number of second in 100 years
          10^7 - max requests per second per server serviceable.
        ```
        
- Design a scalable weather service that pulls data from an API.
    
- You are required to implement an in-memory cache module/library which you will embed in your application to improve the application performance, by holding heavily accessed (read/written) application specific objects. To start, we would begin with following minimal requirements.
    
    - Your cache module should be generic, re-usable and easy to integrate across various modules within your production/organization.
        
    - The cache will be bounded by a fixed capacity (number of items) for holding the objects, which will be mentioned during early initialization of the p program.
        
    - Upon hitting the capacity, the cache module can invoke one of various cache eviction strategies to make room for newer objects. You are required to incorporate cache eviction in your code to handle aforementioned condition.
        
    - You could choose to implement various cache eviction strategies such as 'Least recently used', 'Least frequently used', 'time based expiration'et.al
        
    - In one of our unique use cases, we would like to change the eviction policy of the cache during runtime and the cache should start evicting keys based on the new eviction policy set.
        
- Design library management system.
    
    - Any library member should be able to search books by their title, author, subject category as well by the publication date.
        
    - Each book will have a unique identification number and other details including a rack number which will help to physically locate the book.
        
    - There could be more than one copy of a book, and library members should be able to check-out and reserve any copy. We will call each copy of a book, a book item.
        
- The system should be able to retrieve information like who took a particular book or what are the books checked-out by a specific library member.
    
- There should be a maximum limit (5) on how many books a member can check-out.
    
- There should be a maximum limit (10) on how many days a member can keep a book.
    
- The system should be able to collect fines for books returned after the due date.
    
- Members should be able to reserve books that are not currently available.
    
- The system should be able to send notifications whenever the reserved books become available, as well as when the book is not returned within the due date.
    
- Each book and member card will have a unique barcode. The system will be able to read barcodes from books and members’ library cards.
    
- Design an API rate limiter.
