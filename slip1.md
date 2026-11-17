# Slip 1

## JAVA

### Q1 (A). Write a Java program to display characters from A to Z.

**Slip Solution**

```java
class Alphabet {
    public static void main(String[] args) {
        for(char c='A';c<='Z';c++) System.out.print(c+" ");
    }
}
```

**Run:** `javac Alphabet.java && java Alphabet`

### Q1 (B). Write a Java program to copy only non-numeric data from one file to another file.

**Slip Solution**

```java
import java.io.*;
import java.util.Scanner;

class CopyNonNumeric {
    public static void main(String[] args) throws IOException {
        Scanner sc=new Scanner(System.in);
        System.out.print("Source file: ");
        String src=sc.nextLine();
        System.out.print("Destination file: ");
        String dest=sc.nextLine();
        try(FileReader r=new FileReader(src); FileWriter w=new FileWriter(dest)) {
            int c;
            while((c=r.read())!=-1)
                if(!Character.isDigit(c)) w.write(c);
        }
        System.out.println("File copied.");
    }
}
```

The program copies every character except numeric digits. Use different source and destination filenames.

**Run:** `javac CopyNonNumeric.java && java CopyNonNumeric`

## PYTHON

### Q2 (A). Write a Python program to accept n numbers in a list and remove duplicates from the list.

**Slip Solution**

```python
n=int(input("How many numbers? "))
a=[int(input()) for _ in range(n)]
print("List without duplicates:",list(dict.fromkeys(a)))
```

**Run:** `python slip1_q2a.py`

### Q2 (B). Write a Python program to accept your birthdate and output your age.

**Slip Solution**

```python
from datetime import date,datetime

dob=datetime.strptime(input("Birthdate (DD-MM-YYYY): "),"%d-%m-%Y").date()
today=date.today()
age=today.year-dob.year-((today.month,today.day)<(dob.month,dob.day))
print("Age:",age)
```

**Run:** `python slip1_q2b.py`

