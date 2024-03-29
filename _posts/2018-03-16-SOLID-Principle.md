---
title: SOLID Principles and Design Patterns.
tags: SOLIDDesign
header:
  theme: dark
  background: 'linear-gradient(135deg, rgb(34, 139, 87), rgb(139, 34, 139))'
article_header:
  type: overlay
  theme: dark
  background_color: '#203028'
  background_image:
    gradient: 'linear-gradient(135deg, rgba(34, 139, 87 , .4), rgba(139, 34, 139, .4))'
   
---

SOLID Principles and Design Patterns plays a key role in achieving all of the below points.







### SOLID Introduction 
1. SOLID principles are the design principles that enable us to manage most of the software design problems
2. The term SOLID is an acronym for five design principles intended to make software designs more understandable, flexible and maintainable
3. The principles are a subset of many principles promoted by Robert C. Martin
4. The SOLID acronym was first introduced by Michael Feathers

SOLID Acronym 
- S : Single Responsibility Principle (SRP) 
- O : Open closed Principle (OSP) 
- L :  Liskov substitution Principle (LSP) 
- I  :  Interface Segregation Principle (ISP) 
- D : Dependency Inversion Principle (DIP)

If we don’t follow SOLID Principles   
1. We end up with tight or strong coupling of the code with many other modules/applications
2. Tight coupling causes time to implement any new requirement, features or any bug fixes and some times it creates unknown issues
3. End up with a code which is not testable
4. End up with duplication of code
5. End up creating new bugs by fixing another bug
6. End up with many unknown issues in the application development cycle

Following SOLID Principles helps us to  
1. Achieve reduction in complexity of code
2. Increase readability, extensibility and maintenance
3. Reduce error and implement Reusability
4. Achieve Better testability
5. Reduce tight coupling

Solution to develop a successful application depends on  
Architecture : choosing an architecture is the first step in designing application based on the requirements. Example : MVC, WEBAPI, MVVM..etc
Design Principles : Application development process need to follow the design principles
Design Patterns : We need to choose correct design patterns to build the software


## Single responsive principal :

### Definition :
Class should have one and only one reasons to change . Should have single responsibility to change.
Single responsibility is the concept of a Class doing one specific thing (responsibility) and not trying to do more than it should, which is also referred to as High Cohesion.

### How to Recognize a Break of the SRP?
I can give you several rules of thumb.
- Class Has Too Many Dependencies.
- A constructor with too many input parameters implies many dependencies (hopefully you do inject dependencies). Another way too see many dependencies is by the test class.
If you need to mock too many objects, it usually means breaking the SRP.
- Method Has Too Many Parameters
- Same as the class’s smell. Think of the method’s parameters as dependencies.
- How easy is it to name the class? If a class is difficult to name, it is probably doing too much.
- How many public methods does the class have? 7+/-2 is a good rule of thumb. If the class has more than that, you should think about splitting it into several classes.
- Are there cohesive groups of public methods used in separate contexts?
- How many private methods or data members are there? If the class has a complex internal structure, you probably should refactor it so that the internals are packaged into separate smaller classes.
- And the easiest rule of thumb: how big is the class? If you have a C++ header file containing a single class that is more than a couple of hundred lines long, you should probably split it up.

Hence we can say that Single Responsibility Principle achieves the motivation points that we have just discussed.


### Open / Closed principal :

### Definition : 

In object-oriented programming, the open/closed principle states that "software entities such as classes, modules, functions, etc. should be open for extension, but closed for modification"

1. Which means, any new functionality should be implemented by adding new classes, attributes and methods, instead of changing the current ones or existing ones.

2. Bertrand Meyer is generally credited for having originated the term open/closed principle and This Principle is considered by Bob Martin as “the most important principle of object-oriented design”.

### Implementation guidelines
1. The simplest way to apply OCP is to implement the new functionality on new derived (sub) classes that inherit the original class implementation.

2. Another way is to allow client  to access the original class with an abstract interface, 

3. So, at any given point of time when there is a requirement change instead of touching the existing functionality it’s always suggested to create new classes and leave the original implementation untouched.

### What if I do not follow Open closed principle during a requirement enhancement in the development process. 
 
In that case, we end up with the following disadvantages
 
1. If a class or a function always allows the addition of new logic, as a developer we end up testing the entire functionality along with the requirement.
 
2. Also, as a developer we need to ensure to communicate the scope of the changes to the Quality Assurance team in advance so that they can gear up for enhanced regression testing along with the feature testing. 
 
3. Step 2 above is a costly process to adapt for any organization 
 
4. Not following the Open Closed Principle breaks the SRP since the class or function might end up doing multiple tasks.
 
