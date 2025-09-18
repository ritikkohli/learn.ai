# Python Essentials for AI Development

## 1. Variables, Data Types, and Control Structures

### Variables in Python

Variables in Python are symbolic names that refer to objects. Python is dynamically typed, meaning you don't need to declare variable types explicitly[80][86].

```python
# Variable assignment examples
name = "Jane Doe"           # String
age = 19                    # Integer
height = 5.8               # Float
is_student = True          # Boolean
subjects = ["Math", "Physics"]  # List

# Check variable types
print(type(name))          # <class 'str'>
print(type(age))           # <class 'int'>
print(type(height))        # <class 'float'>
print(type(is_student))    # <class 'bool'>
```

### Python Data Types

Python has several built-in data types organized into categories[83][92]:

**Numeric Types:**
- `int` - Whole numbers (e.g., 42, -7)
- `float` - Decimal numbers (e.g., 3.14, -0.5)
- `complex` - Complex numbers (e.g., 3+4j)

**Text Type:**
- `str` - Strings (e.g., "Hello World")

**Sequence Types:**
- `list` - Ordered, mutable collection [1, 2, 3]
- `tuple` - Ordered, immutable collection (1, 2, 3)
- `range` - Sequence of numbers

**Mapping Type:**
- `dict` - Key-value pairs {"name": "John", "age": 25}

**Set Types:**
- `set` - Unordered collection of unique elements {1, 2, 3}
- `frozenset` - Immutable set

**Boolean Type:**
- `bool` - True or False

### Control Structures

Control structures manage the flow of program execution[89][102][105]:

#### Conditional Statements (if, elif, else)

```python
# Basic if statement
number = 10
if number > 0:
    print("Positive number")

# if-else statement
number = -5
if number > 0:
    print("Positive number")
else:
    print("Not a positive number")

# if-elif-else statement
score = 85
if score >= 90:
    print("Grade A")
elif score >= 80:
    print("Grade B")
elif score >= 70:
    print("Grade C")
else:
    print("Grade F")

# Ternary operator (one-line if-else)
result = "Pass" if score >= 60 else "Fail"
```

#### Loops

**For Loops:** Iterate over sequences
```python
# Iterating over a list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# Using range()
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)

# With enumerate for index and value
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
```

**While Loops:** Execute while condition is true
```python
count = 0
while count < 5:
    print(f"Count: {count}")
    count += 1

# Input validation example
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input.lower() == 'quit':
        break
    print(f"You entered: {user_input}")
```

#### Loop Control Statements

```python
# break - exit loop completely
for i in range(10):
    if i == 5:
        break
    print(i)  # Prints 0, 1, 2, 3, 4

# continue - skip current iteration
for i in range(5):
    if i == 2:
        continue
    print(i)  # Prints 0, 1, 3, 4
```

## 2. Functions, Modules, and Object-Oriented Programming

### Functions

Functions are reusable blocks of code that perform specific tasks[87]:

```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

# Function with default parameter
def greet_with_title(name, title="Mr."):
    return f"Hello, {title} {name}!"

# Function with multiple parameters
def calculate_area(length, width):
    """Calculate rectangle area"""
    return length * width

# Function with variable arguments
def sum_numbers(*args):
    return sum(args)

# Function with keyword arguments
def create_profile(**kwargs):
    profile = {}
    for key, value in kwargs.items():
        profile[key] = value
    return profile

# Usage examples
print(greet("Alice"))
print(greet_with_title("Smith", "Dr."))
area = calculate_area(10, 5)
total = sum_numbers(1, 2, 3, 4, 5)
profile = create_profile(name="John", age=30, city="New York")
```

### Modules

Modules are files containing Python code that can be imported and reused[81]:

**Creating a module (math_utils.py):**
```python
# math_utils.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

PI = 3.14159
```

**Using modules:**
```python
# Import entire module
import math_utils
result = math_utils.add(5, 3)

# Import specific functions
from math_utils import add, PI
result = add(5, 3)

# Import with alias
import math_utils as mu
result = mu.multiply(4, 5)

# Import built-in modules
import math
import datetime
import random

# Standard library examples
current_time = datetime.datetime.now()
random_number = random.randint(1, 100)
square_root = math.sqrt(16)
```

