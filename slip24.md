# Slip 24

## JAVA

### Q1 (A). Write a Java program to count the number of digits, spaces, and characters from a file.

**Slip Solution**

```java
import java.io.FileReader;

class FileCount {
    public static void main(String[] args) throws Exception {
        FileReader f=new FileReader("input.txt");
        int c,letters=0,digits=0,spaces=0;
        while((c=f.read())!=-1) {
            if(Character.isLetter(c)) letters++;
            if(Character.isDigit(c)) digits++;
            if(c==' ') spaces++;
        }
        f.close();
        System.out.println("Characters: "+letters);
        System.out.println("Digits: "+digits);
        System.out.println("Spaces: "+spaces);
    }
}
```

Create `input.txt` in the same folder. Characters reports the total number of file characters, including spaces and digits.

**Run:** `javac FileCount.java && java FileCount`

### Q1 (B). Create a class Account having synchronized deposit() and withdraw() methods. Show that bank transactions can be carried out concurrently using synchronization.

**Slip Solution**

```java
class Account {
    int balance=1000;
    synchronized void deposit(int amount) {
        balance+=amount;
        System.out.println("Deposit "+amount+", Balance "+balance);
    }
    synchronized void withdraw(int amount) {
        if(balance>=amount) {
            balance-=amount;
            System.out.println("Withdraw "+amount+", Balance "+balance);
        } else System.out.println("Insufficient balance");
    }
}

class BankSync {
    public static void main(String[] args) {
        Account a=new Account();
        Thread t1=new Thread(()->{ for(int i=0;i<3;i++) a.deposit(500); });
        Thread t2=new Thread(()->{ for(int i=0;i<3;i++) a.withdraw(300); });
        t1.start(); t2.start();
    }
}
```

**Run:** `javac BankSync.java && java BankSync`

## PYTHON

### Q2 (A). Write a Python program to check whether a given number is prime and find its factorial using user-defined functions.

**Slip Solution**

```python
def is_prime(n):
    return n>1 and all(n%i for i in range(2,int(n**0.5)+1))

def factorial(n):
    f=1
    for i in range(1,n+1): f*=i
    return f

n=int(input("Enter number: "))
print("Prime" if is_prime(n) else "Not Prime")
if n<0: print("Factorial is not defined for negative numbers")
else: print("Factorial:",factorial(n))
```

**Run:** `python slip24_q2a.py`

### Q2 (B). Customer Feedback Analysis: Generate ratings of 50 customers using NumPy. Calculate mean, median, standard deviation, rating frequency, and create a bar chart.

**Slip Solution**

```python
import numpy as np
import matplotlib.pyplot as plt

ratings=np.random.randint(1,6,50)
print("Ratings:",ratings)
print("Mean:",np.mean(ratings))
print("Median:",np.median(ratings))
print("Standard deviation:",np.std(ratings))
values,counts=np.unique(ratings,return_counts=True)
for v,c in zip(values,counts): print(v,":",c)
plt.bar(values,counts)
plt.xlabel("Rating")
plt.ylabel("Frequency")
plt.show()
```

**Run:** `pip install numpy matplotlib; python slip24_q2b.py`

