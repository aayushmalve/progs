# Slip 19

## JAVA

### Q1 (A). Write a Java program to display Fibonacci series using a function.

**Slip Solution**

```java
import java.util.Scanner;

class Fibonacci {
    static void show(int n) {
        int a=0,b=1;
        for(int i=0;i<n;i++) { System.out.print(a+" "); int c=a+b; a=b; b=c; }
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        show(sc.nextInt());
    }
}
```

**Run:** `javac Fibonacci.java && java Fibonacci`

### Q1 (B). Create a class Account having synchronized deposit() and withdraw() methods. Show that bank transactions can be carried out concurrently using synchronization.

**Slip Solution**

```java
class Account {
    int balance=1000;
    synchronized void deposit(int amount) {
        balance+=amount;
        System.out.println("Deposited: "+amount+" Balance: "+balance);
    }
    synchronized void withdraw(int amount) {
        if(balance>=amount) {
            balance-=amount;
            System.out.println("Withdrawn: "+amount+" Balance: "+balance);
        } else System.out.println("Insufficient balance");
    }
}

class Bank {
    public static void main(String[] args) {
        Account a=new Account();
        Thread t1=new Thread(()->{ for(int i=0;i<3;i++) a.deposit(500); });
        Thread t2=new Thread(()->{ for(int i=0;i<3;i++) a.withdraw(300); });
        t1.start(); t2.start();
    }
}
```

**Run:** `javac Bank.java && java Bank`

## PYTHON

### Q2 (A). Write a Python program to accept a number and display its multiplication table on button click.

**Slip Solution**

```python
import tkinter as tk

root=tk.Tk()
root.title("Multiplication Table")
entry=tk.Entry(root)
entry.pack()
result=tk.Label(root)
result.pack()

def show():
    n=int(entry.get())
    result.config(text="\n".join(f"{n} x {i} = {n*i}" for i in range(1,11)))

tk.Button(root,text="Show Table",command=show).pack()
root.mainloop()
```

Tkinter is included with most standard Python desktop installations.

**Run:** `python slip19_q2a.py`

### Q2 (B). Write a Python script using a package to calculate area and perimeter of a circle.

**Slip Solution**

```python
import math

r=float(input("Radius: "))
print("Area:",math.pi*r*r)
print("Perimeter:",2*math.pi*r)
```

**Run:** `python slip19_q2b.py`

