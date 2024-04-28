### Singleton is a creational design pattern that lets you ensure that a class has only one instance while providing a global access point to this instance.

👉 The Singleton pattern solves two problems at the same time, violating the **Single Responsibility Principle**:

    1. Ensure that a class has just a single instance
    2. Provide a global access point to that instance


**All implementations of the Singleton have these two steps in common:**

- Make the default constructor private, to prevent other objects from using the new operator with the Singleton class.
- Create a static creation method that acts as a constructor. Under the hood, this method calls the private constructor to create an object and saves it in a static field. All following calls to this method return the cached object.

If your code has access to the Singleton class, then it’s able to call the Singleton’s static method. So whenever that method is called, the same object is always returned.

![image](https://github.com/Lokesh598/Low-Level-Design/assets/63910828/15108e44-7078-4fe7-b945-a754b2f42805)


The Singleton class declares the static method getInstance that returns the same instance of its own class.

The Singleton’s constructor should be hidden from the client code. Calling the getInstance method should be the only way of getting the Singleton object.


### How to Implement
1. Add a private static field to the class for storing the singleton instance.

2. Declare a public static creation method for getting the singleton instance.

3. Implement “lazy initialization” inside the static method. It should create a new object on its first call and put it into the static field. The method should always return that instance on all subsequent calls.

4. Make the constructor of the class private. The static method of the class will still be able to call the constructor, but not the other objects.

5. Go over the client code and replace all direct calls to the singleton’s constructor with calls to its static creation method.

### Pros
1. You can be sure that a class has only a single instance.

2. You gain a global access point to that instance.
   
3. The singleton object is initialized only when it’s requested for the first time.

### Cons
1. Violates the Single Responsibility Principle. The pattern solves two problems at the time.
 
2. The Singleton pattern can mask bad design, for instance, when the components of the program know too much about each other.
 
3. The pattern requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times.
