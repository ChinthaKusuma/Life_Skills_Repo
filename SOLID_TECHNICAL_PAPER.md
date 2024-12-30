
# TECHNICAL PAPER

# SOLID Principles

The SOLID principles are a set of five design principles in object-oriented programming. They were introduced by Robert C. Martin (Uncle Bob) to help developers create software that is maintainable, scalable, and robust.

### Acronym:
- **S**: Single Responsibility Principle
- **O**: Open/Closed Principle
- **L**: Liskov Substitution Principle
- **I**: Interface Segregation Principle
- **D**: Dependency Inversion Principle

---

## 1. Single Responsibility Principle (SRP)

A class should have one, and only one, reason to change.

### Explanation:
Each class should only have one job or responsibility. This ensures that changes in one part of the system don’t affect unrelated areas.

### Benefits:
- Simplifies debugging, testing, and maintaining code.

### Sample Code:
```python
class EmployeeRepository:
    """Handles database logic related to employees."""
    def add_employee(self):
        print("Employee added to database")

class SalaryCalculator:
    """Handles logic related to salary."""
    def calculate_salary(self):
        print("Salary calculation logic executed.")
```
### Explanation:
- `EmployeeRepository` is only responsible for database-related logic.
- `SalaryCalculator` only handles salary-related logic.

---

## 2. Open/Closed Principle (OCP)

You should be able to add new features to a system without modifying existing code. This promotes flexibility and prevents bugs when existing, stable code is changed.

### Sample Code:
```python
class Operation:
    def calculate(self, data):
        pass

class SumOperation(Operation):
    def calculate(self, data):
        return sum(data)

class AverageOperation(Operation):
    def calculate(self, data):
        return sum(data) / len(data)

operations = [SumOperation(), AverageOperation()]
for operation in operations:
    print(operation.calculate([1, 2, 3, 4]))
```

---

## 3. Liskov Substitution Principle (LSP)

Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

### Explanation:
Subclasses should do what their parent class promises. If you replace a parent class with a subclass, everything should still work as expected, without errors

### Benefits:
- Prevents unexpected behavior in polymorphic code.

### Sample Code:
```python
class Bird:
    def move(self):
        print("Moving")

class FlyingBird(Bird):
    def fly(self):
        print("Flying")

class Penguin(Bird):
    def swim(self):
        print("Swimming")

birds = [FlyingBird(), Penguin()]
for bird in birds:
    bird.move()
```

---

## 4. Interface Segregation Principle (ISP)

A client should not be forced to depend on interfaces it does not use.

### Explanation:
Split large interfaces into smaller, more specific ones so that implementing classes only need to concern themselves with methods they actually use.

### Benefits:
- Reduces unnecessary dependencies and makes code easier to refactor.

### Sample Code:
```python
class Coder:
    def code(self):
        pass

class Designer:
    def design(self):
        pass

class Tester:
    def test(self):
        pass

class Developer(Coder, Tester):
    def code(self):
        print("Coding")

    def test(self):
        print("Testing")
```

---

## 5. Dependency Inversion Principle (DIP)

High-level modules should not depend on low-level modules. Both should depend on abstractions.

### Explanation:
- Rely on abstractions (e.g., interfaces) rather than concrete implementations.

### Benefits:
- Increases flexibility and testability by decoupling components.

### Sample Code:
```python
class Database:
    def connect(self):
        pass

class MySQLDatabase(Database):
    def connect(self):
        print("Connecting to MySQL")

class UserService:
    def __init__(self, db: Database):
        self.db = db

    def get_user(self):
        self.db.connect()

db = MySQLDatabase()
service = UserService(db)
service.get_user()
```


      

