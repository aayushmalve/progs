# Slip 3

## JAVA

### Q1 (A). Write a Java program to check whether a given number is Armstrong or not. Use static keyword.

**Slip Solution**

```java
import java.util.Scanner;

class Armstrong {
    static boolean check(int n) {
        if(n<0) return false;
        int t=n,sum=0,digits=String.valueOf(n).length();
        while(t>0) {
            int d=t%10;
            sum+= (int)Math.pow(d,digits);
            t/=10;
        }
        return sum==n;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        System.out.println(check(n)?"Armstrong":"Not Armstrong");
    }
}
```

**Run:** `javac Armstrong.java && java Armstrong`

### Q1 (B). Write a Java program to find the largest of three numbers entered by the user using nested if-else statements.

**Slip Solution**

```java
import java.util.Scanner;

class Largest {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int a=sc.nextInt(),b=sc.nextInt(),c=sc.nextInt();
        if(a>=b) {
            if(a>=c) System.out.println(a);
            else System.out.println(c);
        } else {
            if(b>=c) System.out.println(b);
            else System.out.println(c);
        }
    }
}
```

**Run:** `javac Largest.java && java Largest`

## PYTHON

### Q2 (A). Write a Python program to check if a given key already exists in a dictionary. If the key exists, replace it with another key/value pair.

**Slip Solution**

```python
d={"name":"Aayush","age":20}
old=input("Key to replace: ")
if old in d:
    new=input("New key: ")
    value=input("New value: ")
    del d[old]
    d[new]=value
print(d)
```

**Run:** `python slip3_q2a.py`

### Q2 (B). Write a program which accepts an integer value n and displays all prime numbers till n.

**Slip Solution**

```python
n=int(input("Enter n: "))
for x in range(2,n+1):
    prime=True
    for i in range(2,int(x**0.5)+1):
        if x%i==0:
            prime=False
            break
    if prime: print(x,end=" ")
```

**Run:** `python slip3_q2b.py`

