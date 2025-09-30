
# Slip 1:  


***

## Q1. Swap Two Numbers Using Reference Variables

### Approach

- Define a function that takes two integer references as parameters.
- Swap their values inside the function using a temporary variable.
- Call the function from `main` and display the numbers before and after swapping.


### Code

```cpp
#include <iostream>
using namespace std;

// [Swap Function Definition]
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x, y;
    // [Accept Input]
    cout << "Enter two numbers: ";
    cin >> x >> y;
    cout << "Before swap: x=" << x << " y=" << y << endl;
    // [Call Swap Function]
    swap(x, y);
    cout << "After swap: x=" << x << " y=" << y << endl;
    return 0;
}
```


### Explanation

- The `swap` function uses reference parameters (`int &a, int &b`), so changes inside the function affect the original variables in `main`.
- A temporary variable is used to hold one value during the swap.
- The program demonstrates the effect by printing values before and after the swap.


### Syntax Definitions

- **Reference Parameter (`int &a`)**: Allows the function to modify the original variable passed from the caller.


## Q2. Customer Class: Accept/Display/Filter by Name Starting with 'P'

### Approach

- Create a `Customer` class with attributes: code, name, and population.
- Accept details for `n` customers and store them in a vector.
- Display details of customers whose names start with the letter 'P'.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Class Definition]
class Customer {
    int code, population;
    string name;
public:
    // [Accept Input]
    void accept() {
        cout << "Code: "; cin >> code;
        cout << "Name: "; cin >> name;
        cout << "Population: "; cin >> population;
    }
    // [Display Function]
    void display() { cout << code << " " << name << " " << population << endl; }
    string getName() { return name; }
};

int main() {
    int n;
    cout << "Number of customers: ";
    cin >> n;
    vector<Customer> customers(n);
    for(auto &c : customers) c.accept();
    cout << "Customers with names starting with 'P':\n";
    for(auto &c : customers)
        if(!c.getName().empty() && c.getName()[0] == 'P')
            c.display();
    return 0;
}
```


### Explanation

- The `Customer` class encapsulates customer data and provides methods to accept and display it.
- The program reads `n` customers, then iterates through the list, displaying only those whose names start with 'P'.
- The check `!c.getName().empty()` ensures the name is not empty before accessing the first character.


### Syntax Definitions

- **Class**: A user-defined type that groups data and functions.
- **Vector**: A dynamic array from the C++ Standard Library that can grow or shrink in size.


## Q3. Library Management System (Case Study)

### Approach

- Define a `Book` class with attributes: title, author, year, and ISBN.
- Accept details for multiple books and store them in a vector.
- Allow the user to search for a book by ISBN and display its details if found.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Book Class Definition]
class Book {
    string title, author, isbn;
    int year;
public:
    // [Accept Input]
    void accept() {
        cout << "Title: "; cin >> title;
        cout << "Author: "; cin >> author;
        cout << "Year: "; cin >> year;
        cout << "ISBN: "; cin >> isbn;
    }
    // [Display Function]
    void display() {
        cout << title << " " << author << " " << year << " " << isbn << endl;
    }
    string getISBN() { return isbn; }
};

int main() {
    int n;
    cout << "Number of books: ";
    cin >> n;
    vector<Book> library(n);
    for(auto &b : library) b.accept();
    string searchISBN;
    cout << "Enter ISBN to search: ";
    cin >> searchISBN;
    bool found = false;
    for(auto &b : library) {
        if(b.getISBN() == searchISBN) {
            b.display();
            found = true;
        }
    }
    if(!found) cout << "Book not found." << endl;
    return 0;
}
```


### Explanation

- The `Book` class encapsulates book details and provides methods for input and output.
- The program reads `n` books, then searches for a book by ISBN and displays its details if found.
- The `found` flag ensures a message is shown if no book matches the search.


### Syntax Definitions

- **Class**: Encapsulates data and functions for a specific concept (here, a book).
- **Vector**: A resizable array from the C++ Standard Library.
- **Method**: A function defined inside a class.



---


---

# Slip 2:  


***

## Q1. Inline Function to Print Cube of a Number

### Approach

- Define an inline function that takes an integer and prints its cube.
- Call the function from `main` with user input.


### Code

```cpp
#include <iostream>
using namespace std;

// [Inline Function Definition]
inline void printCube(int n) {
    cout << "Cube of " << n << " is " << (n * n * n) << endl;
}

int main() {
    int x;
    cout << "Enter a number: ";
    cin >> x;
    printCube(x);
    return 0;
}
```


### Explanation

- The `printCube` function is marked `inline`, suggesting the compiler to expand it at the call site for efficiency.
- The function calculates the cube and prints it directly.
- User input is read in `main` and passed to the function.


### Syntax Definitions

- **inline**: A keyword that suggests the compiler to insert the function's code at each call site, potentially improving performance for small functions.

***

## Q2. Person Class: Accept/Display/Search by Contact Number

### Approach

- Create a `Person` class with attributes: name and contact number.
- Accept details for `n` persons and store them in a vector.
- Display all persons and search for a person by contact number.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Class Definition]
class Person {
    string name, contact;
public:
    // [Accept Input]
    void accept() {
        cout << "Enter name: "; cin >> name;
        cout << "Enter contact number: "; cin >> contact;
    }
    // [Display Function]
    void display() { cout << name << " " << contact << endl; }
    string getContact() { return contact; }
};

int main() {
    int n;
    cout << "How many persons? ";
    cin >> n;
    vector<Person> people(n);
    for(auto &p : people) p.accept();
    cout << "All persons:\n";
    for(auto &p : people) p.display();
    string searchContact;
    cout << "Enter contact to search: "; cin >> searchContact;
    bool found = false;
    for(auto &p : people) {
        if(p.getContact() == searchContact) {
            p.display();
            found = true;
        }
    }
    if(!found) cout << "No record found.\n";
    return 0;
}
```


### Explanation

- The `Person` class encapsulates name and contact number, with methods to accept and display data.
- The program reads `n` persons, displays all, and then searches for a person by contact number.
- If a match is found, the details are displayed; otherwise, a message is shown.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library that can grow or shrink in size.

***

## Q3. Generic Data Management System (Template Case Study)

### Approach

- Use a template class to manage different types of data (e.g., students, faculty, courses).
- Demonstrate with a `Student` class and a template `DataManager` class.
- Add and display records generically.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Template Class Definition]
template <typename T>
class DataManager {
    vector<T> records;
public:
    void add(const T& rec) { records.push_back(rec); }
    void display() { for(const auto& r : records) r.display(); }
};

// [Student Class Definition]
class Student {
public:
    string name; int roll; double grade;
    void accept() { cout << "Name: "; cin >> name;
                    cout << "Roll: "; cin >> roll;
                    cout << "Grade: "; cin >> grade; }
    void display() { cout << name << " " << roll << " " << grade << endl; }
};

int main() {
    DataManager<Student> dm;
    int n; cout << "No. of students: "; cin >> n;
    for(int i=0; i<n; ++i) {
        Student s; s.accept(); dm.add(s);
    }
    cout << "All students:" << endl;
    dm.display();
    return 0;
}
```


### Explanation

- The `DataManager` template class can store and manage any type of record.
- Here, it is used with the `Student` class to add and display student records.
- The template allows for easy extension to other types (e.g., faculty, courses) by changing the type parameter.


### Syntax Definitions

- **template <typename T>**: Allows the creation of generic classes or functions that work with any data type.
- **vector**: A dynamic array from the C++ Standard Library.

***



***

Say "next" to continue with Slip 3 in this format!

---

# Slip 3:  


***

## Q1. Display First ‘n’ Numbers of Fibonacci Series

### Approach

- Use a loop to generate and print the first `n` terms of the Fibonacci sequence.
- Start with the first two terms (0 and 1), then compute each next term as the sum of the previous two.


### Code

```cpp
#include <iostream>
using namespace std;

// [Fibonacci Function Definition]
void fibonacci(int n) {
    int a = 0, b = 1;
    cout << a << " " << b << " ";
    for(int i = 2; i < n; ++i) {
        int next = a + b;
        cout << next << " ";
        a = b;
        b = next;
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Enter number of terms: ";
    cin >> n;
    fibonacci(n);
    return 0;
}
```


### Explanation

- The `fibonacci` function prints the first two terms, then uses a loop to calculate and print each subsequent term.
- Each new term is the sum of the previous two, and the variables are updated accordingly.
- The user specifies how many terms to print.


### Syntax Definitions

- **void**: Indicates the function does not return a value.
- **for loop**: Used to repeat a block of code a specific number of times.

***

## Q2. Student Class: Print Details of Students with Grade 'O'

### Approach

- Define a `Student` class with attributes: name, age, and grade.
- Accept details for `n` students and store them in a vector.
- Display details of students whose grade is 'O'.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    string name;
    int age;
    char grade;
