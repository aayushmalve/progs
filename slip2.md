# Slip 2

## JAVA

### Q1 (A). Write a Java program to display all the vowels from a given string.

**Slip Solution**

```java
import java.util.Scanner;

class Vowels {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String s=sc.nextLine();
        for(char c:s.toCharArray())
            if("aeiouAEIOU".indexOf(c)>=0) System.out.print(c+" ");
    }
}
```

**Run:** `javac Vowels.java && java Vowels`

### Q1 (B). Write a Java program that accepts two numbers and an operator (+, -, *, /, %) through command-line arguments and performs the specified arithmetic operation.

**Slip Solution**

```java
class Arithmetic {
    public static void main(String[] args) {
        if(args.length!=3) {
            System.out.println("Usage: java Arithmetic number1 number2 operator");
            return;
        }
        double a=Double.parseDouble(args[0]),b=Double.parseDouble(args[1]);
        switch(args[2]) {
            case "+": System.out.println(a+b); break;
            case "-": System.out.println(a-b); break;
            case "*": System.out.println(a*b); break;
            case "/":
                if(b==0) System.out.println("Division by zero");
                else System.out.println(a/b);
                break;
            case "%":
                if(b==0) System.out.println("Division by zero");
                else System.out.println(a%b);
                break;
            default: System.out.println("Invalid operator");
        }
    }
}
```

The argument order is number1, number2, operator.

**Run:** `javac Arithmetic.java && java Arithmetic 10 5 '*'`

## PYTHON

### Q2 (A). Write a Python function that accepts a string and calculates the number of uppercase and lowercase letters. Sample: The quick Brown Fox.

**Slip Solution**

```python
def count_case(s):
    upper=sum(c.isupper() for c in s)
    lower=sum(c.islower() for c in s)
    print("No. of Upper case characters:",upper)
    print("No. of Lower case characters:",lower)

count_case("The quick Brown Fox")
```

Expected output: 3 uppercase and 13 lowercase characters.

**Run:** `python slip2_q2a.py`

### Q2 (B). Write a Flask program to create a Student Registration form (Name, Email, Course, Year), store submitted data in an SQLite table named registrations, and display all registered students in an HTML table.

**Slip Solution**

```python
from flask import Flask,request,render_template_string,redirect
import sqlite3

app=Flask(__name__)

def connect():
    return sqlite3.connect("students.db")

with connect() as db:
    db.execute("CREATE TABLE IF NOT EXISTS registrations(name TEXT,email TEXT,course TEXT,year TEXT)")

@app.route("/",methods=["GET","POST"])
def home():
    if request.method=="POST":
        with connect() as db:
            db.execute("INSERT INTO registrations VALUES(?,?,?,?)",(request.form["name"],request.form["email"],request.form["course"],request.form["year"]))
        return redirect("/")
    with connect() as db:
        rows=db.execute("SELECT * FROM registrations").fetchall()
    return render_template_string("""
    <form method="post">
    <input name="name" placeholder="Name" required>
    <input name="email" type="email" placeholder="Email" required>
    <input name="course" placeholder="Course" required>
    <input name="year" placeholder="Year" required>
    <button>Register</button></form>
    <table border="1"><tr><th>Name</th><th>Email</th><th>Course</th><th>Year</th></tr>
    {% for r in rows %}<tr>{% for v in r %}<td>{{v}}</td>{% endfor %}</tr>{% endfor %}</table>
    """,rows=rows)

app.run(debug=True)
```

Open `http://127.0.0.1:5000` in a browser.

**Run:** `pip install flask; python slip2_q2b.py`

