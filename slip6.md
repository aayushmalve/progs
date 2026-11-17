# Slip 6

## JAVA

### Q1 (A). Write a Java program to count the number of even and odd elements in an integer array.

**Slip Solution**

```java
import java.util.Scanner;

class EvenOdd {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.print("Array size: ");
        int n=sc.nextInt(),even=0,odd=0;
        int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        for(int x:a) if(x%2==0) even++; else odd++;
        System.out.println("Even: "+even);
        System.out.println("Odd: "+odd);
    }
}
```

**Run:** `javac EvenOdd.java && java EvenOdd`

### Q1 (B). Write a Java program to accept a filename from the user and display whether the file exists or not.

**Slip Solution**

```java
import java.io.File;
import java.util.Scanner;

class FileCheck {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        File f=new File(sc.nextLine());
        System.out.println(f.exists()?"File exists":"File does not exist");
    }
}
```

**Run:** `javac FileCheck.java && java FileCheck`

## PYTHON

### Q2 (A). Write a Python script using a package to calculate the area and volume of a cube and sphere.

**Slip Solution**

```python
import math

a=float(input("Cube side: "))
r=float(input("Sphere radius: "))
print("Cube area:",6*a*a)
print("Cube volume:",a**3)
print("Sphere area:",4*math.pi*r*r)
print("Sphere volume:",4*math.pi*r**3/3)
```

**Run:** `python slip6_q2a.py`

### Q2 (B). Generate ratings for 100 customers using random numbers. Calculate mean, median, standard deviation, rating frequency, satisfaction percentage, and create a bar chart.

**Slip Solution**

```python
import random
import statistics
import matplotlib.pyplot as plt

ratings=[random.randint(1,5) for _ in range(100)]
print("Mean:",statistics.mean(ratings))
print("Median:",statistics.median(ratings))
print("Standard deviation:",statistics.stdev(ratings))
for r in range(1,6): print(r,":",ratings.count(r))
satisfied=sum(x>=4 for x in ratings)
print("Satisfaction percentage:",satisfied/len(ratings)*100)
plt.bar(range(1,6),[ratings.count(r) for r in range(1,6)])
plt.xlabel("Rating")
plt.ylabel("Frequency")
plt.show()
```

Satisfaction is calculated as ratings of 4 or 5 out of 5.

**Run:** `pip install matplotlib; python slip6_q2b.py`

