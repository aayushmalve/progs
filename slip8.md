# Slip 8

## JAVA

### Q1 (A). Write a Java program to accept an age. Throw a user-defined InvalidAgeException if the age is below 18 years.

**Slip Solution**

```java
import java.util.Scanner;

class InvalidAgeException extends Exception {
    InvalidAgeException() { super("Age must be 18 or above"); }
}

class AgeCheck {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int age=sc.nextInt();
        try {
            if(age<18) throw new InvalidAgeException();
            System.out.println("Eligible");
        } catch(InvalidAgeException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

**Run:** `javac AgeCheck.java && java AgeCheck`

### Q1 (B). Write a Java program to display files having the extension .txt from a given directory.

**Slip Solution**

```java
import java.io.File;
import java.util.Scanner;

class TextFiles {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        File dir=new File(sc.nextLine());
        File[] files=dir.listFiles((d,name)->name.toLowerCase().endsWith(".txt"));
        if(files==null) System.out.println("Invalid directory");
        else for(File f:files) System.out.println(f.getName());
    }
}
```

**Run:** `javac TextFiles.java && java TextFiles`

## PYTHON

### Q2 (A). Write a Python script to find the repeated items of a tuple.

**Slip Solution**

```python
t=(1,2,3,2,4,1,5)
for x in dict.fromkeys(t):
    if t.count(x)>1: print(x)
```

**Run:** `python slip8_q2a.py`

### Q2 (B). Create test.txt containing integers, characters, and float numbers. Read the file and print an appropriate message using exception handling.

**Slip Solution**

```python
with open("test.txt","w") as f:
    f.write("10\nA\n3.14\nhello\n")

with open("test.txt") as f:
    for line in f:
        x=line.strip()
        try:
            print("Integer:",int(x))
        except ValueError:
            try:
                print("Float:",float(x))
            except ValueError:
                if len(x)==1: print("Character:",x)
                else: print("String:",x)
```

The program creates the requested test.txt file, then reads and classifies its contents.

**Run:** `python slip8_q2b.py`

