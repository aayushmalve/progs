# Slip 20

## JAVA

### Q1 (A). Write a Java program using AWT to create a Frame with title TYBBACA and red background. Close the frame when the user clicks the close button.

**Slip Solution**

```java
import java.awt.*;
import java.awt.event.*;

class RedFrame {
    public static void main(String[] args) {
        Frame f=new Frame("TYBBACA");
        f.setSize(400,300);
        f.setBackground(Color.RED);
        f.addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) { f.dispose(); }
        });
        f.setVisible(true);
    }
}
```

**Run:** `javac RedFrame.java && java RedFrame`

### Q1 (B). Write a TCP/IP client-server program in which the client sends two strings and the server responds with their concatenation.

**Slip Solution**

**File: `Server.java`**

```java
import java.net.*;
import java.io.*;

class Server {
    public static void main(String[] args) throws Exception {
        ServerSocket ss=new ServerSocket(5000);
        Socket s=ss.accept();
        DataInputStream in=new DataInputStream(s.getInputStream());
        DataOutputStream out=new DataOutputStream(s.getOutputStream());
        String a=in.readUTF(),b=in.readUTF();
        out.writeUTF(a+b);
        s.close(); ss.close();
    }
}
```

Save the code as `Server.java`. Start the server first. Then run the client below in another terminal.

**Run:** `javac Server.java; java Server`

### Q1 (B) - Client. Client program for the TCP/IP string-concatenation task.

**Slip Solution**

**File: `Client.java`**

```java
import java.net.*;
import java.io.*;
import java.util.Scanner;

class Client {
    public static void main(String[] args) throws Exception {
        Scanner sc=new Scanner(System.in);
        Socket s=new Socket("localhost",5000);
        DataOutputStream out=new DataOutputStream(s.getOutputStream());
        DataInputStream in=new DataInputStream(s.getInputStream());
        System.out.print("First string: ");
        out.writeUTF(sc.nextLine());
        System.out.print("Second string: ");
        out.writeUTF(sc.nextLine());
        System.out.println("Concatenated: "+in.readUTF());
        s.close();
    }
}
```

**Run:** `javac Client.java; java Client`

## PYTHON

### Q2 (A). Write a program which accepts an integer n and displays all prime numbers till n.

**Slip Solution**

```python
n=int(input("Enter n: "))
for x in range(2,n+1):
    if all(x%i for i in range(2,int(x**0.5)+1)):
        print(x,end=" ")
```

**Run:** `python slip20_q2a.py`

### Q2 (B). Write a Python script to generate and print a dictionary containing numbers from 1 to n in the form (x, x*x).

**Slip Solution**

```python
n=int(input("Enter n: "))
d={x:x*x for x in range(1,n+1)}
print(d)
```

**Run:** `python slip20_q2b.py`

