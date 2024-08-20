## Key Features

- Project Creation and Management: Practice creating and managing projects with ease, honing your project management skills along the way.
- User Invitation System: Learn how to implement user invitation systems for collaborative projects.
- Issue Management: Master the art of tracking and resolving project issues efficiently.
- Comment System: Understand the importance of collaboration and feedback by incorporating comment systems into your projects.
- Subscription Plans: Gain insights into implementing subscription-based models, a valuable skill in the modern tech industry.

  

## Technology Stack

- Spring Boot: Dive deep into backend development with Spring Boot's powerful features.
- MySQL: Learn the ins and outs of database management using MySQL.
- React: Discover the flexibility and interactivity of React for frontend development.
- Tailwind CSS: Experiment with modern UI styling techniques using Tailwind CSS and Shadcn UI Library.
- Redux: Master state management in complex applications with Redux.
- React Router DOM: Navigate seamlessly between different sections of your application with React Router DOM.
- JWT Authentication: Implement secure user authentication mechanisms using JSON Web Tokens.
- Spring Security: Ensure your applications are secure from various threats with Spring Security.
- Spring Starter Mail: Learn how to integrate email notifications into your projects with Spring Starter Mail.
- Razorpay Integration: Gain hands-on experience in integrating payment gateways for subscription-based services.

  
- Only the allowed users should be able to view the projects or comments related to the project they own or a part of, I missed this part

## Additional Features

- Search and Filter: Develop advanced search and filtering functionalities to enhance user experience using Debouncing technique.
- Responsive Design: Practice creating responsive designs that adapt seamlessly to various devices and screen sizes.


## Steps


### Auth

1. Create Security Filter
	1. Appconfig
	2. jwtFilter
2. Create User Model
3. Create `CustomUserDetailService` to get rid of default spring security default password
	1. create Auth Controller

### Project API
1. Create Project Model

- **Debouncing**: Delays the execution of the function until the user stops typing.
- **Throttling**: Limits the execution of the function to once every X milliseconds.

Choose between debouncing and throttling based on your requirements. Use `debounce` for scenarios like search inputs where you want to wait until the user stops typing, and `throttle` for scenarios like infinite scroll, where you want to limit the number of requests.


- Used WebSocket and StompClient for Chat section