# Slip 11

## JAVA

### Q1 (A). Write a menu-driven Java program using command-line arguments for addition, subtraction, multiplication, and division.

**Slip Solution**

```java
class Menu {
    public static void main(String[] args) {
        if(args.length!=3) {
            System.out.println("Usage: java Menu choice number1 number2");
            return;
        }
        int choice=Integer.parseInt(args[0]);
        double a=Double.parseDouble(args[1]),b=Double.parseDouble(args[2]);
        switch(choice) {
            case 1: System.out.println(a+b); break;
            case 2: System.out.println(a-b); break;
            case 3: System.out.println(a*b); break;
            case 4:
                if(b==0) System.out.println("Division by zero");
                else System.out.println(a/b);
                break;
            default: System.out.println("Invalid choice");
        }
    }
}
```

**Run:** `javac Menu.java && java Menu 1 10 5`

### Q1 (B). Write a Java program to read a file and count the number of vowels present in it.

**Slip Solution**

```java
import java.io.FileReader;
import java.util.Scanner;

class CountVowels {
    public static void main(String[] args) throws Exception {
        Scanner sc=new Scanner(System.in);
        FileReader f=new FileReader(sc.nextLine());
        int c,count=0;
        while((c=f.read())!=-1)
            if("aeiouAEIOU".indexOf(c)>=0) count++;
        f.close();
        System.out.println("Vowels: "+count);
    }
}
```

**Run:** `javac CountVowels.java && java CountVowels`

## PYTHON

### Q2 (A). Write a Python program to compute the element-wise sum of tuples (1,2,3,4), (3,5,2,1), and (2,2,3,1).

**Slip Solution**

```python
a=(1,2,3,4)
b=(3,5,2,1)
c=(2,2,3,1)
print(tuple(x+y+z for x,y,z in zip(a,b,c)))
```

**Run:** `python slip11_q2a.py`

### Q2 (B). Write a Python program to find repeated items of a tuple and check whether an element exists within a tuple.

**Slip Solution**

```python
t=(1,2,3,2,4,1,5)
for x in dict.fromkeys(t):
    if t.count(x)>1: print("Repeated:",x)

n=int(input("Search element: "))
print("Exists" if n in t else "Not found")
```

**Run:** `python slip11_q2b.py`

