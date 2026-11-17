# Slip 25

## JAVA

### Q1 (A). Write a Java program to check whether a given string is palindrome or not.

**Slip Solution**

```java
import java.util.Scanner;

class StringPalindrome {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String s=sc.nextLine();
        String r=new StringBuilder(s).reverse().toString();
        System.out.println(s.equalsIgnoreCase(r)?"Palindrome":"Not Palindrome");
    }
}
```

**Run:** `javac StringPalindrome.java && java StringPalindrome`

### Q1 (B). Create a package named Series with two classes to print the square series and Fibonacci series. Write a Java program to generate n terms of both series.

**Slip Solution**

Create the following three files.

**File: `Series/SquareSeries.java`**

```java
package Series;

public class SquareSeries {
    public void print(int n) {
        for(int i=1;i<=n;i++) System.out.print(i*i+" ");
    }
}
```

**File: `Series/FibonacciSeries.java`**

```java
package Series;

public class FibonacciSeries {
    public void print(int n) {
        int a=0,b=1;
        for(int i=0;i<n;i++) { System.out.print(a+" "); int c=a+b; a=b; b=c; }
    }
}
```

**File: `Main.java`**

```java
import Series.SquareSeries;
import Series.FibonacciSeries;
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        System.out.print("Squares: ");
        new SquareSeries().print(n);
        System.out.print("\nFibonacci: ");
        new FibonacciSeries().print(n);
    }
}
```

**Run:** `javac Series/*.java Main.java && java Main`

## PYTHON

### Q2 (A). Write a Python function that accepts a string and calculates the number of uppercase and lowercase letters. Sample: The quick Brow Fox.

**Slip Solution**

```python
def count_case(s):
    print("No. of Upper case characters:",sum(c.isupper() for c in s))
    print("No. of Lower case characters:",sum(c.islower() for c in s))

count_case("The quick Brow Fox")
```

Expected output: 3 uppercase and 12 lowercase characters.

**Run:** `python slip25_q2a.py`

### Q2 (B). Create a DataFrame with missing values and duplicate records. Identify missing values, replace them, detect and remove duplicates, and display the cleaned dataset.

**Slip Solution**

```python
import pandas as pd

df=pd.DataFrame({"Name":["A","B","B","C"],"Marks":[80,None,None,90]})
print("Missing values:\n",df.isnull().sum())
df["Marks"]=df["Marks"].fillna(df["Marks"].mean())
print("Duplicate rows:\n",df[df.duplicated()])
df=df.drop_duplicates()
print("Cleaned data:\n",df)
```

**Run:** `pip install pandas; python slip25_q2b.py`

