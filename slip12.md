# Slip 12

## JAVA

### Q1 (A). Write a Java program to display each string in reverse order from a string array.

**Slip Solution**

```java
class ReverseStrings {
    public static void main(String[] args) {
        String[] a={"Java","Python","Computer"};
        for(String s:a) System.out.println(new StringBuilder(s).reverse());
    }
}
```

**Run:** `javac ReverseStrings.java && java ReverseStrings`

### Q1 (B). Write a Java program to display the multiplication table of a given number in a list box by clicking a button.

**Slip Solution**

```java
import javax.swing.*;
import java.awt.*;

class TableList {
    public static void main(String[] args) {
        JFrame f=new JFrame("Multiplication Table");
        JTextField n=new JTextField(8);
        JButton b=new JButton("Show Table");
        DefaultListModel<String> model=new DefaultListModel<>();
        JList<String> list=new JList<>(model);
        b.addActionListener(e->{
            model.clear();
            int x=Integer.parseInt(n.getText());
            for(int i=1;i<=10;i++) model.addElement(x+" x "+i+" = "+(x*i));
        });
        f.setLayout(new FlowLayout());
        f.add(n); f.add(b); f.add(new JScrollPane(list));
        f.setSize(300,350); f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); f.setVisible(true);
    }
}
```

**Run:** `javac TableList.java && java TableList`

## PYTHON

### Q2 (A). Write a Flask program to accept a string through an HTML form and check whether it is a palindrome.

**Slip Solution**

```python
from flask import Flask,request

app=Flask(__name__)

@app.route("/",methods=["GET","POST"])
def home():
    result=""
    if request.method=="POST":
        s=request.form["text"]
        result="Palindrome" if s==s[::-1] else "Not Palindrome"
    return f'<form method="post"><input name="text" required><button>Check</button></form><p>{result}</p>'

app.run()
```

Open `http://127.0.0.1:5000` in a browser.

**Run:** `pip install flask; python slip12_q2a.py`

### Q2 (B). Write a Python program to count repeated characters in the string thequickbrownfoxjumpsoverthelazydog.

**Slip Solution**

```python
from collections import Counter

s="thequickbrownfoxjumpsoverthelazydog"
counts=Counter(s)
for ch,n in sorted(counts.items(),key=lambda x:-x[1]):
    if n>1: print(f"{ch}-{n}",end=" ")
```

The repeated counts are o-4, e-3, u-2, h-2, r-2, t-2.

**Run:** `python slip12_q2b.py`

