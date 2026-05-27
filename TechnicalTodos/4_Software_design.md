# Design patterns

## Singleton
- Creational design pattern, defines behavior of object creation
- Make sure there is only one instance
- Prevents accidental creation of multiple instances
- Ensures controlled and efficient use of resources (memory, connections)
- Simplifies coordination, since there is a single shared instance

> [!IMPORTANT]
> Real world applications 
- **Logging systems**
- **Configuration managers**
- **Database connections**
- **Thread pools**

> [!IMPORTANT]
> Best features 
- **Lazy or Eager Initialization**: An Instance can be created at class load time (eager) or when first needed (lazy).
- **Thread Safety**: Can be designed to work correctly in multithreaded environments.

## Factory
- Creational design pattern
- Defines interface for creating objects 
- Lets subclasses to decide which objects to instantiate
- Promotes loose coupling by delegating object creation to a method
- Usually not that useful for small applications

> [!IMPORTANT]
> Real world applications of factory
- Web browsers: Use factory methods to create different types of plugins or page renderers based on content type
- AndroidOS: Activities are often created through factories, devs usually just override ```onCreate()```
- Game dev: Use factory patterns to spwan enemies/items based on game level

> [!IMPORTANT] 
> The main components of Factory:
- **Creator**: abstract class or an interface that declares the factory method.
    - Typically contains a method that serves as a factory for creating objects. 
    - May also contain other methods that work with the created objects.
- **Concrete Creator**: subclasses of the Creator that implement the factory method to create specific types of objects. 
    - Each Concrete Creator is responsible for creating a particular product.
- **Product**: interface or abstract class for the objects that the factory method creates. 
    - The Product defines the common interface for all objects that the factory method can create.
- **Concrete Product**: Classes that are the actual objects that the factory method creates. 
    - Each Concrete Product class implements the Product interface or extends the Product abstract class.

## Observer
- Behavioral design pattern
- Creates 1 to many relation between subject and observers
- When subject state changes -> all observers are notified and updated automatically (sync comms)

> [!IMPORTANT]
> Real life applications
- **Social Media Notifications**: Users (*observers*), receive updates when someone they follow (*subject*) posts new content
- **Stock market apps**: Investors (*observers*) get real-time updates when stock prices (*subjects*) change
- **Event listeners in GUI's/Web**: UI components respond to user actions like click / keyboard

> [!IMPORTANT] 
> The main components of Observer:
- **Subject**: Maintains a list of observers, provides methods to add/remove them, and notifies them of state changes.
- **Observer**: Defines an interface with an update() method to ensure all observers receive updates consistently.
- **ConcreteSubject**: A specific subject that holds actual data. On state change, it notifies registered observers (e.g., a weather station).
- **ConcreteObserver**: Implements the observer interface and reacts to subject updates (e.g., a weather app showing weather updates).
