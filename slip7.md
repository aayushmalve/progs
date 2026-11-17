# Slip 7

## JAVA

### Q1 (A). Write a Java program to accept a number. If negative, throw a user-defined NegativeNumberException; otherwise display its square.

**Slip Solution**

```java
import java.util.Scanner;

class NegativeNumberException extends Exception {
    NegativeNumberException() { super("Negative number"); }
}

class Square {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        try {
            if(n<0) throw new NegativeNumberException();
            System.out.println("Square: "+(n*n));
        } catch(NegativeNumberException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

**Run:** `javac Square.java && java Square`

### Q1 (B). Accept n cricket players (pid, pname, totalRuns, InningsPlayed, NotOuttimes), calculate averages, and display details of the player with maximum average using an array of objects.

**Slip Solution**

```java
import java.util.Scanner;

class Player {
    int pid,runs,innings,notOut;
    String name;
    Player(int p,String n,int r,int i,int no) {
        pid=p; name=n; runs=r; innings=i; notOut=no;
    }
    double average() {
        return innings==notOut?0:(double)runs/(innings-notOut);
    }
}

class Cricket {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        Player[] p=new Player[n];
        for(int i=0;i<n;i++) {
            int id=sc.nextInt();
            String name=sc.next();
            int runs=sc.nextInt(),innings=sc.nextInt(),notOut=sc.nextInt();
            p[i]=new Player(id,name,runs,innings,notOut);
        }
        Player best=p[0];
        for(Player x:p) if(x.average()>best.average()) best=x;
        System.out.println("PID: "+best.pid);
        System.out.println("Name: "+best.name);
        System.out.println("Runs: "+best.runs);
        System.out.println("Average: "+best.average());
    }
}
```

**Run:** `javac Cricket.java && java Cricket`

## PYTHON

### Q2 (A). Write a Python script to display datetime in various formats: current date and time, month of year, week number, day of year, and day of month.

**Slip Solution**

```python
from datetime import datetime

d=datetime.now()
print("Current date and time:",d)
print("Month:",d.strftime("%B"))
print("Week number:",d.strftime("%U"))
print("Day of year:",d.strftime("%j"))
print("Day of month:",d.strftime("%d"))
```

**Run:** `python slip7_q2a.py`

### Q2 (B). Write a Python program to generate a random password with uppercase and lowercase letters.

**Slip Solution**

```python
import random
import string

chars=string.ascii_letters
password="".join(random.choice(chars) for _ in range(10))
print("Password:",password)
```

**Run:** `python slip7_q2b.py`

