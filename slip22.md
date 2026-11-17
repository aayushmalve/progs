# Slip 22

## JAVA

### Q1 (A). Write a Java program to calculate factorial of a number using a loop.

**Slip Solution**

```java
import java.util.Scanner;

class Factorial {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        long f=1;
        for(int i=1;i<=n;i++) f*=i;
        System.out.println("Factorial: "+f);
    }
}
```

**Run:** `javac Factorial.java && java Factorial`

### Q1 (B). Write a Java program to display all records of a table in JTable and provide navigation using Scrollable ResultSet.

**Slip Solution**

```java
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.sql.*;

class StudentTable {
    public static void main(String[] args) throws Exception {
        Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/college","root","password");
        Statement st=con.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE,ResultSet.CONCUR_READ_ONLY);
        ResultSet rs=st.executeQuery("SELECT * FROM student");
        ResultSetMetaData md=rs.getMetaData();
        DefaultTableModel model=new DefaultTableModel();
        for(int i=1;i<=md.getColumnCount();i++) model.addColumn(md.getColumnName(i));
        while(rs.next()) {
            Object[] row=new Object[md.getColumnCount()];
            for(int i=1;i<=md.getColumnCount();i++) row[i-1]=rs.getObject(i);
            model.addRow(row);
        }
        rs.beforeFirst();
        JTable table=new JTable(model);
        JButton next=new JButton("Next"),previous=new JButton("Previous");
        next.addActionListener(e->{
            try { if(rs.next()) table.setRowSelectionInterval(rs.getRow()-1,rs.getRow()-1); }
            catch(SQLException ex) { JOptionPane.showMessageDialog(null,ex.getMessage()); }
        });
        previous.addActionListener(e->{
            try { if(rs.previous()) table.setRowSelectionInterval(rs.getRow()-1,rs.getRow()-1); }
            catch(SQLException ex) { JOptionPane.showMessageDialog(null,ex.getMessage()); }
        });
        JFrame f=new JFrame("Student Records");
        f.add(new JScrollPane(table),BorderLayout.CENTER);
        JPanel p=new JPanel(); p.add(previous); p.add(next);
        f.add(p,BorderLayout.SOUTH);
        f.setSize(600,400); f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); f.setVisible(true);
    }
}
```

**Database setup:** Run this SQL in MySQL before running the program:

```sql
CREATE DATABASE college;
USE college;
CREATE TABLE student(id INT PRIMARY KEY,name VARCHAR(50),marks INT);
INSERT INTO student VALUES(1,'Asha',85),(2,'Ravi',78),(3,'Neha',92);
```

Update the JDBC username and password in the connection line. The statement requests a scrollable, read-only ResultSet.

**Run:** `javac -cp mysql-connector-j.jar StudentTable.java && java -cp .:mysql-connector-j.jar StudentTable`

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

### Q2 (B). E-Commerce Order Analysis. Calculate order value, region-wise sales, top-selling product, create visualizations, and generate a final report.

**Slip Solution**

```python
import pandas as pd
import matplotlib.pyplot as plt

data={
    "Order ID":[1,2,3,4,5,6],
    "Product":["Laptop","Phone","Laptop","Tablet","Phone","Tablet"],
    "Quantity":[2,3,1,4,2,3],
    "Price":[50000,20000,50000,15000,20000,15000],
    "Region":["West","East","West","North","East","South"]
}
df=pd.DataFrame(data)
df["Order Value"]=df["Quantity"]*df["Price"]
region=df.groupby("Region")["Order Value"].sum()
product=df.groupby("Product")["Quantity"].sum()
print(df)
print("Region-wise sales:\n",region)
print("Top-selling product:",product.idxmax())
print("Total sales:",df["Order Value"].sum())
print("Final report: Total sales =",df["Order Value"].sum(),"; top product =",product.idxmax())
region.plot(kind="bar",title="Region-wise Sales")
plt.ylabel("Sales")
plt.tight_layout()
plt.show()
product.plot(kind="bar",title="Product-wise Quantity")
plt.ylabel("Quantity")
plt.tight_layout()
plt.show()
```

**Run:** `pip install pandas matplotlib; python slip22_q2b.py`