public:
    // [Accept Input]
    void accept() {
        cout << "Name: "; cin >> name;
        cout << "Age: "; cin >> age;
        cout << "Grade (O/A/B/C/D): "; cin >> grade;
    }
    // [Display Function]
    void display() { cout << name << " " << age << " " << grade << endl; }
    char getGrade() { return grade; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    cout << "Students with grade O:\n";
    for(auto &s : students)
        if(s.getGrade() == 'O') s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then iterates through the list, displaying only those with grade 'O'.
- The `getGrade` method is used to check each student's grade.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.
- **auto**: Automatically deduces the type of the variable from its initializer.

***

## Q3. Math Utility Library (Static Functions Case Study)

### Approach

- Create a class with static functions for mathematical operations (factorial and prime check).
- Call these functions directly using the class name, without creating an object.


### Code

```cpp
#include <iostream>
using namespace std;

// [MathLib Class Definition]
class MathLib {
public:
    // [Static Factorial Function]
    static int factorial(int n) {
        int result = 1;
        for(int i = 1; i <= n; ++i) result *= i;
        return result;
    }
    // [Static Prime Check Function]
    static bool isPrime(int n) {
        if(n < 2) return false;
        for(int i = 2; i*i <= n; ++i)
            if(n % i == 0) return false;
        return true;
    }
};

int main() {
    int n;
    cout << "Enter number for factorial: "; cin >> n;
    cout << "Factorial: " << MathLib::factorial(n) << endl;
    cout << "Enter number for prime check: "; cin >> n;
    cout << (MathLib::isPrime(n) ? "Prime" : "Not Prime") << endl;
    return 0;
}
```


### Explanation

- The `MathLib` class provides static methods for factorial and prime checking.
- Static methods can be called using the class name without creating an object.
- The program demonstrates both functionalities with user input.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **bool**: A data type that can hold `true` or `false`.
- **?: (ternary operator)**: A shorthand for if-else to choose between two values.

---

# Slip 4:  


***

## Q1. Template Program to Find Area of Circle \& Rectangle (Different Data Types)

### Approach

- Use function templates to calculate area for both circle and rectangle.
- Demonstrate the template with different data types (e.g., int, double).


### Code

```cpp
#include <iostream>
using namespace std;

// [Template Function for Area of Circle]
template <typename T>
T areaCircle(T r) {
    return 3.14159 * r * r;
}
// [Template Function for Area of Rectangle]
template <typename T>
T areaRectangle(T l, T b) {
    return l * b;
}
int main() {
    cout << "Area of circle (double, r=2.5): " << areaCircle(2.5) << endl;
    cout << "Area of rectangle (int, l=5, b=6): " << areaRectangle(5, 6) << endl;
    return 0;
}
```


### Explanation

- The `areaCircle` and `areaRectangle` functions are templates, so they work with any numeric type.
- The code demonstrates usage with both `double` and `int` types.
- The formulas for area are directly implemented in the respective functions.


### Syntax Definitions

- **template <typename T>**: Allows the function to operate with any data type specified at the call site.
- **endl**: Outputs a newline and flushes the output buffer.

***

## Q2. Multilevel Inheritance: Employee/Manager/SeniorManager

### Approach

- Use a base class `Employee` with common attributes.
- Derive `Manager` from `Employee`, and `SeniorManager` from `Manager`.
- Each class adds its own specific data and methods.


### Code

```cpp
#include <iostream>
using namespace std;
// [Base Class: Employee]
class Employee {
protected:
    string name; int id;
public:
    void accept() { cout << "Name: "; cin >> name; cout << "ID: "; cin >> id; }
    void display() { cout << name << " " << id << endl; }
};
// [Derived Class: Manager]
class Manager : public Employee {
protected:
    string department;
public:
    void accept() { Employee::accept(); cout << "Department: "; cin >> department; }
    void display() { Employee::display(); cout << "Department: " << department << endl; }
};
// [Further Derived: SeniorManager]
class SeniorManager : public Manager {
    int yearsExp;
public:
    void accept() { Manager::accept(); cout << "Years Experience: "; cin >> yearsExp; }
    void display() { Manager::display(); cout << "Experience: " << yearsExp << endl; }
};

int main() {
    SeniorManager sm;
    sm.accept();
    sm.display();
    return 0;
}
```


### Explanation

- `Employee` is the base class with name and id.
- `Manager` adds a department, and `SeniorManager` adds years of experience.
- Each class's `accept` and `display` methods call the parent class's method to handle inherited data.


### Syntax Definitions

- **protected**: Members are accessible in the class and its derived classes.
- **public inheritance**: Derived class inherits all public and protected members of the base class.

***

## Q3. Publishing Company Case Study (Inheritance \& Exception Handling)

### Approach

- Use a base class `Publication` with title and price.
- Derive `Book` (adds pages) and `Tape` (adds play time).
- Use exception handling to set values to zero if invalid input is given.


### Code

```cpp
#include <iostream>
using namespace std;
class Publication {
protected:
    string title; float price;
public:
    void accept() { cout<<"Title: "; cin>>title; cout<<"Price: "; cin>>price; }
    void display() { cout<<"Title: "<<title<<" Price: "<<price<<endl; }
};
class Book: public Publication {
    int pages;
public:
    void accept() {
        try {
            Publication::accept();
            cout << "Pages: "; cin >> pages;
            if (pages <= 0) throw 1;
        } catch (...) {
            title = ""; price = 0; pages = 0;
            cout << "Error! Book values set to zero.\n";
        }
    }
    void display() { Publication::display(); cout<<"Pages: "<<pages<<endl; }
};
class Tape: public Publication {
    float playTime;
public:
    void accept() {
        try {
            Publication::accept();
            cout << "Play Time: "; cin >> playTime;
            if (playTime <= 0) throw 1;
        } catch (...) {
            title = ""; price = 0; playTime = 0;
            cout << "Error! Tape values set to zero.\n";
        }
    }
    void display() { Publication::display(); cout<<"Play Time: "<<playTime<<endl; }
};
int main() {
    Book b; Tape t;
    cout<<"---Book---\n"; b.accept();
    cout<<"---Tape---\n"; t.accept();
    b.display(); t.display();
    return 0;
}
```


### Explanation

- `Publication` is the base class for common data.
- `Book` and `Tape` inherit from `Publication` and add their own fields.
- Exception handling ensures that if invalid input is given (pages or play time ≤ 0), all values are set to zero and an error message is shown.


### Syntax Definitions

- **try-catch**: Used for exception handling; code in `try` is executed, and if an exception is thrown, control passes to `catch`.
- **public inheritance**: Allows derived classes to access public and protected members of the base class.

---

# Slip 5:  


***

## Q1. Function Overloading: Volume of Cone and Sphere

### Approach

- Use function overloading to define two `volume` functions: one for a cone (radius and height), one for a sphere (radius only).
- Calculate the volume using the respective formulas and demonstrate both in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Volume of Cone]
double volume(double r, double h) {
    return (3.14159 * r * r * h) / 3;
}
// [Volume of Sphere]
double volume(double r) {
    return (4.0 / 3.0) * 3.14159 * r * r * r;
}
int main() {
    cout << "Volume of cone (r=2, h=4): " << volume(2, 4) << endl;
    cout << "Volume of sphere (r=2): " << volume(2) << endl;
    return 0;
}
```


### Explanation

- Two `volume` functions are defined: one takes two arguments (cone), one takes one (sphere).
- The compiler chooses the correct function based on the number of arguments.
- The formulas for volume are directly implemented.


### Syntax Definitions

- **Function Overloading**: Defining multiple functions with the same name but different parameter lists.
- **double**: A data type for floating-point numbers.

***

## Q2. Template Vector Class (Create, Modify, Scalar Multiply, Display)

### Approach

- Create a template class for a vector of type `T`.
- Implement methods to create, modify, multiply by a scalar, and display the vector.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

template <typename T>
class MyVector {
    vector<T> data;
public:
    // [Create Vector]
    void create(int n) {
        cout << "Enter " << n << " elements:\n";
        T val;
        for (int i = 0; i < n; ++i) {
            cin >> val; data.push_back(val);
        }
    }
    // [Modify Element]
    void modify(int idx, T val) {
        if (idx >= 0 && idx < data.size()) data[idx] = val;
    }
    // [Scalar Multiplication]
    void multiply(T scalar) {
        for (auto &v : data) v *= scalar;
    }
    // [Display Vector]
    void display() {
        cout << "(";
        for (size_t i = 0; i < data.size(); ++i) {
            cout << data[i];
            if (i < data.size() - 1) cout << ",";
        }
        cout << ")\n";
    }
};

int main() {
    MyVector<int> v;
    v.create(3);
    v.display();
    v.modify(1, 99); v.display();
    v.multiply(2); v.display();
    return 0;
}
```


### Explanation

- The template class `MyVector` can store any type of vector.
- Methods allow creation, modification, scalar multiplication, and display of the vector.
- Demonstrated with `int` type in `main`.


### Syntax Definitions

- **template <typename T>**: Allows the class to work with any data type.
- **vector**: A dynamic array from the C++ Standard Library.
- **auto**: Automatically deduces the type of the variable from its initializer.

***

## Q3. Math Utility Library (Static Functions Case Study)

### Approach

- Create a class with static functions for factorial and prime checking.
- Call these functions directly using the class name, without creating an object.


### Code

```cpp
#include <iostream>
using namespace std;

class MathLib {
public:
    // [Static Factorial Function]
    static int factorial(int n) {
        int result = 1;
        for(int i = 1; i <= n; ++i) result *= i;
        return result;
    }
    // [Static Prime Check Function]
    static bool isPrime(int n) {
        if(n < 2) return false;
        for(int i = 2; i*i <= n; ++i)
            if(n % i == 0) return false;
        return true;
    }
};

int main() {
    int x;
    cout << "Enter number for factorial: "; cin >> x;
    cout << "Factorial: " << MathLib::factorial(x) << endl;
    cout << "Enter number for prime check: "; cin >> x;
    cout << (MathLib::isPrime(x) ? "Prime" : "Not Prime") << endl;
    return 0;
}
```


### Explanation

- The `MathLib` class provides static methods for factorial and prime checking.
- Static methods can be called using the class name without creating an object.
- The program demonstrates both functionalities with user input.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **bool**: A data type that can hold `true` or `false`.
- **?: (ternary operator)**: A shorthand for if-else to choose between two values.

---

# Slip 6:  


***

## Q1. Inline Function to Calculate Area of a Circle (with Default Argument)

### Approach

- Define an inline function to calculate the area of a circle.
- Use a default argument for the radius so the function can be called with or without a parameter.
- Demonstrate both default and user-supplied radius in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Inline Function with Default Argument]
inline double area(double r = 1.0) {
    return 3.14159 * r * r;
}

int main() {
    cout << "Default radius area: " << area() << endl;
    double rad;
    cout << "Enter radius: ";
    cin >> rad;
    cout << "Area with radius " << rad << ": " << area(rad) << endl;
    return 0;
}
```


### Explanation

- The `area` function is marked `inline` and has a default argument (`r = 1.0`).
- If called without an argument, it uses the default radius of 1.0.
- The user can also input a custom radius, which is then used in the calculation.


### Syntax Definitions

- **inline**: Suggests the compiler to expand the function at the call site for efficiency.
- **Default Argument**: Allows a function parameter to have a default value if not provided by the caller.

***

## Q2. Manager Class (Handles Administrative \& Technical Details)

### Approach

- Create a `Manager` class with attributes for name, department (administrative), and skillset (technical).
- Provide methods to accept and display all details.


### Code

```cpp
#include <iostream>
using namespace std;

// [Manager Class Definition]
class Manager {
    string name, dept, skillset;
public:
    void accept() {
        cout << "Name: "; cin >> name;
        cout << "Department: "; cin >> dept;
        cout << "Skillset: "; cin >> skillset;
    }
    void display() {
        cout << name << " " << dept << " " << skillset << endl;
    }
};

int main() {
    Manager mgr;
    mgr.accept();
    mgr.display();
    return 0;
}
```


### Explanation

- The `Manager` class encapsulates both administrative (department) and technical (skillset) details.
- The `accept` method reads all fields from the user, and `display` prints them.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.

***

## Q3. Parking Management System (Constructor/Destructor Case Study)

### Approach

- Define a `Vehicle` class with attributes for plate number, owner, and entry time.
- Use a constructor to initialize and display entry, and a destructor to display exit.
- Demonstrate object lifecycle in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Vehicle Class with Constructor/Destructor]
class Vehicle {
    string plate, owner;
    int entryTime;
public:
    Vehicle(string p, string o, int t) : plate(p), owner(o), entryTime(t) {
        cout << "Vehicle Entered: " << plate << endl;
    }
    ~Vehicle() {
        cout << "Vehicle Exited: " << plate << endl;
    }
    void display() { cout << plate << " " << owner << " " << entryTime << endl; }
};

int main() {
    Vehicle v("MH12AB1234", "Rahul", 1005);
    v.display();
    return 0; // Destructor called automatically
}
```