### Object-Oriented Programming (OOP)

Python supports four main OOP principles[81][87][90]:

#### Classes and Objects

```python
class Dog:
    # Class attribute (shared by all instances)
    species = "Canine"
    
    # Constructor method
    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age
    
    # Instance method
    def bark(self):
        return f"{self.name} says Woof!"
    
    # Another method
    def get_info(self):
        return f"{self.name} is {self.age} years old"

# Creating objects (instances)
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

# Accessing attributes and methods
print(dog1.name)        # Buddy
print(dog1.bark())      # Buddy says Woof!
print(dog2.get_info())  # Max is 5 years old
```

#### Inheritance

```python
# Base class (Parent)
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species
    
    def make_sound(self):
        return "Some generic sound"
    
    def sleep(self):
        return f"{self.name} is sleeping"

# Derived class (Child)
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name, "Canine")  # Call parent constructor
        self.breed = breed
    
    def make_sound(self):  # Override parent method
        return "Woof!"
    
    def fetch(self):  # New method specific to Dog
        return f"{self.name} is fetching the ball"

# Usage
my_dog = Dog("Buddy", "Golden Retriever")
print(my_dog.make_sound())  # Woof!
print(my_dog.sleep())       # Buddy is sleeping
print(my_dog.fetch())       # Buddy is fetching the ball
```

#### Encapsulation

```python
class BankAccount:
    def __init__(self, account_number, initial_balance):
        self.account_number = account_number
        self._balance = initial_balance  # Protected attribute
        self.__pin = "1234"  # Private attribute (name mangling)
    
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
            return f"Deposited ${amount}. New balance: ${self._balance}"
        return "Invalid deposit amount"
    
    def withdraw(self, amount, pin):
        if pin != self.__pin:
            return "Invalid PIN"
        if amount > 0 and amount <= self._balance:
            self._balance -= amount
            return f"Withdrew ${amount}. New balance: ${self._balance}"
        return "Insufficient funds or invalid amount"
    
    def get_balance(self):
        return self._balance

# Usage
account = BankAccount("123456", 1000)
print(account.deposit(500))
print(account.withdraw(200, "1234"))
```

#### Polymorphism

```python
class Shape:
    def area(self):
        pass
    
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, length, width):
        self.length = length
        self.width = width
    
    def area(self):
        return self.length * self.width
    
    def perimeter(self):
        return 2 * (self.length + self.width)

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14159 * self.radius ** 2
    
    def perimeter(self):
        return 2 * 3.14159 * self.radius

# Polymorphism in action
shapes = [Rectangle(5, 3), Circle(4), Rectangle(2, 8)]

for shape in shapes:
    print(f"Area: {shape.area():.2f}")
    print(f"Perimeter: {shape.perimeter():.2f}")
    print("---")
```

## 3. Data Structures (Lists, Dictionaries, Sets)

### Lists

Lists are ordered, mutable collections that allow duplicates[82][85][91]:

```python
# Creating lists
fruits = ["apple", "banana", "orange"]
numbers = [1, 2, 3, 4, 5]
mixed = ["hello", 42, 3.14, True]
empty_list = []

# List methods and operations
fruits.append("grape")          # Add to end
fruits.insert(1, "kiwi")        # Insert at index
removed = fruits.pop()          # Remove and return last item
fruits.remove("banana")         # Remove specific item
fruits.sort()                   # Sort in place
fruits.reverse()                # Reverse in place

# List comprehensions
squares = [x**2 for x in range(10)]
even_numbers = [x for x in range(20) if x % 2 == 0]
uppercase_fruits = [fruit.upper() for fruit in fruits]

# Slicing
print(numbers[1:4])     # [2, 3, 4]
print(numbers[:3])      # [1, 2, 3]
print(numbers[2:])      # [3, 4, 5]
print(numbers[-1])      # 5 (last item)

# Useful list operations
print(len(fruits))      # Length
print(max(numbers))     # Maximum value
print(sum(numbers))     # Sum of elements
print("apple" in fruits)  # Check membership
```

### Dictionaries

Dictionaries store key-value pairs and are ordered (Python 3.7+)[82][85][88]:

