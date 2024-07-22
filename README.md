# Clean-architecture
## Clean Architecture and Clean Code Etiquette

## Clean Architecture

Clean Architecture is a software design philosophy that promotes a clear separation of concerns and helps developers build systems that are easy to maintain and extend. The principles of Clean Architecture are described in detail in the book "Clean Architecture: A Craftsman's Guide to Software Structure and Design" by Robert C. Martin (Uncle Bob). 

### Key Principles of Clean Architecture

1. **Separation of Concerns**: Different parts of the application should be responsible for different concerns. This separation makes the system easier to understand, develop, and maintain.

2. **Independence of Frameworks**: The architecture should not depend on any library or framework. Frameworks are tools, and their use should be minimized to avoid tight coupling.

3. **Testability**: The system should be easy to test. Business rules can be tested without the UI, database, web server, or any other external element.

4. **Independence of UI**: The user interface should be independent of the rest of the system. Changes to the UI should not affect the business rules.

5. **Independence of Database**: The business rules should not depend on the database. The database is a detail that can be changed without affecting the business logic.

6. **Independence of External Agencies**: The system should not depend on external libraries, frameworks, or services. These are implementation details that can change.

### Layers of Clean Architecture

1. **Entities**: These are the business objects of the application. They contain business rules and can be used across different use cases.

2. **Use Cases**: These contain the application-specific business rules. They orchestrate the flow of data to and from the entities and direct the user interface on what to display.

3. **Interface Adapters**: These convert data from the format most convenient for the use cases and entities to the format most convenient for external agents such as the database or the web.

4. **Frameworks and Drivers**: This is where the frameworks and tools lie: the database, the web framework, etc. These are the details, and they can be easily replaced.

### Diagram of Clean Architecture

```
          |--------------------|
          |   Entities         |
          |--------------------|
                 |
                 v
          |--------------------|
          |   Use Cases        |
          |--------------------|
                 |
                 v
          |--------------------|
          | Interface Adapters |
          |--------------------|
                 |
                 v
          |--------------------|
          | Frameworks & Drivers |
          |--------------------|
```

## Clean Code Etiquette

Clean Code is a philosophy that emphasizes writing code that is readable, maintainable, and understandable. The principles of Clean Code are described in detail in the book "Clean Code: A Handbook of Agile Software Craftsmanship" by Robert C. Martin.

### Key Principles of Clean Code

1. **Meaningful Names**: Use descriptive and unambiguous names for variables, functions, classes, etc. Names should convey intent.

2. **Small Functions**: Functions should be small and do one thing. They should be easy to understand and test.

3. **Single Responsibility Principle (SRP)**: A class should have one, and only one, reason to change. This principle promotes cohesion within the class.

4. **Open-Closed Principle (OCP)**: Software entities should be open for extension but closed for modification. This principle promotes flexibility and scalability.

5. **Liskov Substitution Principle (LSP)**: Subtypes must be substitutable for their base types. This principle ensures that a derived class does not affect the behavior of the base class.

6. **Interface Segregation Principle (ISP)**: Many client-specific interfaces are better than one general-purpose interface. This principle promotes the use of multiple, smaller interfaces.

7. **Dependency Inversion Principle (DIP)**: Depend on abstractions, not on concretions. This principle helps to decouple code and reduce dependencies.

### Writing Clean Code

1. **Commenting**: Comments should be used sparingly and only to explain why something is done, not what is done. Good code should be self-explanatory.

2. **Formatting**: Consistent formatting improves readability. Use consistent indentation, spacing, and braces.

3. **Error Handling**: Handle errors gracefully and provide meaningful error messages. Use exceptions for exceptional conditions.

4. **Testing**: Write unit tests for your code. Tests help to ensure that your code works as expected and makes it easier to refactor.

5. **Refactoring**: Continuously improve your code. Refactoring helps to keep the codebase clean and maintainable.

### Example of Clean Code

```csharp
public class OrderProcessor
{
    private readonly IOrderRepository _orderRepository;
    private readonly IPaymentService _paymentService;

    public OrderProcessor(IOrderRepository orderRepository, IPaymentService paymentService)
    {
        _orderRepository = orderRepository;
        _paymentService = paymentService;
    }

    public void ProcessOrder(Order order)
    {
        if (order == null)
        {
            throw new ArgumentNullException(nameof(order));
        }

        _paymentService.ProcessPayment(order.Payment);

        _orderRepository.Save(order);
    }
}
```

### Explanation of the Example

- **Meaningful Names**: The class, method, and variable names clearly indicate their purpose.
- **Single Responsibility Principle**: The `OrderProcessor` class has a single responsibility: processing orders.
- **Dependency Inversion Principle**: The class depends on abstractions (`IOrderRepository` and `IPaymentService`) rather than concrete implementations.
- **Error Handling**: The method checks for null orders and throws an appropriate exception.
- **Small Functions**: The `ProcessOrder` method is small and does one thing.

## Conclusion

Clean Architecture and Clean Code principles help to build software systems that are maintainable, flexible, and easy to understand. By adhering to these principles, developers can create high-quality code that is easy to work with and can evolve over time.

For more detailed information and advanced topics, refer to "Clean Architecture: A Craftsman's Guide to Software Structure and Design" by Robert C. Martin and "Clean Code: A Handbook of Agile Software Craftsmanship" by Robert C. Martin.