### Explanation

- The constructor initializes the vehicle and prints an entry message.
- The destructor prints an exit message when the object goes out of scope (at the end of `main`).
- The `display` method shows all vehicle details.


### Syntax Definitions

- **Constructor**: A special function that initializes an object when it is created.
- **Destructor**: A special function that is called when an object is destroyed, used for cleanup.
- **Member Initializer List**: The `: plate(p), owner(o), entryTime(t)` syntax initializes members before the constructor body runs.

---

# Slip 7:  


***

## Q1. C++ Program to Calculate Area and Perimeter of Rectangle

### Approach

- Define a `Rectangle` class with member variables for length and width.
- Provide member functions to calculate area and perimeter.
- Accept input from the user and display the results.


### Code

```cpp
#include <iostream>
using namespace std;

// [Rectangle Class Definition]
class Rectangle {
    double length, width;
public:
    void accept() {
        cout << "Enter length: "; cin >> length;
        cout << "Enter width: "; cin >> width;
    }
    double area() { return length * width; }
    double perimeter() { return 2 * (length + width); }
};

int main() {
    Rectangle r;
    r.accept();
    cout << "Area: " << r.area() << endl;
    cout << "Perimeter: " << r.perimeter() << endl;
    return 0;
}
```


### Explanation

- The `Rectangle` class encapsulates the dimensions and provides methods for area and perimeter.
- The `accept` method reads values from the user.
- The results are displayed in `main`.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **double**: A data type for floating-point numbers.

***

## Q2. Class `Time` with Operator Overloading (!=, >>, <<)

### Approach

- Define a `Time` class with hours, minutes, and seconds.
- Overload the `!=` operator to compare two `Time` objects.
- Overload the `>>` and `<<` operators for input and output.


### Code

```cpp
#include <iostream>
using namespace std;

// [Time Class Definition]
class Time {
    int h, m, s;
public:
    // [Input Operator >>]
    friend istream& operator>>(istream& in, Time& T) {
        cout << "Hours: "; in >> T.h;
        cout << "Minutes: "; in >> T.m;
        cout << "Seconds: "; in >> T.s;
        return in;
    }
    // [Output Operator <<]
    friend ostream& operator<<(ostream& out, const Time& T) {
        out << T.h << ":" << T.m << ":" << T.s;
        return out;
    }
    // [Inequality Operator !=]
    bool operator!=(const Time& t) {
        return h != t.h || m != t.m || s != t.s;
    }
};

int main() {
    Time t1, t2;
    cin >> t1;
    cin >> t2;
    cout << "Time 1: " << t1 << endl;
    cout << "Time 2: " << t2 << endl;
    if (t1 != t2)
        cout << "Times are not equal." << endl;
    else
        cout << "Times are equal." << endl;
    return 0;
}
```


### Explanation

- The `Time` class uses friend functions to overload input and output operators.
- The `!=` operator checks if any component of the time differs.
- Demonstrates operator overloading for user-defined types.


### Syntax Definitions

- **friend**: Allows a function to access private/protected members of a class.
- **operator overloading**: Redefining operators for user-defined types.
- **istream/ostream**: Standard input/output stream classes in C++.

***

## Q3. Financial Application: Money Class with Operator Overloading

### Approach

- Define a `Money` class with rupees and paise.
- Overload the `+` operator to add two `Money` objects, normalizing paise to rupees.
- Provide a display method.


### Code

```cpp
#include <iostream>
using namespace std;

// [Money Class Definition]
class Money {
    int rupees, paise;
public:
    Money(int r=0, int p=0): rupees(r), paise(p) { normalize(); }
    void normalize() { rupees += paise/100; paise %= 100; }
    Money operator+(const Money& m) { return Money(rupees + m.rupees, paise + m.paise); }
    void display() { cout << rupees << " Rupees " << paise << " Paise\n"; }
};

int main() {
    Money m1(10,150), m2(3,95), m3;
    m3 = m1 + m2;
    m3.display();
    return 0;
}
```


### Explanation

- The `Money` class handles currency addition and normalization (e.g., 150 paise = 1 rupee 50 paise).
- The `+` operator is overloaded to add two `Money` objects.
- The `display` method prints the result in a readable format.


### Syntax Definitions

- **operator+**: Overloads the `+` operator for user-defined types.
- **Constructor with default arguments**: Allows object creation with or without parameters.
- **Normalization**: Adjusts paise to rupees if paise >= 100.

---

# Slip 8:  


***

## Q1. Function Overloading: Swap for Int and Double

### Approach

- Define two overloaded `swap` functions: one for `int` and one for `double`.
- Use reference parameters to swap values in place.
- Demonstrate both swaps in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Swap Ints]
void swap(int &a, int &b) {
    int t = a; a = b; b = t;
}
// [Swap Doubles]
void swap(double &a, double &b) {
    double t = a; a = b; b = t;
}
int main() {
    int i1 = 5, i2 = 9;
    double d1 = 2.5, d2 = 8.7;
    swap(i1, i2); swap(d1, d2);
    cout << "Swapped ints: " << i1 << " " << i2 << endl;
    cout << "Swapped doubles: " << d1 << " " << d2 << endl;
    return 0;
}
```


### Explanation

- Two `swap` functions are defined, one for `int` and one for `double`.
- Reference parameters allow the function to modify the original variables.
- Demonstrates function overloading and in-place swapping for both types.


### Syntax Definitions

- **Function Overloading**: Defining multiple functions with the same name but different parameter types.
- **Reference Parameter**: Allows a function to modify the caller's variable directly.

***

## Q2. Mobile Class with Accept/Sale/Purchase

### Approach

- Create a `Mobile` class with attributes: company, model, color, price, quantity.
- Implement methods to accept details, sell (decrement quantity), purchase (increment quantity), and display.


### Code

```cpp
#include <iostream>
using namespace std;

// [Mobile Class Definition]
class Mobile {
    string company, model, color;
    double price;
    int quantity;
public:
    void accept() {
        cout << "Company: "; cin >> company;
        cout << "Model: "; cin >> model;
        cout << "Color: "; cin >> color;
        cout << "Price: "; cin >> price;
        cout << "Quantity: "; cin >> quantity;
    }
    void sale(int qty) {
        if (quantity >= qty) {
            quantity -= qty;
            cout << "Sale success. Remaining: " << quantity << endl;
        } else cout << "Not enough stock.\n";
    }
    void purchase(int qty) {
        quantity += qty;
        cout << "Purchased. Total stock: " << quantity << endl;
    }
    void display() {
        cout << company << " " << model << " " << color << " " << price << " " << quantity << endl;
    }
};

int main() {
    Mobile m;
    m.accept();
    m.display();
    m.sale(3); // Sale demo
    m.purchase(5); // Purchase demo
    m.display();
    return 0;
}
```


### Explanation

- The `Mobile` class manages product details and stock operations.
- The `sale` method checks for sufficient stock before selling.
- The `purchase` method adds to the stock.
- The `display` method prints all details.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **Method**: A function defined inside a class.

***

## Q3. Bookshop Management (Inventory \& Sale Case Study)

### Approach

- Define a `Book` class with attributes: author, title, price, publisher, stock.
- Accept book details, search by title/author, check stock, and print bill if available.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Book Class Definition]
class Book {
    string author, title, publisher;
    double price;
    int stock;
public:
    void accept() {
        cout << "Title: "; cin >> title;
        cout << "Author: "; cin >> author;
        cout << "Publisher: "; cin >> publisher;
        cout << "Price: "; cin >> price;
        cout << "Stock: "; cin >> stock;
    }
    bool match(string t, string a) { return title==t && author==a; }
    bool available(int qty) { return stock >= qty; }
    double bill(int qty) { return price * qty; }
    void sell(int qty) { stock -= qty; }
    void display() {
        cout << title << " " << author << " " << publisher << " " << price << " " << stock << endl;
    }
};

int main() {
    int n; cout << "Books? "; cin >> n;
    vector<Book> shop(n);
    for(auto &b:shop) b.accept();
    string reqTitle, reqAuthor; int reqQty;
    cout << "Title/Author/QTY: "; cin >> reqTitle >> reqAuthor >> reqQty;
    for(auto &b:shop) {
        if(b.match(reqTitle, reqAuthor)) {
            if(b.available(reqQty)) {
                cout << "Total Cost: " << b.bill(reqQty) << endl;
                b.sell(reqQty);
            } else cout << "Insufficient stock\n";
        }
    }
    return 0;
}
```


### Explanation

- The `Book` class manages inventory and sales operations.
- The program accepts book details, searches for a match, checks stock, and processes the sale.
- The bill is calculated and stock updated if the sale is successful.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **Method**: A function defined inside a class.

---

# Slip 9:  


***

## Q1. Circle Class: Area and Circumference

### Approach

- Define a `Circle` class with a private radius attribute.
- Provide member functions to calculate area and circumference.
- Accept radius from the user and display the results.


### Code

```cpp
#include <iostream>
using namespace std;

// [Circle Class Definition]
class Circle {
    double radius;
public:
    void accept() { cout << "Enter radius: "; cin >> radius; }
    double area() { return 3.14159 * radius * radius; }
    double circumference() { return 2 * 3.14159 * radius; }
};

int main() {
    Circle c;
    c.accept();
    cout << "Area: " << c.area() << endl;
    cout << "Circumference: " << c.circumference() << endl;
    return 0;
}
```


### Explanation

- The `Circle` class encapsulates the radius and provides methods for area and circumference.
- The `accept` method reads the radius from the user.
- The results are displayed in `main`.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **double**: A data type for floating-point numbers.

***

## Q2. MyPoint Class (with Copy Constructor)

### Approach

- Define a `MyPoint` class with two coordinates (x, y).
- Implement a copy constructor to initialize a new object from an existing one.
- Demonstrate copying in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [MyPoint Class Definition]
class MyPoint {
    int x, y;
public:
    MyPoint(int a, int b) : x(a), y(b) {}
    MyPoint(const MyPoint &p) { x = p.x; y = p.y; }
    void display() { cout << "x: " << x << " y: " << y << endl; }
};

int main() {
    MyPoint p1(3,4);
    MyPoint p2 = p1; // Copy
    p1.display(); p2.display();
    return 0;
}
```


### Explanation

- The `MyPoint` class has a parameterized constructor and a copy constructor.
- `MyPoint p2 = p1;` uses the copy constructor to create a new object with the same values as `p1`.
- The `display` method prints the coordinates.


### Syntax Definitions

- **Copy Constructor**: A special constructor that initializes an object using another object of the same class.
- **Member Initializer List**: The `: x(a), y(b)` syntax initializes members before the constructor body runs.

***

## Q3. Financial Application: Money Class with Operator Overloading

### Approach

- Define a `Money` class with rupees and paise.
- Overload the `+` operator to add two `Money` objects, normalizing paise to rupees.
- Provide a display method.


### Code

```cpp
#include <iostream>
using namespace std;

