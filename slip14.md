# Slip 14

## JAVA

### Q1 (A). Write a Java program to calculate power of a number using recursion.

**Slip Solution**

```java
import java.util.Scanner;

class Power {
    static long power(int a,int n) {
        if(n==0) return 1;
        return a*power(a,n-1);
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int a=sc.nextInt(),n=sc.nextInt();
        if(n<0) System.out.println("Exponent must be non-negative");
        else System.out.println(power(a,n));
    }
}
```

**Run:** `javac Power.java && java Power`

### Q1 (B). Write a Java program to accept employee details (Eno, EName, Sal) and display them on the next frame using an appropriate event.

**Slip Solution**

```java
import javax.swing.*;
import java.awt.*;

class EmployeeForm {
    public static void main(String[] args) {
        JFrame f=new JFrame("Employee Details");
        JTextField eno=new JTextField(),name=new JTextField(),sal=new JTextField();
        JButton b=new JButton("Submit");
        f.setLayout(new GridLayout(4,2,5,5));
        f.add(new JLabel("Employee No:")); f.add(eno);
        f.add(new JLabel("Employee Name:")); f.add(name);
        f.add(new JLabel("Salary:")); f.add(sal);
        f.add(new JLabel()); f.add(b);
        b.addActionListener(e->{
            JFrame next=new JFrame("Employee Information");
            next.add(new JLabel("Eno: "+eno.getText()+"   Name: "+name.getText()+"   Salary: "+sal.getText()));
            next.setSize(450,100); next.setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE); next.setVisible(true);
        });
        f.setSize(350,200); f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); f.setVisible(true);
    }
}
```

**Run:** `javac EmployeeForm.java && java EmployeeForm`

## PYTHON

### Q2 (A). Write a Python program to accept dimensions of a cylinder and display its surface area and volume.

**Slip Solution**

```python
import math

r=float(input("Radius: "))
h=float(input("Height: "))
print("Surface area:",2*math.pi*r*(r+h))
print("Volume:",math.pi*r*r*h)
```

**Run:** `python slip14_q2a.py`

### Q2 (B). Write a Python program to display plain text and cipher text using Caesar encryption.

**Slip Solution**

```python
text=input("Plain text: ")
shift=int(input("Shift: "))
result=""
for c in text:
    if c.isupper(): result+=chr((ord(c)-65+shift)%26+65)
    elif c.islower(): result+=chr((ord(c)-97+shift)%26+97)
    else: result+=c
print("Plain text:",text)
print("Cipher text:",result)
```

**Run:** `python slip14_q2b.py`