```python
# Creating dictionaries
student = {
    "name": "Alice",
    "age": 20,
    "grades": [85, 92, 78],
    "is_enrolled": True
}

# Dictionary operations
student["major"] = "Computer Science"  # Add new key-value pair
age = student["age"]                   # Access value
name = student.get("name", "Unknown")  # Safe access with default

# Dictionary methods
keys = student.keys()        # Get all keys
values = student.values()    # Get all values
items = student.items()      # Get key-value pairs

# Iterating over dictionaries
for key in student:
    print(f"{key}: {student[key]}")

for key, value in student.items():
    print(f"{key}: {value}")

# Dictionary comprehensions
squares_dict = {x: x**2 for x in range(5)}
filtered_dict = {k: v for k, v in student.items() if isinstance(v, str)}

# Nested dictionaries
students_db = {
    "student1": {"name": "Alice", "grade": 85},
    "student2": {"name": "Bob", "grade": 92}
}
```

### Sets

Sets are unordered collections of unique elements[82][85][88]:

```python
# Creating sets
fruits = {"apple", "banana", "orange"}
numbers = {1, 2, 3, 4, 5}
empty_set = set()  # Note: {} creates an empty dict, not set

# Set operations
fruits.add("grape")         # Add element
fruits.remove("banana")     # Remove element (raises error if not found)
fruits.discard("kiwi")      # Remove element (no error if not found)

# Set mathematical operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

union = set1 | set2              # {1, 2, 3, 4, 5, 6}
intersection = set1 & set2       # {3, 4}
difference = set1 - set2         # {1, 2}
symmetric_diff = set1 ^ set2     # {1, 2, 5, 6}

# Set comprehensions
even_squares = {x**2 for x in range(10) if x % 2 == 0}

# Practical use cases
# Remove duplicates from list
numbers_with_duplicates = [1, 2, 2, 3, 3, 3, 4]
unique_numbers = list(set(numbers_with_duplicates))

# Check for common elements
list1 = [1, 2, 3]
list2 = [3, 4, 5]
has_common = bool(set(list1) & set(list2))
```

## 4. File Handling and Exception Management

### File Handling

Python provides robust file handling capabilities[100][103][112]:

#### Basic File Operations

```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is line 2\n")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()  # Read entire file
    print(content)

# Reading line by line
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())  # strip() removes newline characters

# Reading specific number of lines
with open("example.txt", "r") as file:
    lines = file.readlines()  # Returns list of lines
    first_line = file.readline()  # Returns first line
```

#### File Modes

```python
# Different file modes
# "r" - Read only (default)
# "w" - Write (overwrites existing file)
# "a" - Append to existing file
# "x" - Create new file (fails if exists)
# "b" - Binary mode (e.g., "rb", "wb")
# "t" - Text mode (default)
# "+" - Read and write

# Examples
with open("data.txt", "a") as file:  # Append mode
    file.write("New line added\n")

with open("binary_file.bin", "wb") as file:  # Binary write
    file.write(b"Binary data")

with open("config.txt", "r+") as file:  # Read and write
    content = file.read()
    file.write("\nAdditional config")
```

### Exception Handling

Exception handling allows programs to gracefully handle errors[100][103][106][118]:

#### Basic Exception Handling

```python
# Basic try-except structure
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Handling multiple exceptions
try:
    number = int(input("Enter a number: "))
    result = 10 / number
    print(f"Result: {result}")
except ValueError:
    print("Invalid input! Please enter a number.")
except ZeroDivisionError:
    print("Cannot divide by zero!")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

#### File Exception Handling

```python
# Safe file handling with exceptions
def read_file_safely(filename):
    try:
        with open(filename, 'r') as file:
            content = file.read()
            return content
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found.")
        return None
    except PermissionError:
        print(f"Error: Permission denied to read '{filename}'.")
        return None
    except IOError:
        print(f"Error: I/O error occurred while reading '{filename}'.")
        return None
    except Exception as e:
        print(f"Unexpected error: {e}")
        return None

# Usage
content = read_file_safely("data.txt")
if content:
    print("File content:", content)
```

#### Advanced Exception Handling

```python
# Using finally block for cleanup
def process_file(filename):
    file = None
    try:
        file = open(filename, 'r')
        data = file.read()
        # Process data here
        return data.upper()
    except FileNotFoundError:
        print("File not found!")
        return None
    except Exception as e:
        print(f"Error processing file: {e}")
        return None
    finally:
        # This block always executes
        if file:
            file.close()
            print("File closed.")

