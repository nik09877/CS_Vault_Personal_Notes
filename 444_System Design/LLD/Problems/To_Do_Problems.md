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
- [ ] Design Inventory Management System
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

# Prompts
1. For each design pattern Provide me 5 different questions that can be solved using the design pattern
2. For each design pattern Provide me 5 different problem statements that can be solved using that design pattern