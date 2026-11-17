# Slip 4

## JAVA

### Q1 (A). Write a Java program to display alternate characters from a given string.

**Slip Solution**

```java
import java.util.Scanner;

class Alternate {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String s=sc.nextLine();
        for(int i=0;i<s.length();i+=2) System.out.print(s.charAt(i));
    }
}
```

**Run:** `javac Alternate.java && java Alternate`

### Q1 (B). Write a Java program to accept an integer from the user and check whether it is Positive, Negative, or Zero.

**Slip Solution**

```java
import java.util.Scanner;

class NumberCheck {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        if(n>0) System.out.println("Positive");
        else if(n<0) System.out.println("Negative");
        else System.out.println("Zero");
    }
}
```

**Run:** `javac NumberCheck.java && java NumberCheck`

## PYTHON

### Q2 (A). Write a Python program to create a background with changing colors using Flask.

**Slip Solution**

```python
from flask import Flask
import random

app=Flask(__name__)
colors=["red","green","blue","yellow","pink","orange"]

@app.route("/")
def home():
    color=random.choice(colors)
    return f'<body style="background-color:{color}"><h2>Background Color: {color}</h2><a href="/">Change Color</a></body>'

app.run()
```

Refresh or click Change Color to get another background color.

**Run:** `pip install flask; python slip4_q2a.py`

### Q2 (B). Write a program which accepts an integer value n and displays Fibonacci terms till n.

**Slip Solution**

```python
n=int(input("Enter limit: "))
a,b=0,1
while a<=n:
    print(a,end=" ")
    a,b=b,a+b
```

Here n is the maximum Fibonacci value, as stated by “terms till n”.

**Run:** `python slip4_q2b.py`