// [Money Class Definition]
class Money {
    int rupees, paise;
public:
    Money(int r=0, int p=0): rupees(r), paise(p) { normalize(); }
    void normalize() { rupees += paise/100; paise %= 100; }
    Money operator+(const Money& m) { return Money(rupees + m.rupees, paise + m.paise); }
    void display() { cout << rupees << " Rupees " << paise << " Paise\n"; }
};

int main() {
    Money m1(7,190), m2(3,50), m3;
    m3 = m1 + m2;
    m3.display();
    return 0;
}
```


### Explanation

- The `Money` class handles currency addition and normalization (e.g., 190 paise = 1 rupee 90 paise).
- The `+` operator is overloaded to add two `Money` objects.
- The `display` method prints the result in a readable format.


### Syntax Definitions

- **operator+**: Overloads the `+` operator for user-defined types.
- **Constructor with default arguments**: Allows object creation with or without parameters.
- **Normalization**: Adjusts paise to rupees if paise >= 100.

---

# Slip 10:  


***

## Q1. Class Template to Compare Numbers of Different Types

### Approach

- Use a class template to compare two values of any type (int, float, etc.).
- Provide a method to display which value is greater or if they are equal.
- Demonstrate with different data types in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Template Class for Comparison]
template <typename T>
class Compare {
    T a, b;
public:
    Compare(T x, T y) : a(x), b(y) {}
    void displayGreater() {
        if(a > b)
            cout << a << " is greater than " << b << endl;
        else if(b > a)
            cout << b << " is greater than " << a << endl;
        else
            cout << a << " and " << b << " are equal." << endl;
    }
};

int main() {
    Compare<int> cmp1(5, 10);
    cmp1.displayGreater();
    Compare<float> cmp2(2.5, 1.5);
    cmp2.displayGreater();
    return 0;
}
```


### Explanation

- The `Compare` template class works for any data type that supports comparison operators.
- The `displayGreater` method compares the two values and prints the result.
- Demonstrated with both `int` and `float` types in `main`.


### Syntax Definitions

- **template <typename T>**: Allows the class to work with any data type specified at instantiation.
- **Class Template**: A blueprint for creating classes that operate with generic types.

***

## Q2. Employee and Manager Inherited Class

### Approach

- Define a base class `Employee` with name, code, and designation.
- Derive a `Manager` class from `Employee` that adds years of experience and salary.
- Accept and display all details for a manager.


### Code

```cpp
#include <iostream>
using namespace std;

// [Employee Base Class]
class Employee {
protected:
    string name, designation;
    int code;
public:
    void accept() {
        cout << "Name: "; cin >> name;
        cout << "Code: "; cin >> code;
        cout << "Designation: "; cin >> designation;
    }
    void display() { cout << name << " " << code << " " << designation << endl; }
};

// [Manager Derived Class]
class Manager : public Employee {
    int exp;
    double salary;
public:
    void accept() {
        Employee::accept();
        cout << "Years Experience: "; cin >> exp;
        cout << "Salary: "; cin >> salary;
    }
    void display() {
        Employee::display();
        cout << "Experience: " << exp << " Salary: " << salary << endl;
    }
};

int main() {
    Manager m;
    m.accept();
    m.display();
    return 0;
}
```


### Explanation

- The `Manager` class inherits from `Employee` and adds its own fields.
- The `accept` and `display` methods in `Manager` call the base class methods to handle inherited data.
- Demonstrates inheritance and method overriding.


### Syntax Definitions

- **protected**: Members are accessible in the class and its derived classes.
- **public inheritance**: Derived class inherits all public and protected members of the base class.

***

## Q3. Employee Payroll System (Inheritance Case Study)

### Approach

- Use a base class `Employee` for common data (name, id).
- Derive `FullTimeEmployee` and `PartTimeEmployee` classes for specific attributes.
- Accept and display details for both types of employees.


### Code

```cpp
#include <iostream>
using namespace std;

// [Employee Base Class]
class Employee {
protected:
    string name; int id;
public:
    void accept() { cout << "Name: "; cin >> name; cout << "ID: "; cin >> id; }
    void display() { cout << name << " " << id << endl; }
};

// [FullTimeEmployee Derived Class]
class FullTimeEmployee : public Employee {
    double salary;
public:
    void accept() { Employee::accept(); cout << "Salary: "; cin >> salary; }
    void display() { Employee::display(); cout << "FullTime Salary: " << salary << endl; }
};

// [PartTimeEmployee Derived Class]
class PartTimeEmployee : public Employee {
    double hourlyRate;
public:
    void accept() { Employee::accept(); cout << "Hourly Rate: "; cin >> hourlyRate; }
    void display() { Employee::display(); cout << "PartTime Rate: " << hourlyRate << endl; }
};

int main() {
    FullTimeEmployee f; PartTimeEmployee p;
    f.accept(); f.display();
    p.accept(); p.display();
    return 0;
}
```


### Explanation

- The base class `Employee` holds common data.
- `FullTimeEmployee` and `PartTimeEmployee` inherit from `Employee` and add their own fields.
- Each derived class calls the base class methods for shared data.


### Syntax Definitions

- **Inheritance**: Mechanism by which one class acquires the properties and behaviors of another class.
- **Method Overriding**: Redefining a base class method in a derived class.

---

# Slip 11:  


***

## Q1. Exception: Throw INVALID AGE

### Approach

- Check if the entered age is valid (between 0 and 100).
- If not, throw and handle an exception with a custom error message.


### Code

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

// [Age Validation Function]
void checkAge(int age) {
    if(age < 0 || age > 100) throw runtime_error("INVALID AGE");
}

int main() {
    int age;
    cout << "Enter age: ";
    cin >> age;
    try {
        checkAge(age);
        cout << "Valid age.\n";
    } catch(runtime_error &e) {
        cout << e.what() << endl;
    }
    return 0;
}
```


### Explanation

- The `checkAge` function throws a `runtime_error` if the age is not in the valid range.
- The exception is caught in `main` and the error message is displayed.


### Syntax Definitions

- **throw**: Used to signal the occurrence of an exception.
- **try-catch**: Used to handle exceptions and prevent program termination.
- **runtime_error**: A standard exception class for runtime errors.

***

## Q2. Temperature Converter with Static Functions

### Approach

- Create a class with static functions to convert between Celsius and Fahrenheit.
- Call these functions directly using the class name.


### Code

```cpp
#include <iostream>
using namespace std;

// [Temperature Converter Class]
class TConverter {
public:
    static double CtoF(double c) { return c*9/5 + 32; }
    static double FtoC(double f) { return (f-32)*5/9; }
};

int main() {
    double c, f;
    cout << "Celsius: "; cin >> c;
    cout << "Fahrenheit: " << TConverter::CtoF(c) << endl;
    cout << "Fahrenheit: "; cin >> f;
    cout << "Celsius: " << TConverter::FtoC(f) << endl;
    return 0;
}
```


### Explanation

- The `TConverter` class provides static methods for temperature conversion.
- Static methods are called using the class name, without creating an object.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.

***

## Q3. Online Retail Store Product Management (Case Study)

### Approach

- Define a `Product` class with id, name, price, category, and stock.
- Allow adding, updating, and retrieving products by category or price range.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Product Class Definition]
class Product {
    int id, stock;
    string name, category;
    double price;
public:
    void accept() {
        cout << "ID:"; cin >> id;
        cout << "Name:"; cin >> name;
        cout << "Category:"; cin >> category;
        cout << "Price:"; cin >> price;
        cout << "Stock:"; cin >> stock;
    }
    void update(double p, int s) { price = p; stock = s; }
    void display() { cout << id << " " << name << " " << category << " " << price << " " << stock << endl; }
    bool matchCategory(string cat) { return category == cat; }
    bool matchPrice(double lo, double hi) { return price >= lo && price <= hi; }
};

int main() {
    vector<Product> prods;
    for(int i = 0; i < 2; ++i) { Product p; p.accept(); prods.push_back(p); }
    cout << "Category search: "; string cat; cin >> cat;
    for(auto &p : prods) if(p.matchCategory(cat)) p.display();
    cout << "Update first product...\n"; prods[0].update(99.99, 100); prods[0].display();
    return 0;
}
```


### Explanation

- The `Product` class manages product details and provides methods for updating and searching.
- Products are stored in a vector, and can be filtered by category or price range.
- Demonstrates basic CRUD operations for a retail system.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **Method**: A function defined inside a class.

---

# Slip 12:  


***

## Q1. Swap Two Numbers Using Reference Variables

### Approach

- Define a function that takes two integer references as parameters.
- Swap their values inside the function using a temporary variable.
- Call the function from `main` and display the numbers before and after swapping.


### Code

```cpp
#include <iostream>
using namespace std;

// [Swap Function Definition]
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x, y;
    cout << "Enter two numbers: ";
    cin >> x >> y;
    cout << "Before swap: x=" << x << " y=" << y << endl;
    swap(x, y);
    cout << "After swap: x=" << x << " y=" << y << endl;
    return 0;
}
```


### Explanation

- The `swap` function uses reference parameters (`int &a, int &b`), so changes inside the function affect the original variables in `main`.
- A temporary variable is used to hold one value during the swap.
- The program demonstrates the effect by printing values before and after the swap.


### Syntax Definitions

- **Reference Parameter (`int &a`)**: Allows the function to modify the original variable passed from the caller.

***

## Q2. Customer Class: Accept/Display/Filter by Name Starting with 'P'

### Approach

- Create a `Customer` class with attributes: code, name, and population.
- Accept details for `n` customers and store them in a vector.
- Display details of customers whose names start with the letter 'P'.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Class Definition]
class Customer {
    int code, population;
    string name;
public:
    void accept() {
        cout << "Code: "; cin >> code;
        cout << "Name: "; cin >> name;
        cout << "Population: "; cin >> population;
    }
    void display() { cout << code << " " << name << " " << population << endl; }
    string getName() { return name; }
};

