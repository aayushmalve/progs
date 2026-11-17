# Slip 30

## JAVA

### Q1 (A). Write a Java program to accept a number. If it is zero, throw a user-defined Number is Zero exception. If it is non-numeric, display Number is Invalid; otherwise check whether it is palindrome or not.

**Slip Solution**

```java
import java.util.Scanner;

class NumberIsZeroException extends Exception {
    NumberIsZeroException() { super("Number is Zero"); }
}

class NumberPalindrome {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        try {
            int n=Integer.parseInt(sc.nextLine());
            if(n==0) throw new NumberIsZeroException();
            String s=String.valueOf(n);
            String r=new StringBuilder(s).reverse().toString();
            System.out.println(s.equals(r)?"Palindrome":"Not Palindrome");
        } catch(NumberIsZeroException e) {
            System.out.println(e.getMessage());
        } catch(NumberFormatException e) {
            System.out.println("Number is Invalid");
        }
    }
}
```

**Run:** `javac NumberPalindrome.java && java NumberPalindrome`

### Q1 (B). Write a Java program to design the Personal Information GUI using Swing.

**Slip Solution**

The form includes First Name, Last Name, Address, Mobile Number, Gender (Male/Female), Your Interests (Computer/Sports/Music), Submit, and Reset.

```java
import javax.swing.*;
import java.awt.*;

class PersonalInfo {
    public static void main(String[] args) {
        JFrame f=new JFrame("Personal Information");
        JTextField first=new JTextField(),last=new JTextField(),address=new JTextField(),mobile=new JTextField();
        JRadioButton male=new JRadioButton("Male"),female=new JRadioButton("Female");
        ButtonGroup gender=new ButtonGroup();
        gender.add(male); gender.add(female);
        JCheckBox computer=new JCheckBox("Computer"),sports=new JCheckBox("Sports"),music=new JCheckBox("Music");
        JPanel g=new JPanel(); g.add(male); g.add(female);
        JPanel interests=new JPanel(); interests.add(computer); interests.add(sports); interests.add(music);
        JButton submit=new JButton("Submit"),reset=new JButton("Reset");
        JPanel form=new JPanel(new GridLayout(7,2,5,5));
        form.setBorder(BorderFactory.createTitledBorder("Personal Information"));
        form.add(new JLabel("First Name:")); form.add(first);
        form.add(new JLabel("Last Name:")); form.add(last);
        form.add(new JLabel("Address:")); form.add(address);
        form.add(new JLabel("Mobile Number:")); form.add(mobile);
        form.add(new JLabel("Gender:")); form.add(g);
        form.add(new JLabel("Your Interests:")); form.add(interests);
        form.add(submit); form.add(reset);
        submit.addActionListener(e->{
            String gen=male.isSelected()?"Male":female.isSelected()?"Female":"";
            String choices=(computer.isSelected()?"Computer ":"")+(sports.isSelected()?"Sports ":"")+(music.isSelected()?"Music":"");
            JOptionPane.showMessageDialog(f,"Name: "+first.getText()+" "+last.getText()+"\nAddress: "+address.getText()+"\nMobile: "+mobile.getText()+"\nGender: "+gen+"\nInterests: "+choices);
        });
        reset.addActionListener(e->{
            first.setText(""); last.setText(""); address.setText(""); mobile.setText("");
            gender.clearSelection(); computer.setSelected(false); sports.setSelected(false); music.setSelected(false);
        });
        f.add(form); f.setSize(500,300); f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); f.setLocationRelativeTo(null); f.setVisible(true);
    }
}
```

**Run:** `javac PersonalInfo.java && java PersonalInfo`

## PYTHON

### Q2 (A). Write a Python program to accept a string and a character from the user and count the occurrences of the character in the string.

**Slip Solution**

```python
s=input("Enter string: ")
c=input("Enter character: ")
print("Occurrences:",s.count(c))
```

**Run:** `python slip30_q2a.py`

### Q2 (B). Write a Python program to accept Date (Day, Month, Year) with functions to accept and display it. Throw a user-defined Invalid Date Exception if the date is invalid.

**Slip Solution**

```python
from datetime import date

class InvalidDateException(Exception):
    pass

def accept_date():
    d=int(input("Day: "))
    m=int(input("Month: "))
    y=int(input("Year: "))
    try:
        return date(y,m,d)
    except ValueError:
        raise InvalidDateException("Invalid Date")

def display_date(d):
    print("Date:",d.strftime("%d-%m-%Y"))

try:
    display_date(accept_date())
except InvalidDateException as e:
    print(e)
except ValueError:
    print("Invalid Date")
```

**Run:** `python slip30_q2b.py`