# Raising custom exceptions
class CustomError(Exception):
    """Custom exception class"""
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

def validate_age(age):
    try:
        age = int(age)
        if age < 0 or age > 150:
            raise CustomError("Age must be between 0 and 150")
        return age
    except ValueError:
        raise CustomError("Age must be a number")

# Using custom exceptions
try:
    user_age = validate_age("25")
    print(f"Valid age: {user_age}")
except CustomError as e:
    print(f"Validation error: {e}")
```

## 5. Virtual Environments and Package Management with pip

### Virtual Environments

Virtual environments create isolated Python installations for different projects[101][104][107][113]:

#### Creating and Managing Virtual Environments

```bash
# Create a virtual environment
python -m venv myproject_env

# On Windows
python -m venv myproject_env

# On macOS/Linux
python3 -m venv myproject_env

# Activate the virtual environment
# Windows
myproject_env\Scripts\activate

# macOS/Linux
source myproject_env/bin/activate

# Deactivate the virtual environment
deactivate
```

#### Virtual Environment Best Practices

```bash
# Create project structure
mkdir my_ai_project
cd my_ai_project

# Create virtual environment in project folder
python -m venv .venv

# Activate virtual environment
# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate

# Verify you're in the virtual environment
which python    # Should show path to .venv
pip list        # Should show minimal packages
```

### Package Management with pip

pip is Python's package installer[101][104][107]:

#### Basic pip Commands

```bash
# Install a package
pip install package_name

# Install specific version
pip install package_name==1.2.3

# Install minimum version
pip install "package_name>=1.0"

# Install from requirements file
pip install -r requirements.txt

# Upgrade a package
pip install --upgrade package_name

# Uninstall a package
pip uninstall package_name

# List installed packages
pip list

# Show package information
pip show package_name

# Search for packages (deprecated, use PyPI website)
# pip search package_name
```

#### Requirements Files

```bash
# Generate requirements file from current environment
pip freeze > requirements.txt

# Install from requirements file
pip install -r requirements.txt
```

**Example requirements.txt:**
```
numpy==1.21.0
pandas>=1.3.0
matplotlib==3.4.2
scikit-learn>=0.24.0
```

#### Essential Packages for AI Development

```bash
# Activate your virtual environment first
source .venv/bin/activate  # or .venv\Scripts\activate on Windows

# Install essential AI/ML packages
pip install numpy pandas matplotlib seaborn
pip install scikit-learn jupyter notebook
pip install tensorflow  # or pytorch
pip install opencv-python pillow

# For data analysis
pip install scipy statsmodels

# For web scraping (if needed)
pip install requests beautifulsoup4

# For API development
pip install flask fastapi

# Development tools
pip install pytest black flake8
```

#### Working with Different Environments

```python
# Check which Python and pip you're using
import sys
print("Python executable:", sys.executable)

# In terminal/command prompt
which python    # macOS/Linux
where python    # Windows
pip --version   # Shows pip version and location
```

### Project Setup Example

Here's a complete example of setting up a Python AI project:

```bash
# 1. Create project directory
mkdir ai_learning_project
cd ai_learning_project

# 2. Create virtual environment
python -m venv .venv

# 3. Activate virtual environment
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

# 4. Upgrade pip
pip install --upgrade pip

# 5. Install essential packages
pip install numpy pandas matplotlib jupyter scikit-learn

# 6. Create requirements file
pip freeze > requirements.txt

# 7. Create project structure
mkdir src data notebooks tests
touch src/__init__.py
touch README.md .gitignore

# 8. Start Jupyter notebook (for interactive development)
jupyter notebook
```

**Example .gitignore for Python projects:**
```
# Virtual environment
.venv/
venv/
env/

# Python cache
__pycache__/
*.pyc
*.pyo

# Jupyter checkpoints
.ipynb_checkpoints/

# Data files
data/raw/
data/processed/

# OS files
.DS_Store
Thumbs.db
```

This comprehensive guide covers all the Python essentials you need to start your AI journey. Practice these concepts by building small projects and gradually move to more complex AI applications as you become comfortable with the fundamentals.