int main() {
    int n;
    cout << "Number of customers: ";
    cin >> n;
    vector<Customer> customers(n);
    for(auto &c : customers) c.accept();
    cout << "Customers with names starting with 'P':\n";
    for(auto &c : customers)
        if(!c.getName().empty() && c.getName()[0] == 'P')
            c.display();
    return 0;
}
```


### Explanation

- The `Customer` class encapsulates customer data and provides methods to accept and display it.
- The program reads `n` customers, then iterates through the list, displaying only those whose names start with 'P'.
- The check `!c.getName().empty()` ensures the name is not empty before accessing the first character.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library that can grow or shrink in size.

***

## Q3. Library Management System (Case Study)

### Approach

- Define a `Book` class with attributes: title, author, year, and ISBN.
- Accept details for multiple books and store them in a vector.
- Allow the user to search for a book by ISBN and display its details if found.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Book Class Definition]
class Book {
    string title, author, isbn;
    int year;
public:
    void accept() {
        cout << "Title: "; cin >> title;
        cout << "Author: "; cin >> author;
        cout << "Year: "; cin >> year;
        cout << "ISBN: "; cin >> isbn;
    }
    void display() {
        cout << title << " " << author << " " << year << " " << isbn << endl;
    }
    string getISBN() { return isbn; }
};

int main() {
    int n;
    cout << "Number of books: ";
    cin >> n;
    vector<Book> library(n);
    for(auto &b : library) b.accept();
    string searchISBN;
    cout << "Enter ISBN to search: ";
    cin >> searchISBN;
    bool found = false;
    for(auto &b : library) {
        if(b.getISBN() == searchISBN) {
            b.display();
            found = true;
        }
    }
    if(!found) cout << "Book not found." << endl;
    return 0;
}
```


### Explanation

- The `Book` class encapsulates book details and provides methods for input and output.
- The program reads `n` books, then searches for a book by ISBN and displays its details if found.
- The `found` flag ensures a message is shown if no book matches the search.


### Syntax Definitions

- **class**: Encapsulates data and functions for a specific concept (here, a book).
- **vector**: A resizable array from the C++ Standard Library.
- **Method**: A function defined inside a class.




---

# Slip 13:  


***

## Q1. Inline Function to Print Cube of a Number

### Approach

- Define an inline function that takes an integer and prints its cube.
- Call the function from `main` with user input.


### Code

```cpp
#include <iostream>
using namespace std;

// [Inline Function Definition]
inline void printCube(int n) {
    cout << "Cube: " << n*n*n << endl;
}

int main() {
    int x;
    cout << "Enter a number: ";
    cin >> x;
    printCube(x);
    return 0;
}
```


### Explanation

- The `printCube` function is marked `inline`, suggesting the compiler to expand it at the call site for efficiency.
- The function calculates the cube and prints it directly.
- User input is read in `main` and passed to the function.


### Syntax Definitions

- **inline**: A keyword that suggests the compiler to insert the function's code at each call site, potentially improving performance for small functions.

***

## Q2. Person Class: Accept/Display/Search by Contact Number

### Approach

- Create a `Person` class with attributes: name and contact number.
- Accept details for `n` persons and store them in a vector.
- Display all persons and search for a person by contact number.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Class Definition]
class Person {
    string name, contact;
public:
    void accept() {
        cout << "Enter name: "; cin >> name;
        cout << "Enter contact number: "; cin >> contact;
    }
    void display() { cout << name << " " << contact << endl; }
    string getContact() { return contact; }
};

int main() {
    int n;
    cout << "How many persons? ";
    cin >> n;
    vector<Person> people(n);
    for(auto &p : people) p.accept();
    cout << "All persons:\n";
    for(auto &p : people) p.display();
    string searchContact;
    cout << "Enter contact to search: "; cin >> searchContact;
    bool found = false;
    for(auto &p : people) {
        if(p.getContact() == searchContact) {
            p.display();
            found = true;
        }
    }
    if(!found) cout << "No record found.\n";
    return 0;
}
```


### Explanation

- The `Person` class encapsulates name and contact number, with methods to accept and display data.
- The program reads `n` persons, displays all, and then searches for a person by contact number.
- If a match is found, the details are displayed; otherwise, a message is shown.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library that can grow or shrink in size.

***

## Q3. Generic Data Management System (Template Case Study)

### Approach

- Use a template class to manage different types of data (e.g., students, faculty, courses).
- Demonstrate with a `Student` class and a template `DataManager` class.
- Add and display records generically.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Template Class Definition]
template <typename T>
class DataManager {
    vector<T> records;
public:
    void add(const T& rec) { records.push_back(rec); }
    void display() { for(const auto& r : records) r.display(); }
};

// [Student Class Definition]
class Student {
public:
    string name; int roll; double grade;
    void accept() { cout << "Name: "; cin >> name;
                    cout << "Roll: "; cin >> roll;
                    cout << "Grade: "; cin >> grade; }
    void display() { cout << name << " " << roll << " " << grade << endl; }
};

int main() {
    DataManager<Student> dm;
    int n; cout << "No. of students: "; cin >> n;
    for(int i=0; i<n; ++i) {
        Student s; s.accept(); dm.add(s);
    }
    cout << "All students:" << endl;
    dm.display();
    return 0;
}
```


### Explanation

- The `DataManager` template class can store and manage any type of record.
- Here, it is used with the `Student` class to add and display student records.
- The template allows for easy extension to other types (e.g., faculty, courses) by changing the type parameter.


### Syntax Definitions

- **template <typename T>**: Allows the creation of generic classes or functions that work with any data type.
- **vector**: A dynamic array from the C++ Standard Library.

***



***

Say "next" to continue with Slip 14 in this format!

---

# Slip 14:  


***

## Q1. Display First ‘n’ Numbers of Fibonacci Series

### Approach

- Use a loop to generate and print the first `n` terms of the Fibonacci sequence.
- Start with the first two terms (0 and 1), then compute each next term as the sum of the previous two.


### Code

```cpp
#include <iostream>
using namespace std;

// [Fibonacci Function Definition]
void fibonacci(int n) {
    int a = 0, b = 1;
    cout << a << " " << b << " ";
    for(int i = 2; i < n; ++i) {
        int next = a + b;
        cout << next << " ";
        a = b;
        b = next;
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Enter number of terms: ";
    cin >> n;
    fibonacci(n);
    return 0;
}
```


### Explanation

- The `fibonacci` function prints the first two terms, then uses a loop to calculate and print each subsequent term.
- Each new term is the sum of the previous two, and the variables are updated accordingly.
- The user specifies how many terms to print.


### Syntax Definitions

- **void**: Indicates the function does not return a value.
- **for loop**: Used to repeat a block of code a specific number of times.

***

## Q2. Student Class: Print Details of Students with Grade 'O'

### Approach

- Define a `Student` class with attributes: name, age, and grade.
- Accept details for `n` students and store them in a vector.
- Display details of students whose grade is 'O'.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    string name;
    int age;
    char grade;
public:
    // [Accept Input]
    void accept() {
        cout << "Name: "; cin >> name;
        cout << "Age: "; cin >> age;
        cout << "Grade (O/A/B/C/D): "; cin >> grade;
    }
    // [Display Function]
    void display() { cout << name << " " << age << " " << grade << endl; }
    char getGrade() { return grade; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    cout << "Students with grade O:\n";
    for(auto &s : students)
        if(s.getGrade() == 'O') s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then iterates through the list, displaying only those with grade 'O'.
- The `getGrade` method is used to check each student's grade.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.
- **auto**: Automatically deduces the type of the variable from its initializer.

***

## Q3. Math Utility Library (Static Functions Case Study)

### Approach

- Create a class with static functions for mathematical operations (factorial and prime check).
- Call these functions directly using the class name, without creating an object.


### Code

```cpp
#include <iostream>
using namespace std;

// [MathLib Class Definition]
class MathLib {
public:
    // [Static Factorial Function]
    static int factorial(int n) {
        int result = 1;
        for(int i = 1; i <= n; ++i) result *= i;
        return result;
    }
    // [Static Prime Check Function]
    static bool isPrime(int n) {
        if(n < 2) return false;
        for(int i = 2; i*i <= n; ++i)
            if(n % i == 0) return false;
        return true;
    }
};

int main() {
    int n;
    cout << "Enter number for factorial: "; cin >> n;
    cout << "Factorial: " << MathLib::factorial(n) << endl;
    cout << "Enter number for prime check: "; cin >> n;
    cout << (MathLib::isPrime(n) ? "Prime" : "Not Prime") << endl;
    return 0;
}
```


### Explanation

- The `MathLib` class provides static methods for factorial and prime checking.
- Static methods can be called using the class name without creating an object.
- The program demonstrates both functionalities with user input.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **bool**: A data type that can hold `true` or `false`.
- **?: (ternary operator)**: A shorthand for if-else to choose between two values.

---

# Slip 15:  


***

## Q1. Function Overloading: Find Maximum of Two and Three Numbers

### Approach

- Use function overloading to define two `max` functions: one for two arguments, one for three arguments.
- Each function returns the largest value among its parameters.
- Demonstrate both in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Max of Two]
int max(int a, int b) { return (a > b) ? a : b; }
// [Max of Three]
int max(int a, int b, int c) { return (a > b && a > c) ? a : (b > c ? b : c); }

int main() {
    cout << "Max of 5, 9: " << max(5, 9) << endl;
    cout << "Max of 3, 7, 2: " << max(3, 7, 2) << endl;
    return 0;
}
```


### Explanation

- Two `max` functions are defined: one for two integers, one for three.
- The compiler chooses the correct function based on the number of arguments.
- The ternary operator is used for concise comparison.


### Syntax Definitions

- **Function Overloading**: Defining multiple functions with the same name but different parameter lists.
- **Ternary Operator**: A shorthand for if-else: `(condition) ? value_if_true : value_if_false`.

***

## Q2. Student Class: Accept, Display, and Search by Roll Number

### Approach

- Create a `Student` class with attributes: roll number, name, and marks.
- Accept details for `n` students and store them in a vector.
- Search for a student by roll number and display their details.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    double marks;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Marks: "; cin >> marks;
    }
    void display() { cout << roll << " " << name << " " << marks << endl; }
    int getRoll() { return roll; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    int searchRoll;
    cout << "Enter roll to search: "; cin >> searchRoll;
    bool found = false;
    for(auto &s : students) {
        if(s.getRoll() == searchRoll) {
            s.display();
            found = true;
        }
    }
    if(!found) cout << "Student not found." << endl;
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then searches for a student by roll number and displays their details if found.
- The `getRoll` method is used for searching.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Account Management System (Static Count \& Dynamic Array Case Study)

### Approach

- Use a class `Account` with static members to count and sum balances.
- Store accounts in a dynamic array/vector.
- Accept, display, deposit, and withdraw with validation.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Account {
    static int totalAccounts;
    static double totalBalance;
    int accNum;
    double balance;
public:
    Account() { totalAccounts++; }
    void accept() {
        cout << "Acc No: "; cin >> accNum;
        cout << "Balance: "; cin >> balance;
        totalBalance += balance;
    }
    void display() { cout << accNum << " " << balance << endl; }
    void deposit(double amt) { balance += amt; totalBalance += amt; }
    void withdraw(double amt) {
        if(balance >= amt) { balance -= amt; totalBalance -= amt; }
        else cout << "Insufficient balance\n";
    }
    static void stats() {
        cout << "Total Accounts: " << totalAccounts << ", Total Balance: " << totalBalance << endl;
    }
};
int Account::totalAccounts = 0;
double Account::totalBalance = 0.0;

int main() {
    int n; cout << "Number of accounts: "; cin >> n;
    vector<Account> accs(n);
    for(auto &a : accs) a.accept();
    for(auto &a : accs) a.display();
    accs[0].deposit(500); accs[1].withdraw(100);
    Account::stats();
    return 0;
}
```


