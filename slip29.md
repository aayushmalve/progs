# Slip 29

## JAVA

### Q1 (A). Write a Java program to check whether a candidate is eligible for voting or not. Handle user-defined as well as system-defined exceptions.

**Slip Solution**

```java
import java.util.Scanner;

class InvalidAgeException extends Exception {
    InvalidAgeException() { super("Age cannot be negative"); }
}

class Voting {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        try {
            System.out.print("Enter age: ");
            int age=Integer.parseInt(sc.nextLine());
            if(age<0) throw new InvalidAgeException();
            System.out.println(age>=18?"Eligible for voting":"Not eligible for voting");
        } catch(NumberFormatException e) {
            System.out.println("Invalid age input");
        } catch(InvalidAgeException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

NumberFormatException is the system-defined exception; InvalidAgeException is user-defined.

**Run:** `javac Voting.java && java Voting`

### Q1 (B). Write a Java program to read a file and classify characters as uppercase letters, lowercase letters, digits, whitespace characters, and special symbols.

**Slip Solution**

```java
import java.io.FileReader;

class ClassifyFile {
    public static void main(String[] args) throws Exception {
        FileReader f=new FileReader("input.txt");
        int c,upper=0,lower=0,digit=0,space=0,special=0;
        while((c=f.read())!=-1) {
            if(Character.isUpperCase(c)) upper++;
            else if(Character.isLowerCase(c)) lower++;
            else if(Character.isDigit(c)) digit++;
            else if(Character.isWhitespace(c)) space++;
            else special++;
        }
        f.close();
        System.out.println("Uppercase: "+upper);
        System.out.println("Lowercase: "+lower);
        System.out.println("Digits: "+digit);
        System.out.println("Whitespace: "+space);
        System.out.println("Special symbols: "+special);
    }
}
```

Create `input.txt` in the same folder as the program.

**Run:** `javac ClassifyFile.java && java ClassifyFile`

## PYTHON

### Q2 (A). Write a Python program to calculate the volume of a sphere by accepting radius as input.

**Slip Solution**

```python
import math

r=float(input("Radius: "))
print("Volume:",4*math.pi*r**3/3)
```

**Run:** `python slip29_q2a.py`

### Q2 (B). Student Marks Analysis: Create a NumPy array containing marks of 15 students. Display total students, average marks, highest and lowest marks, students scoring above average, and top 3 scores.

**Slip Solution**

```python
import numpy as np

marks=np.array([78,85,60,92,55,88,70,95,66,81,73,90,59,84,76])
avg=np.mean(marks)
print("Total students:",len(marks))
print("Average marks:",avg)
print("Highest marks:",np.max(marks))
print("Lowest marks:",np.min(marks))
print("Above average:",marks[marks>avg])
print("Top 3 scores:",np.sort(marks)[-3:][::-1])
```

**Run:** `pip install numpy; python slip29_q2b.py`

