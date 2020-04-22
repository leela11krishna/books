Reference: https://bushansirgur.in/angular-2-and-spring-mvc-simple-crud-application/
Check the following in case if your connection pool taking too long to setup a connection with MySQL
https://stackoverflow.com/questions/50387952/how-to-resolve-unable-to-load-authentication-plugin-caching-sha2-password-issu

TOOLS AND TECHNOLOGIES USED
Spring 4
Hibernate 5
Angular 2
Bootstrap 3
MySQL
Jackson API 2.8.7
Maven 3.3.9
Eclipse Oxygen
Apache Tomcat 8
Visual Studio Code
1. First let’s create a DB for our application, open your MySQL and add execute the following command,

CREATE DATABASE bookdb;
Let’s start with the backend, Here is the project structure of Spring REST application

I don’t go over in detail about the REST API’s, I believe you all know that the concept of API. Long story short, API’s are nothing but URL’s when we hit those URL’s/Consume those URL’s we will get JSON data that’s it.
So let’s look at how to build such API’s using Spring REST

2. Since we are using a maven, first let’s add all the dependencies that are required for our application

pom.xml
Next step is to create a Property file inside the resources folder and specify the database properties

3. Once it’s done, let’s configure the spring and hibernate. Inside the config, package create a class called AppConfig and write the following code.

We will annotate this class with @Configuration, @PropertySource, @EnableTransactionManagement and @ComponentScan

@Configuration: It is a replacement to the XML based configuration for configuring spring beans. So instead of an XML file, we write a class and annotate that with @Configuration and define the beans in it using @Bean annotation on the methods.

@PropertySource: Specify the classpath of the property file. Reading values from a property file are far superior to hard coding them in our class files. If we hard code then we need to recompile if we want to change any of them.

@EnableTransactionManagement: It enables the transaction management. @ComponentScans: To scan the multiple packages.
4. Next step is to create MyWebAppInitializer class to initialize the servlet container, instead of using traditional web.xml, we will use java class that will extends AbstractAnnotationConfigDispatcherServletInitializer.

5. Next step is to create WebConfig class inside the config package, we will annotate this class with @Configuration, @EnableWebMvc, and @ComponentScan

@EnableWebMvc: @EnableWebMvc is used to enable Spring MVC. @EnableWebMvc is equivalent to <mvc:annotation-driven /> in XML.

Above three files are required for the spring and hibernate configuration.

6. Now, let’s write the model class, create a Book class inside the model package.

7. Now, let’s create an Interface for DAO, we will create BookDAO interface inside the dao package

8. Now, let’s implement those methods in the BookDaoImp class and annotate this class with @Repository

@Repository: It is an annotation that marks the specific class as a Data Access Object, thus clarifying its role.

9. Now, let’s create another Interface for service, we will be creating this service inside the service package

10. Now, let’s implement those methods in the BookServiceImp class and annotate this with @Service

@Service: This tells hibernate it is a Service class where you will have @Transactional etc Service layer related annotations so hibernate treats it as a Service component.

11. Finally, we will create a controller BookController inside the controller package and annotate with @RestController, which specifies that this is a REST controller