### Explanation

- Static members `totalAccounts` and `totalBalance` track the number of accounts and total balance.
- Methods allow for deposit, withdrawal, and displaying statistics.
- Demonstrates static data members and dynamic arrays.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **vector**: A dynamic array from the C++ Standard Library.
- **Dynamic Array**: An array whose size can change at runtime (here, implemented using `vector`).

---

# Slip 16:  


***

## Q1. Exception Handling: Validate Age, Income, City, Vehicle

### Approach

- Take user input for age, income, city, and vehicle type.
- Validate each input against specific constraints:
    - Age: 18–55
    - Income: 50,000–100,000
    - City: Pune, Mumbai, Bangalore, Chennai
    - Vehicle: Must be "4Wheeler"
- Throw and catch exceptions for each invalid input, displaying a specific error message.


### Code

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

// [Validation Function]
void validate(int age, double income, string city, string vehicle) {
    if(age < 18 || age > 55) throw runtime_error("AGE ERROR");
    if(income < 50000 || income > 100000) throw runtime_error("INCOME ERROR");
    if(city != "Pune" && city != "Mumbai" && city != "Bangalore" && city != "Chennai")
        throw runtime_error("CITY ERROR");
    if(vehicle != "4Wheeler") throw runtime_error("VEHICLE ERROR");
}

int main() {
    int age; double income; string city, vehicle;
    cout << "Age, income, city, vehicle: ";
    cin >> age >> income >> city >> vehicle;
    try {
        validate(age, income, city, vehicle);
        cout << "All constraints satisfied!\n";
    } catch(const runtime_error& e) {
        cout << "Exception: " << e.what() << endl;
    }
    return 0;
}
```


### Explanation

- The `validate` function checks each constraint and throws a `runtime_error` with a specific message if a rule is violated.
- The `main` function catches the exception and prints the error message.
- Demonstrates exception handling for multiple business rules.


### Syntax Definitions

- **throw**: Used to signal the occurrence of an exception.
- **try-catch**: Used to handle exceptions and prevent program termination.
- **runtime_error**: A standard exception class for runtime errors.

***

## Q2. Student Class: Accept, Display, and Search by Name

### Approach

- Create a `Student` class with attributes: roll number, name, and marks.
- Accept details for `n` students and store them in a vector.
- Search for a student by name and display their details.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    double marks;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Marks: "; cin >> marks;
    }
    void display() { cout << roll << " " << name << " " << marks << endl; }
    string getName() { return name; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string searchName;
    cout << "Enter name to search: "; cin >> searchName;
    bool found = false;
    for(auto &s : students) {
        if(s.getName() == searchName) {
            s.display();
            found = true;
        }
    }
    if(!found) cout << "Student not found." << endl;
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then searches for a student by name and displays their details if found.
- The `getName` method is used for searching.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Exception Handling with Multiple Constraints (Case Study)

### Approach

- Take user input for age, income, city, and vehicle.
- Validate all constraints; throw/catch exceptions showing specific messages for each condition.
- Demonstrate robust exception handling for business logic.


### Code

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

void validate(int age, double income, string city, string vehicle) {
    if(age < 18 || age > 55) throw runtime_error("AGE ERROR");
    if(income < 50000 || income > 100000) throw runtime_error("INCOME ERROR");
    if(city != "Pune" && city != "Mumbai" && city != "Bangalore" && city != "Chennai")
        throw runtime_error("CITY ERROR");
    if(vehicle != "4Wheeler") throw runtime_error("VEHICLE ERROR");
}

int main() {
    int age; double income; string city, vehicle;
    cout << "Enter age, income, city, vehicle: ";
    cin >> age >> income >> city >> vehicle;
    try {
        validate(age, income, city, vehicle);
        cout << "All constraints satisfied!\n";
    } catch(const runtime_error& e) {
        cout << "Exception: " << e.what() << endl;
    }
    return 0;
}
```


### Explanation

- The `validate` function checks each constraint and throws a `runtime_error` with a specific message if a rule is violated.
- The `main` function catches the exception and prints the error message.
- Demonstrates exception handling for multiple business rules.


### Syntax Definitions

- **throw**: Used to signal the occurrence of an exception.
- **try-catch**: Used to handle exceptions and prevent program termination.
- **runtime_error**: A standard exception class for runtime errors.

---

# Slip 17:  


***

## Q1. ATM Simulation: Deposit, Withdraw, Check Balance

### Approach

- Create an `ATM` class with a balance attribute.
- Implement methods for deposit, withdraw (with validation), and checking balance.
- Use a menu-driven approach in `main` to perform operations.


### Code

```cpp
#include <iostream>
using namespace std;

// [ATM Class Definition]
class ATM {
    double balance;
public:
    ATM(double b = 0) : balance(b) {}
    void deposit(double amt) { balance += amt; }
    void withdraw(double amt) {
        if(amt > balance) cout << "Insufficient funds\n";
        else balance -= amt;
    }
    void checkBalance() { cout << "Balance: " << balance << endl; }
};

int main() {
    ATM atm(1000);
    int choice; double amt;
    do {
        cout << "1.Deposit 2.Withdraw 3.Balance 0.Exit: ";
        cin >> choice;
        switch(choice) {
            case 1: cout << "Amount: "; cin >> amt; atm.deposit(amt); break;
            case 2: cout << "Amount: "; cin >> amt; atm.withdraw(amt); break;
            case 3: atm.checkBalance(); break;
        }
    } while(choice != 0);
    return 0;
}
```


### Explanation

- The `ATM` class manages the account balance and provides methods for deposit, withdrawal (with validation), and balance inquiry.
- The menu-driven loop in `main` allows the user to perform operations until exit.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **switch-case**: A control structure for multi-way branching.
- **do-while loop**: Executes the loop body at least once, then repeats as long as the condition is true.

***

## Q2. Student Class: Accept, Display, and Search by Marks

### Approach

