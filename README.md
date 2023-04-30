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

## New Technologies
Several new technologies were learned during the development of this project. This section will describe these technologies and why they were chosen.

**Flutter + Dart**
The Flutter framework is a cross-platform development kit written for the Dart language. It is a fairly new framework developed by Google. This framework was chosen for ListEverywhere as it would provide a frontend application that supports mobile, desktop, and web without having to rewrite the application for multiple platforms. The framework also contains a large library of pre-made widgets, including widgets that follow the Material design which was utilized in the project. This technology was chosen over alternatives, such as React Native, as the Dart language has closer resemblance to Java and C# over JavaScript and Flutter supports the web platform.

At the start of the project, the "Complete Flutter Development Bootcamp with Dart" course was purchased so that the language could be learned prior to developing the ListEverywhere application. This provided the foundations that were needed to successfully build the final release of the application.

**FatSecret Platform API**
This third party API was used for getting the item names for shopping list items and recipe items. This API was chosen as it provides a large list of food products, removing the need to create a local database table of product names. Additionally, the API has a search method for items that can find exact matches or alternatives to the search query. Another reason for using this API is for the recipe match, as the recipe match can use item IDs instead of having to compare text which can introduce complex logic.

**Spring Security OAuth2 Client**
This package provided an implementation for consuming an OAuth 2 protected service in a Spring Boot application. This was required for interfacing with the FatSecret Platform API to get the item names.

## Technical Approach
Several design diagrams were drafted prior to the development of ListEverywhere. These diagrams outline the approaches taken to building, configuring, and implementing the application and various features. Several of these diagrams can be viewed directly by navigating to the [ListEverywhereDesign Repository](https://github.com/ListEverywhere/ListEverywhereDesign) that is located in the GitHub organization.

**UML Diagram**

The following diagram outlines the UML Classes for the Spring Boot backend application. All the Controllers, Models, and Services required for the backend are detailed in the diagram. A key is provided to detail which layer each class is built for. This document provided the structure of how the backend application was designed and showcases the N-layer architecture.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/UML%20Diagram.png)

**Database ER Diagram**

The following diagram outlines the table structure required to store the data for ListEverywhere in the MySQL database. Fields with a key icon represent the primary key for each table. Fields with a red icon represent a foreign key relationship with another table. The ER diagram was built using the Reverse Engineer tool in MySQL Workbench.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/Database%20ER%20Diagram.png)

**Logical Solution Diagram**

The following diagrams outline the software architecture that will be used by ListEverywhere. This section consists of two diagrams: Software Overview and Widget Design.

**Software Overview**
This diagram breaks down the architecture for the backend and frontend applications for ListEverywhere. The backend contains the Spring Boot application, which follows an N-layer architecture design, as well as a MySQL database connected locally. A detailed breakdown of the Spring Boot application classes is provided in this document under the  UML Diagrams  section. The backend has one integration for the third-party API platform. The frontend contains the Flutter application, in which it follows a similar structure to the N-layer architecture design. The second diagram displays a visual mockup for the Widgets section.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/Logical%20Diagram%20Software%20Overview.png)

**Widget Design**
This diagram utilizes the application wireframes to represent a visual mockup of the custom UI Widgets that will be designed for ListEverywhere’s Flutter application. All the sections highlighted in color represent a custom widget. UI elements that are not highlighted represent widgets that are provided by Flutter and the Material library.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/Logical%20Diagram%20Widget%20Design.png)

**Physical Solution Diagram**

The following diagram outlines the physical and cloud infrastructure that will be used to run ListEverywhere. The backend of the application will be hosted on AWS, in which each service and its specification are written for each AWS service. Additionally, the application MySQL database will be hosted on AWS and will connect locally to the backend in AWS. The backend will integrate with one third-party service that is not managed by ListEverywhere. This includes the FatSecret Platform (getting item information). The client tier will interact with the backend over HTTP and JWT token authentication. The mobile and web clients will both integrate with the backend hosted in AWS. The mobile client will run as a native application while the web client will require a local web server to operate.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/Physical%20Solution%20Diagram.png)

**Service API Design**

The ListEverywhere API was designed prior to building the backend application. This was completed using Stoplight, in which the design can be accessed by clicking the link below:

