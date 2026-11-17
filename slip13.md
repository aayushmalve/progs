# Slip 13

## JAVA

### Q1 (A). Write a Java program to accept n integers, store them in an ArrayList, and display the elements in reverse order.

**Slip Solution**

```java
import java.util.*;

class ReverseList {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        ArrayList<Integer> a=new ArrayList<>();
        for(int i=0;i<n;i++) a.add(sc.nextInt());
        for(int i=a.size()-1;i>=0;i--) System.out.print(a.get(i)+" ");
    }
}
```

**Run:** `javac ReverseList.java && java ReverseList`

### Q1 (B). Write a Java program that asks the user name and greets the user in uppercase. Example: Hello, RAJ, nice to meet you!

**Slip Solution**

```java
import java.util.Scanner;

class Greeting {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String name=sc.nextLine().toUpperCase();
        System.out.println("Hello, "+name+", nice to meet you!");
    }
}
```

**Run:** `javac Greeting.java && java Greeting`

## PYTHON

### Q2 (A). Write a Python program to input a positive integer and display a correct message for correct and incorrect input using exception handling.

**Slip Solution**

```python
try:
    n=int(input("Enter a positive integer: "))
    if n<=0: raise ValueError
    print("Valid positive integer:",n)
except ValueError:
    print("Invalid input. Enter a positive integer.")
```

**Run:** `python slip13_q2a.py`

### Q2 (B). Write a Python program to accept a string and remove the characters which have even index values using a user-defined function.

**Slip Solution**

```python
def remove_even(s):
    return s[1::2]

s=input("Enter string: ")
print(remove_even(s))
```

Characters at indexes 0, 2, 4, ... are removed.

**Run:** `python slip13_q2b.py`

