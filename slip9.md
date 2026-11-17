# Slip 9

## JAVA

### Q1 (A). Accept marks of 5 subjects, calculate total and percentage, and display the grade: >=75 Distinction, >=60 First Class, >=50 Second Class, >=40 Pass, otherwise Fail.

**Slip Solution**

```java
import java.util.Scanner;

class Grade {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int total=0;
        for(int i=1;i<=5;i++) total+=sc.nextInt();
        double per=total/5.0;
        System.out.println("Total: "+total);
        System.out.println("Percentage: "+per);
        if(per>=75) System.out.println("Distinction");
        else if(per>=60) System.out.println("First Class");
        else if(per>=50) System.out.println("Second Class");
        else if(per>=40) System.out.println("Pass");
        else System.out.println("Fail");
    }
}
```

**Run:** `javac Grade.java && java Grade`

### Q1 (B). Write a Java program to validate PAN number and Mobile Number. If invalid, throw a user-defined Invalid Data exception; otherwise display them.

**Slip Solution**

```java
import java.util.Scanner;

class InvalidDataException extends Exception {
    InvalidDataException() { super("Invalid Data"); }
}

class ValidateData {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String pan=sc.nextLine().toUpperCase();
        String mobile=sc.nextLine();
        try {
            if(!pan.matches("[A-Z]{5}[0-9]{4}[A-Z]") || !mobile.matches("[6-9][0-9]{9}"))
                throw new InvalidDataException();
            System.out.println("PAN: "+pan);
            System.out.println("Mobile: "+mobile);
        } catch(InvalidDataException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

**Run:** `javac ValidateData.java && java ValidateData`

## PYTHON

### Q2 (A). Write a Python script to reverse a string word by word.

**Slip Solution**

```python
s=input("Enter a sentence: ")
print(" ".join(word[::-1] for word in s.split()))
```

This reverses each word while keeping the word order.

**Run:** `python slip9_q2a.py`

### Q2 (B). Write a Python program to accept a number n and check whether it is Prime, Perfect, or Armstrong.

**Slip Solution**

```python
def prime(n):
    return n>1 and all(n%i for i in range(2,int(n**0.5)+1))

def perfect(n):
    return n>0 and sum(i for i in range(1,n) if n%i==0)==n

def armstrong(n):
    return n>=0 and sum(int(d)**len(str(n)) for d in str(n))==n

n=int(input("Enter number: "))
print("Prime" if prime(n) else "Not Prime")
print("Perfect" if perfect(n) else "Not Perfect")
print("Armstrong" if armstrong(n) else "Not Armstrong")
```

**Run:** `python slip9_q2b.py`

