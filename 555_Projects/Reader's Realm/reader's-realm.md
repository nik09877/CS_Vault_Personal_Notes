# Problems I Faced
- First time trying to use Typescript in React+Bootstrap and using Spring Boot + MySQL
- I chose SQL for its ACID property and able to handle concurrent updates and to learn how to integrate MySQL with Spring Boot
- I used a lot of `!important` in `css` files because I am using Bootstrap and I don't want my styles to be over written.
-  You can import images and use them like this : 
```Html
<img src={require('./Images/BooksImage.png')}/>
```

- If  in `pom.xml` it is showing 'dependency not found' :  
	- right click on project folder
	- go to Maven
	- rebuild project
- Base path api for endpoints is `/api`
- In `config` package I have added `allowedOrigins`, change it while deploying
- In typescript `BookModel` `author?: string;` means this property is optional and can be `null`
- I had difficulty implementing pagination,search books page in client side because I wanted pagination feature to be a reusable component in my application. 

# Building Homepage
