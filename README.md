# ListEverywhere

## Introduction
ListEverywhere is a digital shopping list and recipe sharing application that allows for users to access their lists from anywhere with an internet connection. Users can easily create, modify, and delete shopping lists within the application, replacing the dated paper list or note-taking application. After registering for a free account, users can begin creating their shopping lists that are readily available at the store or at home. While shopping in the store, users can quickly check off items as they go through the aisles.  
  
ListEverywhere provides a unique feature to enhance the shopping experience of users: recipe integration within lists. Users can find recipes that include ingredients from their list and integrate it into their list. Users will always know what to purchase as ingredients from their list and the recipe automatically merge. This simplifies the process of creating a meal plan, as this application can prepare the list at home or at the store. If users are unable to find a specific recipe, they can create their own recipes inside of the application. Additionally, they can publish this recipe so that other users can incorporate it into their own shopping lists.

**The Problem and Solution**
Current methods for writing shopping lists include paper shopping lists or notes application on a mobile device. One major issue with these methods is that users can forget the lists at home or lose them, either through losing the paper or the device. ListEverywhere solves this issue by storing the user's shopping lists online rather than tying the list to a single location. As long as the user knows their username and password and has an internet connection, their lists are always available at home or in the store. 

ListEverywhere also solves another potential issue that shoppers may encounter: figuring out meal plans. ListEverywhere provides a unique recipe match feature that allows users to find recipes containing items that are already in their shopping list. When the user finds an interesting recipe, the application can automatically merge the recipe items with the user's shopping list, simplifying meal plans.

## Requirements
Below is a list of the functional and non-functional requirements that were specified for ListEverywhere.

**Functional Requirements**
 - User registration
 - User login
 - Create list
 - Edit list
 - Delete list
 - Move list items
 - Checkmark boxes for items
 - Desktop interface
 - Mobile interface
 - Explore recipes (categories, search, match)
 - Search recipes
 - Match recipe to list
 - Create recipe
 - Publish recipe
 - Delete recipe

**Non-Functional Requirements**
 - Deploy the backend application to the Cloud
 - Successfully load the application url
 - Ensure that the budget does not exceed $50 per month
 - Ensure that the computing resources does not exceed 750 hours per month
 - Ensure that the storage does not exceed 20 GB

## Technologies
The following list contains all of the technologies that were used during and for the development of ListEverywhere.

 - **Java 17**
	 - The backend is written using the Java language as the Spring Boot framework is written for Java.
 - **Spring Boot 2.7.4**
	 - Spring Boot automatically handles all the code for standing up a Spring application, making it simple to create and develop a Java application.
 - **Apache Tomcat 8.5.79**
	 - Tomcat provides a server for the Java application to run on.
 - **MySQL 8.0.23**
	 - MySQL provides a database solution for storing any user, shopping list, and recipe data.
 - **Dart 2.19.1**
	 - Dart is the language required for writing applications using the Flutter framework.
 - **Flutter 3.7.1**
	 - The Flutter framework will be used to create a cross-platform mobile and desktop application. Version may be subject to change as the project continues.
 - **Amazon Web Services (AWS)**
	 - AWS will be used to host the application backend so that the application can be accessed outside of a local environment.
 - **FatSecret Platform API**
	 - This API provides an extensive list of product names and various information about them. This will mainly be used for getting shopping list and recipe item names in the application.
 - **Visual Studio Code**
	 - Used for the development of the Flutter fronted application as official extensions for Flutter and Dart were created.
 - **MySQL Workbench**
	 - Used for creating, modifying, and accessing the MySQL database.
 - **Spring Tool Suite 4**
	 - Used for developing the backend Spring Boot application as the IDE is built specifically for Spring Boot development.
 - **Xcode**
	 - Used to sign and build the iOS and MacOS versions of the frontend Flutter application.

## Industry Best Practices
- N-Layer architecture followed for the Spring Boot backend application (See UML diagram in Technical Approach).
- All classes and methods are commented according to the language specifications.
- REST API is secured using JWT tokens
- Flutter application is organized into separate folders and widgets
- MySQL database contains no repeated data - tables with connecting data are linked with foreign keys

## Cloud Deployment
Amazon Web Services (AWS) was used for hosting the backend Spring Boot application on the Cloud. The EC2 instance contains a Tomcat server running the application and a RDS t2.micro service running a MySQL database. The application is running on a single instance with a single vCPU. The specifications were kept to the minimum supporter on AWS so that the application would remain free-tier eligible.

[Application URL](http://listeverywhereapi-env.eba-nsfgxj2p.us-east-1.elasticbeanstalk.com)

## DevOps Principles
The backend application contains a tracer log that outputs trace logs to the console each time a method is executed. The tracer utilizes the Spring Starter AOP dependency. When a method is executed, such as accessing the user's shopping lists endpoint, each method is intercepted by the tracer. The application then logs the start time, execution time, and end time for each method that is executed. The administrator can view the application logs on the local terminal or in AWS to inspect method execution.

