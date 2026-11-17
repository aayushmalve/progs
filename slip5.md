# Slip 5

## JAVA

### Q1 (A). Write a Java program to display the following pattern: 5 / 45 / 345 / 2345 / 12345.

**Slip Solution**

```java
class Pattern {
    public static void main(String[] args) {
        for(int i=5;i>=1;i--) {
            for(int j=i;j<=5;j++) System.out.print(j);
            System.out.println();
        }
    }
}
```

**Run:** `javac Pattern.java && java Pattern`

### Q1 (B). Write a Java program to accept two 3x3 matrices, perform matrix addition, and display the resultant matrix.

**Slip Solution**

```java
import java.util.Scanner;

class MatrixAdd {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int[][] a=new int[3][3];
        int[][] b=new int[3][3];
        System.out.println("Enter first matrix:");
        for(int i=0;i<3;i++) for(int j=0;j<3;j++) a[i][j]=sc.nextInt();
        System.out.println("Enter second matrix:");
        for(int i=0;i<3;i++) for(int j=0;j<3;j++) b[i][j]=sc.nextInt();
        System.out.println("Sum:");
        for(int i=0;i<3;i++) {
            for(int j=0;j<3;j++) System.out.print((a[i][j]+b[i][j])+" ");
            System.out.println();
        }
    }
}
```

**Run:** `javac MatrixAdd.java && java MatrixAdd`

## PYTHON

### Q2 (A). Write a Python script using a package to calculate the area and perimeter of a circle.

**Slip Solution**

```python
import math

r=float(input("Enter radius: "))
print("Area:",math.pi*r*r)
print("Perimeter:",2*math.pi*r)
```

**Run:** `python slip5_q2a.py`

### Q2 (B). Write a Python script to generate Fibonacci terms using a generator function.

**Slip Solution**

```python
def fibonacci(n):
    a,b=0,1
    for _ in range(n):
        yield a
        a,b=b,a+b

n=int(input("Enter number of terms: "))
print(*fibonacci(n))
```

**Run:** `python slip5_q2b.py`