- Create a `Student` class with attributes: roll number, name, and marks.
- Accept details for `n` students and store them in a vector.
- Search for students with marks above a given threshold and display their details.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    double marks;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Marks: "; cin >> marks;
    }
    void display() { cout << roll << " " << name << " " << marks << endl; }
    double getMarks() { return marks; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    double threshold;
    cout << "Enter marks threshold: "; cin >> threshold;
    cout << "Students with marks above threshold:\n";
    for(auto &s : students)
        if(s.getMarks() > threshold) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those with marks above the specified threshold.
- The `getMarks` method is used for filtering.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **auto**: Automatically deduces the type of the variable from its initializer.

***

## Q3. ATM Simulation System (Case Study)

### Approach

- Implement ATM class with deposit, withdraw, and balance methods.
- Validate each operation for errors and demonstrate object usage in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

class ATM {
    double balance;
public:
    ATM(double b = 0) : balance(b) {}
    void deposit(double amt) { balance += amt; }
    void withdraw(double amt) {
        if(amt > balance) cout << "Insufficient funds\n";
        else balance -= amt;
    }
    void checkBalance() { cout << "Balance: " << balance << endl; }
};

int main() {
    ATM atm(1000);
    atm.deposit(500);
    atm.withdraw(200);
    atm.checkBalance();
    return 0;
}
```


### Explanation

- The `ATM` class manages the account balance and provides methods for deposit, withdrawal (with validation), and balance inquiry.
- The program demonstrates object usage and method calls for typical ATM operations.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **Constructor with default argument**: Allows object creation with or without an initial balance.

---

# Slip 18:  


***

## Q1. Shopping Cart System: Add Product, Check Stock, Compute Bill

### Approach

- Define a `Product` class with attributes: name, price, and stock.
- Accept details for multiple products and store them in a vector.
- Allow the user to add products to a cart, check stock, and compute the total bill.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Product Class Definition]
class Product {
    string name;
    double price;
    int stock;
public:
    void accept() { cin >> name >> price >> stock; }
    bool available(int qty) { return stock >= qty; }
    double bill(int qty) { return price * qty; }
    void updateStock(int qty) { stock -= qty; }
    void display() { cout << name << " " << price << " " << stock << endl; }
};

int main() {
    int n; cin >> n;
    vector<Product> prods(n);
    for(auto &p : prods) p.accept();
    string query; int qty;
    cin >> query >> qty;
    for(auto &p : prods)
        if(p.available(qty)) {
            cout << "Bill: " << p.bill(qty) << endl;
            p.updateStock(qty); break;
        }
}
```


### Explanation

- The `Product` class manages product details and provides methods for checking stock, computing bill, and updating inventory.
- The program accepts product details, then processes a purchase by checking stock and updating it if the sale is successful.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **Method**: A function defined inside a class.

***

## Q2. Student Class: Accept, Display, and Search by Name Starting with 'A'

### Approach

- Create a `Student` class with attributes: roll number, name, and marks.
- Accept details for `n` students and store them in a vector.
- Display details of students whose names start with 'A'.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    double marks;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Marks: "; cin >> marks;
    }
    void display() { cout << roll << " " << name << " " << marks << endl; }
    string getName() { return name; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    cout << "Students with names starting with 'A':\n";
    for(auto &s : students)
        if(!s.getName().empty() && s.getName()[0] == 'A')
            s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then iterates through the list, displaying only those whose names start with 'A'.
- The check `!s.getName().empty()` ensures the name is not empty before accessing the first character.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Shopping Cart System (Case Study)

### Approach

- Use a class `Product` for each product (name, price, stock).
- Let user add products to a cart, check stock \& compute total bill.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Product {
    string name;
    double price;
    int stock;
public:
    void accept() { cin >> name >> price >> stock; }
    bool available(int qty) { return stock >= qty; }
    double bill(int qty) { return price * qty; }
    void updateStock(int qty) { stock -= qty; }
    void display() { cout << name << " " << price << " " << stock << endl; }
};

int main() {
    int n; cin >> n;
    vector<Product> prods(n);
    for(auto &p : prods) p.accept();
    string query; int qty;
    cin >> query >> qty;
    for(auto &p : prods)
        if(p.available(qty)) {
            cout << "Bill: " << p.bill(qty) << endl;
            p.updateStock(qty); break;
        }
}
```


### Explanation

- Checks for stock, reports bill, decrements inventory after sale.
- Demonstrates basic shopping cart logic for a retail system.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **Method**: A function defined inside a class.

---

# Slip 19:  


***

## Q1. Login and Registration System

### Approach

- Define a `User` class with attributes for username and password.
- Implement methods for registration (accepting credentials) and login (verifying credentials).
- Demonstrate registration and login in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [User Class Definition]
class User {
    string uname, pwd;
public:
    void reg() { cin >> uname >> pwd; }
    bool login(string u, string p) { return uname==u && pwd==p; }
};

int main() {
    User u; u.reg();
    string u1, p1; cin >> u1 >> p1;
    if(u.login(u1, p1)) cout << "Success\n"; else cout << "Fail\n";
    return 0;
}
```


### Explanation

- The `User` class manages user credentials and provides methods for registration and login.
- The `login` method checks if the entered username and password match the stored credentials.
- Demonstrates basic authentication logic.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **Method**: A function defined inside a class.

***

## Q2. Student Class: Accept, Display, and Search by Marks Above 75

### Approach

- Create a `Student` class with attributes: roll number, name, and marks.
- Accept details for `n` students and store them in a vector.
- Display details of students whose marks are above 75.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    double marks;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Marks: "; cin >> marks;
    }
    void display() { cout << roll << " " << name << " " << marks << endl; }
    double getMarks() { return marks; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    cout << "Students with marks above 75:\n";
    for(auto &s : students)
        if(s.getMarks() > 75) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those with marks above 75.
- The `getMarks` method is used for filtering.


### Syntax Definitions

- **vector**: A dynamic array from the C++ Standard Library.
- **auto**: Automatically deduces the type of the variable from its initializer.

***

## Q3. Login and Registration System (Case Study)

### Approach

- Class for user with username/password; methods for registration \& login.
- Demonstrate registration and login in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

class User {
    string uname, pwd;
public:
    void reg() { cin >> uname >> pwd; }
    bool login(string u, string p) { return uname==u && pwd==p; }
};

int main() {
    User u; u.reg();
    string u1, p1; cin >> u1 >> p1;
    if(u.login(u1, p1)) cout << "Success\n"; else cout << "Fail\n";
    return 0;
}
```


### Explanation

- Register and login; mimics minimal credential system.
- The `login` method checks if the entered username and password match the stored credentials.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **Method**: A function defined inside a class.

---

# Slip 20:  


***

## Q1. School Hierarchy System (Multi-level Inheritance)

### Approach

- Define a base class `Person` with common attributes (name, age).
- Derive a `Teacher` class from `Person` that adds subject information.
- Derive an `Admin` class from `Teacher` that adds duty information.
- Each class provides its own `accept` method to input relevant data.


### Code

```cpp
#include <iostream>
using namespace std;

// [Base Class: Person]
class Person {
protected: string name; int age;
public: void accept(){ cin>>name>>age; }
};
// [Derived Class: Teacher]
class Teacher: public Person {
    string subj;
public: void accept(){ Person::accept(); cin>>subj; }
};
// [Further Derived: Admin]
class Admin: public Teacher {
    string duty;
public: void accept(){ Teacher::accept(); cin>>duty; }
};

int main() {
    Admin a; a.accept();
    return 0;
}
```


### Explanation

- `Person` is the base class for name and age.
- `Teacher` inherits from `Person` and adds subject.
- `Admin` inherits from `Teacher` and adds duty.
- Each class's `accept` method calls its parent to handle inherited data.


### Syntax Definitions

- **protected**: Members are accessible in the class and its derived classes.
- **public inheritance**: Derived class inherits all public and protected members of the base class.

***

## Q2. Student Class: Accept, Display, and Search by Subject

### Approach

- Create a `Student` class with attributes: roll number, name, and subject.
- Accept details for `n` students and store them in a vector.
- Search for students by subject and display their details.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name, subject;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Subject: "; cin >> subject;
    }
    void display() { cout << roll << " " << name << " " << subject << endl; }
    string getSubject() { return subject; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string searchSubject;
    cout << "Enter subject to search: "; cin >> searchSubject;
    bool found = false;
    for(auto &s : students) {
        if(s.getSubject() == searchSubject) {
            s.display();
            found = true;
        }
    }
    if(!found) cout << "Student not found." << endl;
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then searches for students by subject and displays their details if found.
- The `getSubject` method is used for searching.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. School Hierarchy System (Multi-level Inheritance Case Study)

### Approach

- Use base class `Person`, derived class `Teacher`, and further derived class `Admin` to model a school hierarchy.
- Each class adds its own specific data and calls parent methods for inherited data.
- Demonstrate object creation and data input in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

class Person {
protected: string name; int age;
public: void accept(){ cin>>name>>age; }
};
class Teacher: public Person {
    string subj;
public: void accept(){ Person::accept(); cin>>subj; }
};
class Admin: public Teacher {
    string duty;
public: void accept(){ Teacher::accept(); cin>>duty; }
};

int main() {
    Admin a; a.accept();
    return 0;
}
```


### Explanation

- Shows inheritance chain, each class accepts its own plus parent fields.
- Demonstrates multi-level inheritance for a school system.


### Syntax Definitions

- **Inheritance**: Mechanism by which one class acquires the properties and behaviors of another class.
- **Method Overriding**: Redefining a base class method in a derived class.




---

# Slip 21:  


***

## Q1. Generic Data Management System (Template-based Record System)

### Approach

- Use a template class to add and display any kind of record.
- Demonstrate with Student data; easily extensible to Faculty or Course records.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Template Class Definition]
template <typename T>
class DataManager {
    vector<T> data;
public:
    void add(T rec) { data.push_back(rec); }
    void display() { for(auto &r : data) r.display(); }
};

// [Student Class Definition]
class Student {
public:
    string name; int roll; double grade;
    void accept() { cin >> name >> roll >> grade; }
    void display() { cout << name << " " << roll << " " << grade << endl; }
};

int main() {
    DataManager<Student> dm;
    int n; cin >> n;
    for(int i=0;i<n;++i){ Student s; s.accept(); dm.add(s); }
    dm.display();
    return 0;
}
```


### Explanation

- Template class supports flexible record management with a generic interface.
- Here, it is used for Student records, but can be extended to other types.
- The `add` method stores records, and `display` prints all records.


### Syntax Definitions

- **template <typename T>**: Allows the class to work with any data type specified at instantiation.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q2. Student Class: Accept, Display, and Search by Grade

### Approach

- Create a `Student` class with attributes: roll number, name, and grade.
- Accept details for `n` students and store them in a vector.
- Display details of students with a specific grade (e.g., 'A').


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    char grade;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Grade: "; cin >> grade;
    }
    void display() { cout << roll << " " << name << " " << grade << endl; }
    char getGrade() { return grade; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    char searchGrade;
    cout << "Enter grade to search: "; cin >> searchGrade;
    cout << "Students with grade " << searchGrade << ":\n";
    for(auto &s : students)
        if(s.getGrade() == searchGrade) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those with the specified grade.
- The `getGrade` method is used for filtering.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Generic Data Management System (Template Case Study)

### Approach

- Use a template class to manage different types of data (e.g., students, faculty, courses).
- Demonstrate with a `Student` class and a template `DataManager` class.
- Add and display records generically.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Template Class Definition]
template <typename T>
class DataManager {
    vector<T> records;
public:
    void add(const T& rec) { records.push_back(rec); }
    void display() { for(const auto& r : records) r.display(); }
};

// [Student Class Definition]
class Student {
public:
    string name; int roll; double grade;
    void accept() { cin >> name >> roll >> grade; }
    void display() { cout << name << " " << roll << " " << grade << endl; }
};

int main() {
    DataManager<Student> dm;
    int n; cin >> n;
    for(int i=0; i<n; ++i) {
        Student s; s.accept(); dm.add(s);
    }
    dm.display();
    return 0;
}
```


### Explanation

- The `DataManager` template class can store and manage any type of record.
- Here, it is used with the `Student` class to add and display student records.
- The template allows for easy extension to other types (e.g., faculty, courses) by changing the type parameter.


### Syntax Definitions

- **template <typename T>**: Allows the creation of generic classes or functions that work with any data type.
- **vector**: A dynamic array from the C++ Standard Library.

***

---

# Slip 22:  


***

## Q1. Vehicle Management System with Inheritance

### Approach

- Use a base class `Vehicle` with common attributes and methods.
- Derive a `Car` class from `Vehicle` that adds car-specific features (model, doors, maker).
- Demonstrate inheritance and method calls in `main`.


### Code

```cpp
#include <iostream>
using namespace std;
// [Base Class: Vehicle]
class Vehicle {
protected:
    int speed, passengers;
    string fuel;
public:
    void go(){ cout << "Vehicle going.\n"; }
    void stop(){ cout << "Vehicle stopped.\n"; }
    void changeDirection(){ cout << "Direction changed.\n"; }
};
// [Derived Class: Car]
class Car : public Vehicle {
    string model; int doors; string maker;
public:
    void radio(){ cout << "Radio ON.\n"; }
    void ac(){ cout << "AC ON.\n"; }
    void wiper(){ cout << "Wiper ON.\n"; }
};

int main() {
    Car c;
    c.go(); c.radio(); c.ac(); c.stop();
    return 0;
}
```


### Explanation

- The `Car` class inherits all methods and data from `Vehicle`, and adds car-specific features.
- Demonstrates calling both inherited and new methods.


### Syntax Definitions

- **protected**: Members are accessible in the class and its derived classes.
- **public inheritance**: Derived class inherits all public and protected members of the base class.

***

## Q2. Student Class: Accept, Display, and Search by Fuel Type

### Approach