5. Also, if the changes are implemented on the same class, Maintenance of the class becomes difficult since the code of the class increases by thousands of unorganized lines. 
 
Hope the above counter facts helps in understanding on why we need to follow the open closed principle.

Please follow the uploaded repo code which addresses this implementation. 


### Liskov Substitution Principle

### Definition : 
Substitutability is a principle in object-oriented programming and it states that, in a computer program, if S is a Subtype of T, then objects of type T may be replaced with objects of type S 

1. Which means, Derived types must be completely substitutable for their base types

2. More formally, the Liskov substitution principle (LSP) is a particular definition of a subtyping relation, called (strong) behavioral subtyping


### Implementation guidelines :

In the process of development we should ensure that  

1. No new exceptions can be thrown by the subtype unless they are part of the existing exception hierarchy.

2. We should also ensure that Clients should not know which specific subtype they are calling, nor should they need to know that. The client should behave the same regardless of the subtype instance that it is given.

3. And last but not the least, New derived classes just extend without replacing the functionality of old classes

To illustrate LSP, we have created different employee classes to calculate bonus of the employee. From the employee perspective we have implemented the Open closed principle. In the main program, we have created Employee objects which consists of both permanent and contract employee. 

If you take a closer look at this program the Derived types which are Permanent and TemporaryEmployee is completely substituted with the base type employee class.

So, based on the Liskov substitution principle we have achieved LSP by ensuring that Derived types are completely substitutable for their base types.


Now Let’s assume that we need to have a Contract Employee as one of the employee category. now the point here is a contract employee is not eligible for any bonus calculation and post implementing the Employee class so, we end up throwing exception at the runtime in the caclculatebonus() method. This violates the Liskov Substitution Principle. 

Hence, Please follow the uploaded repo code which addresses this issue. 

### Interface Segregation Principle

### Definition :
1. The interface-segregation principle (ISP) states that "no client should be forced to depend on methods it does not use".
2. Which means, Instead of one fat interface many small interfaces are preferred based on groups of methods with each one serving one submodule.
3. The ISP was first used and formulated by Robert C. Martin while consulting for Xerox. 


###  Dependency Inversion Principle

### Definition :
High-level modules should not depend on low-level modules. Both should depend on abstractions.
AND
Abstractions should not depend on details. Details should depend on abstractions.

To simplify this we can state that while designing the interaction between a high-level module and a low-level one, the interaction should be thought of as an abstract interaction between them.  


To understand DIP, let's take an example as below.

    public class CustomerBusinessLogic
       {
          public CustomerBusinessLogic()
          {
          }

          public string GetCustomerName(int id)
          {
              DataAccess dataAccess = DataAccessFactory.GetDataAccessObj();
              return dataAccess.GetCustomerName(id);
          }
       }

       public class DataAccessFactory
       {
          public static DataAccess GetDataAccessObj() 
          {
              return new DataAccess();
          }
       }

       public class DataAccess
       {
          public DataAccess()
          {
          }

          public string GetCustomerName(int id) {
              return "Dummy Customer Name"; // get it from DB in real app
          }
       }


In the above example, CustomerBusinessLogic class uses concrete DataAccess class and it is tightly coupled DataAccess class, nothing but it has direct dependency on DataAccess class. 

As per DIP definition, a high-level module should not depend on low-level modules. Both should depend on abstraction. So, first, decide which is the high-level module (class) and low-level module. High-level module is a module which depends on other modules. In our example, CustomerBusinessLogic depends on DataAccess class, so CustomerBusinessLogic is high-level module and DataAccess is low-level module. So, as per first rule of DIP, CustomerBusinessLogic should not depends on concrete DataAccess class, instead both classes depends on abstraction.

The second rule in DIP is "Abstractions should not depend on details. Details should depend on abstractions".

What is Abstraction here?
In English, abstraction means something which is non-concrete. In programming terms, the above CustomerBusinessLogic and DataAccess are concrete classes, meaning we can create objects of it. So, abstraction in programming is to create an interface or abstract class which is non-concrete. This means we cannot create an object of interface or abstract class. As per DIP, CustomerBusinessLogic (high-level module) should not depend on concrete DataAccess (low-level module) class. Both classes depend on abstractions, meaning both classes should depend on interface or abstract class.

Now, what should be in interface (or in abstract class)? As you can see, CustomerBusinessLogic uses GetCustomerName() method of DataAccess class. (In real life, there will be many customer related methods in DataAccess class). So, let's declare GetCustomerName(int id) method in the interface as shown below.

      public interface ICustomerDataAccess
      {
         string GetCustomerName(int id);
      }

Now, further illustration of ICustomerDataAccess in CustomerDataAccess class can be refer from uploaded example.


<!--more-->