[ListEverywhere API Design](https://gcep-451.stoplight.io/docs/listeverywhere/phakw9myo5b19-list-everywhere-api)

**Sitemap**

The following diagram represents the user flow on the frontend application. This details the paths that the user can take when navigating the frontend of the application. The user will be able to navigate to pages through a navigation bar and exit pages using a back button.
![enter image description here](https://raw.githubusercontent.com/ListEverywhere/ListEverywhereDesign/main/Sitemap.png)

## Risks and Challenges
Several risks and challenges were idenfitied prior to and during development of ListEverywhere. These risks were determined by analyzing the technologies included in the design and factoring in the potential issues that could arise.

**1. Developing a Flutter Application**

**The risk** - Having to learn the Flutter framework and successfully create simple applications using it

**Why?** -  This technology was researched at the beginning of the project. There were no prior experiences with using and building applications in Flutter. This would make it uncertain if a Flutter application could be successfully developed by the end of the project.

**Mitigation Plan**

1. Research the Flutter framework and figure out if it is applicable.
2. Setup the Flutter environments and ensure all the necessary tools are working
3. Create a simple application and get it to run on a mobile device
4. Create a simple backend for the Flutter app to interact with
5. Research how to connect the backend to the Flutter application
6. If successful, decide to use the framework or not by October 30, 2022.

**Resolution** - A Flutter course was purchased that provided several lessons about writing Dart and Flutter code. This provided enough of an understanding of the framework to where the ListEverywhere application could be successfully completed. The course can be found here: [The Complete 2021 Flutter Development Bootcamp with Dart](https://www.appbrewery.co/p/flutter-development-bootcamp-with-dart)

**2. Cloud Hosting**

**The risk** - The resources and cost of using a cloud platform will need to be considered for future stages of the application

**Why?** - The backend will need to be hosted to access the API from a mobile or desktop device. This is resolved by cloud hosting, however the resource usage and cost will need to be monitored. While there is a small budget allocated for the project, it is preferred that cloud costs are kept to a minimum.

**Mitigation Plan**

1. Research which cloud providers will host the application and the technologies it uses. (The cloud hosting platform at this time will be AWS)
2. Run a simple application on the cloud and test out the available resources
3. Test out hosting the application during the first code milestone
4. Have several people test out the application and monitor cloud resources

**Resolution** - A simple testing API application was created and deployed to AWS, choosing the minimal resources required for the application. Once this was verified to be working, the API would be later deployed to the cloud once significant progress was made on it. Additionally, an alert was created that will send an email notification if the monthly costs are over a set amount.

**3. Third-Party API**

**The risk** - The FatSecret API contains a limit of 5000 API calls per day for free plans. This may be an issue if the application continuously calls for product information from the API.

**Why?** - The application must make several API calls to get item information for shopping lists and recipes, as only item ID numbers are stored in the application. During testing and development, the limit was not an issue as it was mainly a single session. However, if multiple users were to use the application at the same time, the application may run out of API calls and temporarily lose access to item names.

**Mitigation Plan**

1. Research the API and the terms and conditions.
2. Identify what the API offers and what data is given.
3. Test out the API by implementing it in an application, either a simple project or an early version of the main project, and measure how many API calls will be required.
4. If the free plan is not sufficient, consider what paid plans are offered by the service.
5. If a solution cannot be resolved, consider a new API or creating a local database of products.

**Resolution** - The API calls limit was not an issue during testing of the application, and some views were modified to reduce unnecessary API calls. This can be seen in some of the controller methods in the backend application where a noItems parameter is available. Towards the end of the project, FatSecret Platform was contacted and granted access to the Premier Free tier as the project was eligible for it. This provides more access to the API without call limits.

## Issues
While the final release candidate for ListEverywhere is feature complete per the requirement specifications, there are several documented issues that must be addressed in the future. If additional bugs are found by users, an issue can be created on the appropriate repository in the ListEverywhere GitHub organization.

**Bugs/Known Issues**

 - When updating a user in the API, the constraints are not checked
 - When opening a list, the list name does not show until the user performs an update
 - Match Recipes with List Items endpoint displays an incorrect error message if the recipe does not exist
 - No animation when item is moved to bottom of the list after being checked
 - Navigation bar shows buggy animation when switching tabs

**Limitations**

 - Page state is not retained when switching to other tabs. Resolving this issue is a higher priority, but it will require a rewrite of certain areas of the application.
 - The mobile builds of ListEverywhere are not available in any app stores due to the potential costs of Cloud hosting, licenses, and API plans.
 - Items may have duplicate entries in the third party API (same names, different IDs) which may create difficulty when trying to match with recipes
 - Response time when accessing endpoints is slow, averaging at around two seconds for certain endpoints. This may be fixed by allocating more resources to the application and optimizing API calls
 - No images for recipes or items
 - Recipe steps and items cannot be moved to a different position
 - Users can only modify account information through the API
 - Lists cannot be sorted