- Create a `Student` class with attributes: roll number, name, and fuel type.
- Accept details for `n` students and store them in a vector.
- Display details of students with a specific fuel type (e.g., "Petrol").


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;
// [Student Class Definition]
class Student {
    int roll;
    string name, fuelType;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Fuel Type: "; cin >> fuelType;
    }
    void display() { cout << roll << " " << name << " " << fuelType << endl; }
    string getFuelType() { return fuelType; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string searchFuel;
    cout << "Enter fuel type to search: "; cin >> searchFuel;
    cout << "Students with fuel type " << searchFuel << ":\n";
    for(auto &s : students)
        if(s.getFuelType() == searchFuel) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those with the specified fuel type.
- The `getFuelType` method is used for filtering.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Vehicle Management System with Inheritance (Case Study)

### Approach

- Use base class `Vehicle`; derived class `Car` adds car-specific features.
- Demonstrate inheritance and method calls in `main`.


### Code

```cpp
#include <iostream>
using namespace std;
class Vehicle {
protected:
    int speed, passengers;
    string fuel;
public:
    void go(){ cout << "Vehicle going.\n"; }
    void stop(){ cout << "Vehicle stopped.\n"; }
    void changeDirection(){ cout << "Direction changed.\n"; }
};
class Car : public Vehicle {
    string model; int doors; string maker;
public:
    void radio(){ cout << "Radio ON.\n"; }
    void ac(){ cout << "AC ON.\n"; }
    void wiper(){ cout << "Wiper ON.\n"; }
};

int main() {
    Car c;
    c.go(); c.radio(); c.ac(); c.stop();
    return 0;
}
```


### Explanation

- Inherits all methods and data from Vehicle, adds Car-specific features.
- Demonstrates inheritance and method calls for a vehicle management system.


### Syntax Definitions

- **Inheritance**: Mechanism by which one class acquires the properties and behaviors of another class.
- **Method Overriding**: Redefining a base class method in a derived class.


---

# Slip 23:  


***

## Q1. Account/Bank Management (with Static Member and Dynamic Array)

### Approach

- Store accounts with static count and total balance.
- Use a vector to store multiple accounts.
- Accept, display, deposit, and withdraw with validation.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Account {
    static int accCount;
    static double totalBalance;
    int accNo; double balance;
public:
    Account() { accCount++; }
    void accept() { cin >> accNo >> balance; totalBalance += balance; }
    void display() { cout << accNo << " " << balance << endl; }
    void deposit(double amt) { balance += amt; totalBalance += amt; }
    void withdraw(double amt) {
        if(balance >= amt) { balance -= amt; totalBalance -= amt; }
        else cout << "Insufficient balance\n";
    }
    static void showStats() { cout << accCount << " " << totalBalance << endl; }
};
int Account::accCount = 0;
double Account::totalBalance = 0.0;

int main() {
    int n; cin >> n;
    vector<Account> ac(n); for(auto &a:ac) a.accept();
    for(auto &a:ac) a.display();
    ac[0].deposit(500); ac[1].withdraw(100);
    Account::showStats();
    return 0;
}
```


### Explanation

- Static variables track total number and overall balances.
- Methods allow for deposit, withdrawal, and displaying statistics.
- Demonstrates static data members and dynamic arrays.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **vector**: A dynamic array from the C++ Standard Library.
- **Dynamic Array**: An array whose size can change at runtime (here, implemented using `vector`).

***

## Q2. Student Class: Accept, Display, and Search by Account Number

### Approach

- Create a `Student` class with attributes: roll number, name, and account number.
- Accept details for `n` students and store them in a vector.
- Search for a student by account number and display their details.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

// [Student Class Definition]
class Student {
    int roll;
    string name;
    int accNo;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Account No: "; cin >> accNo;
    }
    void display() { cout << roll << " " << name << " " << accNo << endl; }
    int getAccNo() { return accNo; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    int searchAccNo;
    cout << "Enter account number to search: "; cin >> searchAccNo;
    bool found = false;
    for(auto &s : students) {
        if(s.getAccNo() == searchAccNo) {
            s.display();
            found = true;
        }
    }
    if(!found) cout << "Student not found." << endl;
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then searches for a student by account number and displays their details if found.
- The `getAccNo` method is used for searching.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Account/Bank Management (with Static Member and Dynamic Array Case Study)

### Approach

- Store accounts with static count and total balance.
- Use vector, input and show all accounts.
- Demonstrate deposit and withdrawal operations.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Account {
    static int accCount;
    static double totalBalance;
    int accNo; double balance;
public:
    Account() { accCount++; }
    void accept() { cin >> accNo >> balance; totalBalance += balance; }
    void display() { cout << accNo << " " << balance << endl; }
    void deposit(double amt) { balance += amt; totalBalance += amt; }
    void withdraw(double amt) {
        if(balance >= amt) { balance -= amt; totalBalance -= amt; }
        else cout << "Insufficient balance\n";
    }
    static void showStats() { cout << accCount << " " << totalBalance << endl; }
};
int Account::accCount = 0;
double Account::totalBalance = 0.0;

int main() {
    int n; cin >> n;
    vector<Account> ac(n); for(auto &a:ac) a.accept();
    for(auto &a:ac) a.display();
    ac[0].deposit(500); ac[1].withdraw(100);
    Account::showStats();
    return 0;
}
```


### Explanation

- Static variables track total number and overall balances.
- Methods allow for deposit, withdrawal, and displaying statistics.
- Demonstrates static data members and dynamic arrays.


### Syntax Definitions

- **static**: Declares a member function or variable that belongs to the class, not to any object.
- **vector**: A dynamic array from the C++ Standard Library.
- **Dynamic Array**: An array whose size can change at runtime (here, implemented using `vector`).

---

# Slip 24: 


***

## Q1. Employee Payroll System (Inheritance: FullTime, PartTime)

### Approach

- Use a base class `Employee` for common data (name, id).
- Two derived classes: `FullTimeEmployee` and `PartTimeEmployee`, each with their specifics.
- Accept and display details for both types of employees.


### Code

```cpp
#include <iostream>
using namespace std;

// [Employee Base Class]
class Employee {
protected:
    string name; int id;
public:
    void accept() { cout << "Name: "; cin >> name; cout << "ID: "; cin >> id; }
    void display() { cout << name << " " << id << endl; }
};

// [FullTimeEmployee Derived Class]
class FullTimeEmployee : public Employee {
    double salary;
public:
    void accept() { Employee::accept(); cout << "Salary: "; cin >> salary; }
    void display() { Employee::display(); cout << "FullTime Salary: " << salary << endl; }
};

// [PartTimeEmployee Derived Class]
class PartTimeEmployee : public Employee {
    double rate;
public:
    void accept() { Employee::accept(); cout << "Hourly Rate: "; cin >> rate; }
    void display() { Employee::display(); cout << "PartTime Rate: " << rate << endl; }
};

int main() {
    FullTimeEmployee f; PartTimeEmployee p;
    f.accept(); p.accept();
    f.display(); p.display();
    return 0;
}
```


### Explanation

- Each derived class adds its own data but calls base class function for common attributes.
- Demonstrates inheritance and method overriding for payroll management.


### Syntax Definitions

- **Inheritance**: Mechanism by which one class acquires the properties and behaviors of another class.
- **Method Overriding**: Redefining a base class method in a derived class.

***

## Q2. Student Class: Accept, Display, and Search by Employee Type

### Approach

- Create a `Student` class with attributes: roll number, name, and employee type (e.g., "FullTime" or "PartTime").
- Accept details for `n` students and store them in a vector.
- Display details of students with a specific employee type.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;
// [Student Class Definition]
class Student {
    int roll;
    string name, empType;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Employee Type: "; cin >> empType;
    }
    void display() { cout << roll << " " << name << " " << empType << endl; }
    string getEmpType() { return empType; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string searchType;
    cout << "Enter employee type to search: "; cin >> searchType;
    cout << "Students with employee type " << searchType << ":\n";
    for(auto &s : students)
        if(s.getEmpType() == searchType) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those with the specified employee type.
- The `getEmpType` method is used for filtering.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Employee Payroll System (Inheritance Case Study)

### Approach

- Use a base class `Employee` for common data (name, id).
- Derive `FullTimeEmployee` and `PartTimeEmployee` classes for specific attributes.
- Accept and display details for both types of employees.


### Code

```cpp
#include <iostream>
using namespace std;

class Employee {
protected:
    string name; int id;
public:
    void accept() { cout << "Name: "; cin >> name; cout << "ID: "; cin >> id; }
    void display() { cout << name << " " << id << endl; }
};
class FullTimeEmployee : public Employee {
    double salary;
public:
    void accept() { Employee::accept(); cout << "Salary: "; cin >> salary; }
    void display() { Employee::display(); cout << "FullTime Salary: " << salary << endl; }
};
class PartTimeEmployee : public Employee {
    double rate;
public:
    void accept() { Employee::accept(); cout << "Hourly Rate: "; cin >> rate; }
    void display() { Employee::display(); cout << "PartTime Rate: " << rate << endl; }
};

int main() {
    FullTimeEmployee f; PartTimeEmployee p;
    f.accept(); p.accept();
    f.display(); p.display();
    return 0;
}
```


### Explanation

- Each derived class adds its own data but calls base class function for common attributes.
- Demonstrates inheritance and method overriding for payroll management.


### Syntax Definitions

- **Inheritance**: Mechanism by which one class acquires the properties and behaviors of another class.
- **Method Overriding**: Redefining a base class method in a derived class.

---

# Slip 25: 

***

## Q1. Function Overloading: Calculate Area of Square and Rectangle

### Approach

- Use function overloading to define two `area` functions: one for a square (one argument), one for a rectangle (two arguments).
- Each function returns the area using the appropriate formula.
- Demonstrate both in `main`.


### Code

```cpp
#include <iostream>
using namespace std;

// [Area of Square]
int area(int side) { return side * side; }
// [Area of Rectangle]
int area(int l, int b) { return l * b; }

int main() {
    cout << "Area of square (4): " << area(4) << endl;
    cout << "Area of rectangle (4,6): " << area(4,6) << endl;
    return 0;
}
```


### Explanation

- Two `area` functions are defined: one takes one argument (square), one takes two (rectangle).
- The compiler chooses the correct function based on the number of arguments.
- Demonstrates function overloading for different shapes.


### Syntax Definitions

- **Function Overloading**: Defining multiple functions with the same name but different parameter lists.

***

## Q2. Student Class: Accept, Display, and Search by Area (for Hostel Allocation)

### Approach

- Create a `Student` class with attributes: roll number, name, and area (e.g., "North", "South").
- Accept details for `n` students and store them in a vector.
- Display details of students from a specific area.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;
// [Student Class Definition]
class Student {
    int roll;
    string name, area;
public:
    void accept() {
        cout << "Roll: "; cin >> roll;
        cout << "Name: "; cin >> name;
        cout << "Area: "; cin >> area;
    }
    void display() { cout << roll << " " << name << " " << area << endl; }
    string getArea() { return area; }
};

int main() {
    int n;
    cout << "Number of students: ";
    cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string searchArea;
    cout << "Enter area to search: "; cin >> searchArea;
    cout << "Students from area " << searchArea << ":\n";
    for(auto &s : students)
        if(s.getArea() == searchArea) s.display();
    return 0;
}
```


### Explanation

- The `Student` class encapsulates student data and provides methods to accept and display it.
- The program reads `n` students, then displays those from the specified area.
- The `getArea` method is used for filtering.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

***

## Q3. Hostel Allocation System (Case Study)

### Approach

- Use a `Student` class with roll, name, and area.
- Accept, display, and search for students by area for hostel allocation.
- Demonstrate object usage and filtering in `main`.


### Code

```cpp
#include <iostream>
#include <vector>
using namespace std;
class Student {
    int roll;
    string name, area;
public:
    void accept() { cin >> roll >> name >> area; }
    void display() { cout << roll << " " << name << " " << area << endl; }
    string getArea() { return area; }
};

int main() {
    int n; cin >> n;
    vector<Student> students(n);
    for(auto &s : students) s.accept();
    string area; cin >> area;
    for(auto &s : students)
        if(s.getArea() == area) s.display();
    return 0;
}
```


### Explanation

- Accepts and displays students, filters by area for hostel allocation.
- Demonstrates object usage and filtering for a real-world scenario.


### Syntax Definitions

- **class**: A user-defined type that groups data and functions.
- **vector**: A dynamic array from the C++ Standard Library.

