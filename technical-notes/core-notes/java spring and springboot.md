## Spring Framework
### Initialise a Spring Project
- [start.spring.io](start.spring.io) 
- Group ID - Package Name 
- Artifact ID - Class Name

### Why Spring?
- Spring Framework to create and manage **objects**
- Wire the objects automatically (auto-wiring)
### Spring Context
Spring context refers to an object container that manages the lifecycle of Java objects (beans).
The Spring context is responsible for creating, configuring, and managing beans within an application. It serves as a central hub that coordinates the interactions between different components and manages the lifecycle of these components.
```Java
var context = AnnotationConfigApplicationContext(HelloWorldConfiguration.class);
```
### Configuration Class
`@Configuration` 
Used to create and configure objects/beans that we need Spring to manage.
```Java
@Configuration
public class HelloWorldConfiguration {
}
```

### Spring Beans
#### Creating a Spring Bean
Beans are created in the **configuration file.**
```java
@Bean
public String lang(){
	return "Java"
}
```
- Name of the bean is: **lang**
We can retrieve a bean by the command.
```java
context.getBean("lang")
```
This retrieves the bean by *name.*
#### Creating Multiple Beans/Objects
To create multiple objects/beans, we can define multiple beans in the configuration file.
**HelloWorldConfiguration.java**
```Java
record Person(String name, int age){};
@Configuration
public class HelloWorldConfiguration {
	@Bean
	public String lang(){
		return "Java";
	}
	@Bean
	public int year(){
		return 1995;
	}
	@Bean
	public Person person(){
		return new Person("James Gosling", "67");
	}
	
	
}
```
#### Changing the name of Beans
We can add an attribute on `@Bean` 
```Java
record Address(String house, String city);
@Bean(name = "addressnew")
public Address address(){
	return new Address("Welsh Cottage", "Zurich");
}
```
Retrieving this object can be done by
```java
context.getBean("addressnew");
```
Another way of retrieving beans is by using the type of the bean, as below
```Java
context.getBean(Address.class);
```
p