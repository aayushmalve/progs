# Slip 16

## JAVA

### Q1 (A). Write a Java program to calculate sum of digits of a given number using recursion.

**Slip Solution**

```java
import java.util.Scanner;

class DigitSum {
    static int sum(int n) {
        if(n==0) return 0;
        return n%10+sum(n/10);
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=Math.abs(sc.nextInt());
        System.out.println("Sum: "+sum(n));
    }
}
```

**Run:** `javac DigitSum.java && java DigitSum`

### Q1 (B). Accept n employee names, sort them in ascending order, and display them using an array of objects and the static keyword.

**Slip Solution**

```java
import java.util.Scanner;

class Employee {
    String name;
    Employee(String name) { this.name=name; }
    static void sort(Employee[] e) {
        for(int i=0;i<e.length-1;i++)
            for(int j=0;j<e.length-i-1;j++)
                if(e[j].name.compareToIgnoreCase(e[j+1].name)>0) {
                    Employee t=e[j]; e[j]=e[j+1]; e[j+1]=t;
                }
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        sc.nextLine();
        Employee[] e=new Employee[n];
        for(int i=0;i<n;i++) e[i]=new Employee(sc.nextLine());
        sort(e);
        for(Employee x:e) System.out.println(x.name);
    }
}
```

**Run:** `javac Employee.java && java Employee`

## PYTHON

### Q2 (A). Write a Flask program that passes a number to a template to display Pass if the number is 40 or more, otherwise Fail.

**Slip Solution**

```python
from flask import Flask,request,render_template_string

app=Flask(__name__)

@app.route("/",methods=["GET","POST"])
def home():
    result=None
    if request.method=="POST":
        n=int(request.form["number"])
        result="Pass" if n>=40 else "Fail"
    return render_template_string('<form method="post"><input type="number" name="number" required><button>Check</button></form>{% if result %}<h3>{{result}}</h3>{% endif %}',result=result)

app.run()
```

**Run:** `pip install flask; python slip16_q2a.py`

Open `http://127.0.0.1:5000` in a browser.

### Q2 (B). Write a Python script using a user-defined package to calculate area and volume of a cylinder and cuboids.

**Slip Solution**

Create the following package files.

**File: `shapes/__init__.py`**

```python
import math

def cylinder(r,h):
    return 2*math.pi*r*(r+h),math.pi*r*r*h

def cuboid(l,b,h):
    return 2*(l*b+b*h+h*l),l*b*h
```

**File: `main.py`**

```python
import shapes

r=float(input("Cylinder radius: "))
h=float(input("Cylinder height: "))
print("Cylinder area and volume:",shapes.cylinder(r,h))
l=float(input("Cuboid length: "))
b=float(input("Cuboid breadth: "))
h=float(input("Cuboid height: "))
print("Cuboid area and volume:",shapes.cuboid(l,b,h))
```

**Run:** `python main.py`
