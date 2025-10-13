

Java Slip Solutions
 Slip 2 A) Write a java program to display all the vowels from a given string.
Answer :
import java.io.DataInputStream;
class Slip2A {
    public static void main(String args[]){
        DataInputStream dr  = new DataInputStream(System.in);
        try {
            System.out.print("Enter String : ");
            String str = dr.readLine().toLowerCase();
            for(int i=0; i<str.length(); i++){
                if(str.charAt(i)=='a' || str.charAt(i)=='e' || str.charAt(i)=='i' || str.charAt(i)=='o'  || str.charAt(i)=='u' ){
                    System.out.print(str.charAt(i));
                }
            }
        } catch (Exception e) {}
    }
}


Slip 2 B) Design a screen in Java to handle the Mouse Events such as MOUSE_MOVED and MOUSE_CLICK and display the position of the Mouse_Click in a TextField.
Answer :
import java.awt.*;
import java.awt.event.*;
class MyFrame extends Frame
{
                TextField t,t1;
                Label l,l1;
                int x,y;
                Panel p;
                MyFrame(String title)
                {
                                super(title);
                                setLayout(new FlowLayout());
                               
                                p=new Panel();
                                p.setLayout(new GridLayout(2,2,5,5));
                                t=new TextField(20);
                                l= new Label("Mouse clicking");
                                l1= new Label("Mouse Movement");
                                t1=new TextField(20);
                                p.add(l);
                                p.add(t);
                                p.add(l1);
                                p.add(t1);
                                add(p);
                                addMouseListener(new MyClick());
                                addMouseMotionListener(new MyMove());
                                setSize(500,500);
                                setVisible(true);
                }
                class MyClick extends MouseAdapter
                {
                                public void mouseClicked(MouseEvent me)
                                {
                                                x=me.getX();
                                                y=me.getY();
                                                t.setText("X="+x+" Y="+y);
                                }
                }
                class MyMove extends MouseMotionAdapter
                {
                                public void mouseMoved(MouseEvent me)
                                {
                                                x=me.getX();
                                                y=me.getY();
                                                t1.setText("X="+ x +" Y="+y);
                                }
                }
}
class Slip2B
{
                public static void main(String args[])
                {
                                MyFrame f = new MyFrame("Slip Number 4");
                }
}

 Slip 3 A) Write a ‘java’ program to check whether given number is Armstrong or not. (Use static keyword)

Answer :

import java.io.DataInputStream;

class Slip3A {

    static int temp;

    public static void main(String args[]){

        int n,r,sum=0;

        DataInputStream dr = new DataInputStream(System.in);

        try {

            System.out.print("Enter Number");

            n = Integer.parseInt(dr.readLine());

            temp=n;

            while(n>0){

                r = n%10;

                sum=sum+(r*r*r);

                n=n/10;

            }

            if(temp==sum){

                System.out.println(temp +  " Is Armstrong Number : ");

            }else{

                System.out.println(temp +  " Is Not Armstrong Number : ");

            }

        } catch (Exception e) {}

    }

}
Slip 3 B) Define an abstract class Shape with abstract methods area () and volume (). Derive abstract class Shape into two classes Cone and Cylinder. Write a java Program to calculate area and volume of Cone and Cylinder.(Use Super Keyword.)
import java.io.*;
abstract class Shape
{
    int a,b;
    Shape(int x, int y){
        a = x;
        b = y;
    }
    abstract double area();
    abstract double volume();
}
class Cone extends Shape{
    Cone(int x, int y){
        super(x,y);
    }
    double area(){
        return (a*b*3.14);
    }
    double volume(){
        return (3.14*a*a*b);
    }
}
class Cylinder extends Shape{
    Cylinder(int x, int y){
        super(x,y);
    }
    double area(){
        return (2*3.14*a*b*3.14*a*b);
    }
    double volume(){
        return (3.14*a*a*b);
    }
}

class Slip3B{
    public static void main(String args[]) throws Exception{
        int r,h,s;
        DataInputStream dr = new DataInputStream(System.in);
        System.out.println("Enter Radius, Height and Side Values : ");
        r = Integer.parseInt(dr.readLine());
        h = Integer.parseInt(dr.readLine());
        s = Integer.parseInt(dr.readLine());
        Shape s1;
        Cone c1 = new Cone(r,s);
        s1=c1;
            System.out.println("Area of Cone  is : " + s1.area());
            System.out.println("Volume of Cone is : " +s1.volume());
        Cylinder cy = new Cylinder(r,h);
        s1 =cy;
            System.out.println("Area of Cylinder  is : " + s1.area());
            System.out.println("Area of Cylinder  is : " + s1.volume());
    }
}
Slip 4 A) Write a java program to display alternate character from a given string.
import java.io.DataInputStream;
class Slip4A {
    public static void main(String args[]){
        DataInputStream dr = new DataInputStream(System.in);
        try {
            System.out.print("Enter String : ");
            String str = dr.readLine();
            for(int i=0;i<str.length();i+=2) {
                System.out.print(" " + str.charAt(i));
            }
        } catch (Exception e) {}
    }
}
Output :
 
Slip 4 B) Write a java program using Applet to implement a simple arithmetic calculator.
Answer :
import java.awt.*;
import java.applet.*;
import java.awt.event.*;

public class Slip4B extends Applet implements ActionListener {
    Button b1, b2, b3, b4, b5, b6, b7, b8, b9, b10, b11, b12, b13, b14, b15, b16;
    String s1 = "", s2;
    Frame f;
    Panel p2;
    TextField t;
    int n1, n2;

    public void init(){

        setLayout(new BorderLayout());
        Frame title = (Frame) this.getParent().getParent();
        title.setTitle("Simple Calc");

        t = new TextField();
        p2 = new Panel();
        p2.setLayout(new GridLayout(6, 4, 2, 1));
        p2.setFont( new Font("Times New Roman",Font.BOLD,15));

        b1 = new Button("1");
        b1.addActionListener(this);

        b2 = new Button("2");
        b2.addActionListener(this);

        b3 = new Button("3");
        b3.addActionListener(this);

        b4 = new Button("+");
        b4.addActionListener(this);

        b5 = new Button("4");
        b5.addActionListener(this);

        b6 = new Button("5");
        b6.addActionListener(this);

        b7 = new Button("6");
        b7.addActionListener(this);

        b8 = new Button("-");
        b8.addActionListener(this);

        b9 = new Button("7");
        b9.addActionListener(this);

        b10 = new Button("8");
        b10.addActionListener(this);

        b11 = new Button("9");
        b11.addActionListener(this);

        b12 = new Button("*");
        b12.addActionListener(this);

        b13 = new Button("Clear");
        b13.addActionListener(this);

        b14 = new Button("0");
        b14.addActionListener(this);

        b15 = new Button("/");
        b15.addActionListener(this);

        b16 = new Button("=");
        b16.addActionListener(this);

        add(t, "North");

        p2.add(b9);
        p2.add(b10);
        p2.add(b11);
        p2.add(b4);

        p2.add(b5);
        p2.add(b6);
        p2.add(b7);
        p2.add(b8);

        p2.add(b1);
        p2.add(b2);
        p2.add(b3);
        p2.add(b12);

        p2.add(new Label(""));
        p2.add(b14);
        p2.add(new Label(""));
        p2.add(b15);
        p2.add(new Label(""));
        p2.add(new Label(""));
        p2.add(new Label(""));
        p2.add(b16);

        add(p2);
        p2.add(new Label(""));
        p2.add(b13);

    }

    public void actionPerformed(ActionEvent e1){
        String str = e1.getActionCommand();
        if (str.equals("+") || str.equals("-") || str.equals("*") || str.equals("/")){
            String str1 = t.getText();
            s2 = str;
            n1 = Integer.parseInt(str1);
            s1 = "";
        }else if (str.equals("=")){
            String str2 = t.getText();
            n2 = Integer.parseInt(str2);
            int sum = 0;

            if (s2 == "+")
                sum = n1 + n2;
            else if (s2 == "-")
                sum = n1 - n2;
            else if (s2 == "*")
                sum = n1 * n2;
            else if (s2 == "/")
                sum = n1 / n2;
            String str1 = String.valueOf(sum);
            t.setText("" + str1);
            s1 = "";
        }else if (str.equals("Clear")){
            t.setText("");
        }else{
            s1 += str;
            t.setText("" + s1);
        }
    }
}

/*
 * <applet code="Slip4B" height=250 width=250>
 * 
 * </applet>
 */
Slip 5 A) Write a java program to display following pattern:
5
4 5
3 4 5
2 3 4 5
1 2 3 4 5

class Slip5A {
    public static void main(String args[]){
        int i,j;
        for(i=5; i>=1; i--){
            for(j=i; j<=5; j++){
                System.out.print(j + " ");
            }
            System.out.println();
        }
    }
}



Slip 5 B) Write a java program to accept list of file names through command line. Delete the files having extension .txt. Display name, location and size of remaining files.

import java.io.*;
class Slip5B{
    public static void main(String args[]) throws Exception{
        for(int i=0;i<args.length;i++){
            File file=new File(args[i]);
            if(file.isFile()){
                String name = file.getName();
                if(name.endsWith(".txt")){
                    file.delete();
                    System.out.println("file is deleted " + file);
                }else{
                    System.out.println("File Name : " + name + "\nFile Location : " +file.getAbsolutePath()+"\nFile Size : "+file.length()+" bytes");
                }
            }
            else{
                System.out.println(args[i]+ "is not a file");
            }
        }
    }
}


Slip 8 A) Define an Interface Shape with abstract method area(). Write a java program to calculate an area of Circle and Sphere.(use final keyword)
Answer :
import java.util.*;
 
interface Shape{
    final float pi= 3.14F;
    double area();
}
class Circle implements Shape{
    int rad;
    Circle(int r){
        rad=r;
    }
    public double area(){
        return pi*rad*rad;
    }
}
class Sphere implements Shape{
     int rad;
     Sphere(int r){
         rad =r;
     }
     public double area(){
         return 4*pi*rad*rad;
     }
}
 
class Slip8A {
    public static void main(String args[]) throws Exception{
        int r;
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the Radius : ");
        r=sc.nextInt();
 
        Shape sh;
        Circle cl=new Circle(r);
        sh=cl;
        System.out.println("Area of Circle : " + sh.area());
 
        Sphere sp=new Sphere(r);
        sh=sp;
        System.out.println("Area of Sphare : "+sh.area());
    }
}

Slip 8 B) Write a java program to display the files having extension .txt from a given directory.

import java.io.File;
class Slip8B 
{
    public static void main(String[] args) 
{
File file = new File("C:\\Users\\Saurabh_Sapkal\\Desktop\\ln\\java\\Slips");
        String[] fileList = file.list();
        for(String str : fileList) {
            if(str.endsWith(".txt")){
                System.out.println(str);
            }
        }
    }
}
Slip 12 A) Write a java program to display each String in reverse order from a String array.
Answer :
class Slip12A{
    public static void main(String args[])
{
            String arr[] = {"swarup", "Sayali", "Mahesh"};
            for(int i=arr.length-1; i>=0; i--){
                System.out.print(arr[i] + ' ');
            }
    }
}
Output :

Slip 12 B) Write a java program to display multiplication table of a given number into the List box by clicking on button.
Answer :
import java.applet.*;
import java.awt.*;
import java.awt.event.*;
  public class Slip12B extends Applet implements ActionListener
{
     Button b1 = new Button("Show");
    List Multi = new List();
    String str ="";
    public void init()
{
        Multi.add("1");
        Multi.add("2");
        Multi.add("3");
        Multi.add("4");
        Multi.add("5");
        Multi.add("6");
        Multi.add("7");
        Multi.add("8");
        Multi.add("9");
        Multi.add("10");
        add(Multi);
        add(b1);
        b1.addActionListener(this);
    }
    public void paint(Graphics g){
 
        int count = 100; 
        int num = Integer.parseInt(Multi.getSelectedItem());
        for(int i=1;i<=10;i++){
            int a = num*i;
            g.drawString(i  +" * " + i +" = "+ a,100,count);
            count = count+20;
           }
    }
    public void actionPerformed(ActionEvent e){
        repaint();
    }
}
 /*
<applet code="Slip12B.class" width="300" height="300">
</applet>
*/
Output :
 

Slip 15 A) Write a java program to search given name into the array, if it is found then display its index otherwise display appropriate message.
Answer :
import java.io.DataInputStream;
class Slip15A{
    public static void main(String args[]){
        String arr[] = {"saurabh", "Sapkal", "Mahesh","priya"};
        int i,n=0;
        boolean a=false;
        DataInputStream dr = new DataInputStream(System.in);
        try {
            System.out.print("Enter String : ");
            String s= dr.readLine();
            for(i = 0; i < arr.length; i++)
            {
                if(arr[i].equals(s))
                {
                    n = i;
                    a = true;
                    break;
                }
            }
            if(a){
                System.out.println("arr" + "["+ i + "]");
            }else{
                System.out.println("not Found");
            }
        } catch (Exception e) {}
    }
}
Output :
 
Slip 15 B) Write an applet application to display smiley face.
Answer :
import java.applet.Applet;
import java.awt.Graphics;
public class Slip15B extends Applet
{
 
public void paint(Graphics g){
    g.drawOval(80, 70, 150, 150);
    g.fillOval(120, 120, 15, 15);
    g.fillOval(170, 120, 15, 15);
    g.drawArc(130, 180, 50, 20, 180, 180);
}
 
}
/*
<applet code="Slip15B.class" width="300" height="300">
</applet>
*/
Output :
 

Slip 18 A) Write a Java program to calculate area of Circle, Triangle & Rectangle.(Use Method Overloading)
import java.util.*;
class AreaCalculate
{
    void area(int r){
        System.out.println("Area of Cirlce = " + (3.14*r*r));
    }
 
    float area(int b, float h){
        return b*h/2;
    }
 
    double area(Float l, Float db){
        return l+db;
    }
   
}
class Slip18A {
    public static void main(String args[]){
        int r, b, l, db;
        float h;
        Scanner br = new Scanner(System.in);
        System.out.println("Enter the radius, base, height, length and breadth : ");
        r = br.nextInt();
        b = br.nextInt();
        h = br.nextFloat();
        l = br.nextInt();
        db = br.nextInt();
        AreaCalculate ac = new AreaCalculate();
        ac.area(r);
        System.out.println("Area of Triangle = " +ac.area(b,h));
        System.out.println("Area of Rectange = " +ac.area(l,db));
 
    }
}

Slip 18 B) Write a java program to copy the data from one file into another file, while copying change the case of characters in target file and replaces all digits by ‘*’ symbol.
import java.io.*;
class Slip18B{
    public static void main(String args[]) throws IOException{
        FileReader fr = new FileReader("a.txt");
        FileWriter fw = new FileWriter("b.txt");
        int c;
        while ((c=fr.read())!=-1){
          if(Character.isDigit(c)==false)
{
              if(Character.isUpperCase(c))
{
                fw.write(Character.toLowerCase(c));
              }
else if(Character.isLowerCase(c)){
                fw.write(Character.toUpperCase(c));
              }
          }else{
              fw.write('*');
          }
        }
        fr.close();
        fw.close();
    }
}

Slip 20 A) Write a java program using AWT to create a Frame with title “TYBBACA”, background color RED. If user clicks on close button then frame should close.
Answer :
 import javax.swing.*;
import java.awt.*;
 
class Slip20A {
    public static void main(String args[]) {
        JFrame frame = new JFrame("TYBBACA");
        frame.setSize(400, 400);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().setBackground(Color.RED);
        frame.setVisible(true);
    }
}
Slip 20 B) Construct a Linked List containing name: CPP, Java, Python and PHP. Then extend your java program to do the following:
i. Display the contents of the List using an Iterator
ii. Display the contents of the List in reverse order using a List Iterator.
Answer :
import java.util.*;
    public class Slip20B{
        public static void main (String args[]){
            LinkedList al = new LinkedList<>();
            al.add("CPP");
            al.add("JAVA");
            al.add("Python");
            al.add("PHP");
            System.out.println("Display content using Iterator...");
            Iterator il=al.iterator();
            while(il.hasNext()){
                System.out.println(il.next());
            }
            System.out.println("Display Content Revverse Using ListIterator");
            ListIterator li1=al.listIterator();
            while(li1.hasNext()){
                li1.next();
            }
            while(li1.hasPrevious()){
                System.out.println("" + li1.previous());
            }
        }
    }
Output :
 

Slip 21 A) Write a java program to display each word from a file in reverse order.
Answer :
import java.io.*;
import java.util.Scanner;
class Slip21A{
    public static void main(String args[]) throws IOException
{
        FileReader fr = new FileReader("a.txt");
        FileWriter fw = new FileWriter("b.txt");
        try (Scanner dr = new Scanner(fr)) 
{
            while(dr.hasNextLine()){
                String s=dr.nextLine();
                StringBuffer buffer = new StringBuffer(s);
                buffer=buffer.reverse();
                String ans = buffer.toString();
                fw.write(ans);
            }
        }catch(Exception e){
            System.out.print("Error...!");
        }
        fr.close();
        fw.close();
    }
}
Slip 21 B) Create a hash table containing city name & STD code. Display the details of the hash table. Also search for a specific city and display STD code of that city.
Answer :
import java.util.*;
import java.io.*;
 
public class Slip21B {
    public static void main(String args[])
{
        Hashtable h1=new Hashtable<>();
        Enumeration en;
        int i,n,std,val,max=0;
        String nm, cname, str, s=null;
        DataInputStream dr = new DataInputStream(System.in);
        try {
            System.out.print("Enter the how Many Record You Want : ");
            n = Integer.parseInt(dr.readLine());
            System.out.print("Enter the City Name & STD Code : ");
            for(i=0; i<n; i++){
                cname = dr.readLine();
                std = Integer.parseInt(dr.readLine());
                h1.put(cname,std);
            }
            System.out.print("Enter city name to search : ");
            nm = dr.readLine();
            en=h1.keys();
            while(en.hasMoreElements())
{
                str=(String)en.nextElement();
                val=(Integer)h1.get(str);
                if(str.equals(nm)){
                    System.out.print("STD Code : " + val);
                }
            }
        } catch (Exception e) {}
    }   
}



Slip 25 A) Write a java program to check whether given string is palindrome or not.

import java.io.DataInputStream;
public class Slip25A {
    public static void main(String args[]){
        int i=0,h=0;
        DataInputStream dr = new DataInputStream(System.in);
        try {
            System.out.print("Enter String : ");
            String str = dr.readLine();
            int j= str.length()-1;
            while(i<j){
                if(str.charAt(i++) != str.charAt(j--)){
                   h = h + i ;
                }
            }
           if(h>0){
               System.out.println("String is not palindrome");
           }else{
                System.out.println("String is palindrome");
           }
        } catch (Exception e) {}
    }
}
Output :
 
Slip 25 B) Create a package named Series having three different classes to print series:
i. Fibonacci series
ii. Cube of numbers
iii. Square of numbers Write a java program to generate ‘n’ terms of the above series.
Answer :
import java.io.*;
import Series.*;

class Slip25B
 {
    public static void main(String args[])throws Exception{
        int n1,n2,n3;
        DataInputStream dr = new DataInputStream(System.in);
        System.out.print("Enter How Many fibonnacci series you want : ");
        n1=Integer.parseInt(dr.readLine());
        System.out.print("Enter How Many cube you want  : ");
        n2=Integer.parseInt(dr.readLine());
        System.out.print("Enter How Many Squares you want : ");
        n3=Integer.parseInt(dr.readLine());
        
        System.out.println("\nFibonacci Series ....");
        Fibo f1 = new Fibo();
        f1.fiboSeries(n1);


        System.out.println("\nCube Series ....");
        Cubes c1=new Cubes();
        c1.cubeSeries(n2);


        System.out.println("\nSquare Series ....");
        Square s1=new Square();
        s1.squareSeries(n3);
    }
}


//Create folder series


//Cubes.java


package Series;


public class Cubes {
    public void cubeSeries(int n){
        for(int i=1; i<=n; i++){
            int c=(i*i*i);
            System.out.print(c + " ");
        }
    }
}


//Fibo.java

package Series;


public class Fibo {
    public int f=0, s=1, i;
    public void fiboSeries(int nl){
        for(i=1; i<=nl; i++){
            System.out.print(f + " ");
            int n=f+s;
            f=s;
            s=n;
        }
    }
}


//Square.java

package Series;


public class Square {
    public void squareSeries(int n){
        for(int i=1; i<=n; i++){
            int c=(i*i);
            System.out.print(c +" ");
        }
    }
}
Output :
 

Slip 28 A) Write a java program to count the number of integers from a given list. (Use Command line arguments).
Answer :
import java.util.*;
public class Slip28A {
    public static void main(String[] args)
 {
        int count = 0;
        List<String> al = new ArrayList<>();
        for (int i = 0; i < args.length; i++) {
            al.add(args[i]);
        }
        for (int i = 0; i < al.size(); i++) {
            String element = al.get(i);
            Try
 {
                int j = Integer.parseInt(element);
                count++;
            } catch (NumberFormatException e) {}
        }
        System.out.println(count + " integers present in list");
    }
}
Output :
 
Slip 28 B) Write a java Program to accept the details of 5 employees (Eno, Ename, Salary) and display it onto the JTable.
Answer :
import javax.swing.*;
public class Slip28B 
{
    JFrame f;
    JTable j;
    Slip28B(){
       f = new JFrame();
        f.setTitle("Employee Details");
        String data[][] = {
            {"1","Radhika Sapkal","50,000"},
            {"2","Ramesh Devakar","20,000"},
            {"3","Hardik Shrinivas","25,000"},
            {"4","Bhihari Kumar","20,000"},
            {"5","Swaraghini Pawar","15,000"},
        };
        String[] columnNames = {"Eno", "Ename", "Salary" };
        j = new JTable(data, columnNames);
        j.setBounds(30,40,200,300);
        JScrollPane sp = new JScrollPane(j);
        f.add(sp);
        f.setSize(500,200);
        f.setVisible(true);
    }
 
    public static void main(String args[]) {
        new Slip28B();
    }
}
Output :


python


Slip 2:
A.	Write a Python function that accepts a string and calculate the number of upper case letters and lower case letters. Sample String: 'The quick Brown Fox' Expected Output: No. of Upper case characters: 3 No. of Lower case characters: 13
def string_test(s):
d={"UPPER_CASE":0, "LOWER_CASE":0}
for c in s:
if c.isupper(): d["UPPER_CASE"]+=1
elif c.islower(): d["LOWER_CASE"]+=1
else:
pass
print ("Original String : ", s)
print ("No. of Upper case characters : ", d["UPPER_CASE"]) print ("No. of Lower case Characters : ", d["LOWER_CASE"])
str1=input("Enter the string you want: ") string_test(str1)
 

Output:-
Enter the string you want: Hello I Am TYBBA(CA) Student Original String : Hello I Am TYBBA(CA) Student
No. of Upper case characters : 11 No. of Lower case Characters : 11
 
B.	Write Python GUI program to create a digital clock with Tkinter to display the time
import time
from tkinter import * canvas = Tk()
canvas.title("Digital Clock") canvas.geometry("350x200") canvas.resizable(1,1)
label = Label(canvas, font=("Courier", 30, 'bold'), bg="red", fg="white", bd =30) label.grid(row =0, column=1)
def digitalclock():
text_input = time.strftime("%H:%M:%S %p") label.config(text=text_input) label.after(200, digitalclock)
digitalclock()
canvas.mainloop()

Slip 3:

A.	Write a Python program to check if a given key already exists in a dictionary. If key exists replace with another key/value pair.
d={'A':1,'B':2,'C':3}
key=input("Enter key to check:") check_value = input("Enter Value: ") if key in d.keys():
print("Key is present and value of the key is:") print(d[key])
d.pop(key) d[key]=check_value
else:
print("Key isn't present!") d[key]=check_value
print("Updated dictionary : ",d)
 
Output:
Enter key to check:A Enter Value: 4
Key is present and value of the key is: 1
Updated dictionary: {'B': 2, 'C': 3, 'A': '4'}
 
B.	Write a python script to define a class student having members roll no, name, age, gender. Create a subclass called Test with member marks of 3 subjects. Create three objects of the Test class and display all the details of the student with total marks.
class Student:
def GetStudent(self):
self.RollNo=int(input("\nEnter Student Roll No:")) self.Name=input("Enter Student Name:") self.Age=int(input("Enter Student Age:")) self.Gender=input("Enter Student Gender:")
def PutStudent(self):
print("Student Roll No:",self.RollNo) print("Student Name:",self.Name) print("Student Age:",self.Age) print("Student Gender:",self.Gender)
class Test(Student): def GetMarks(self):
self.MarkMar=int(input("Enter Marks of Marathi Subject")) self.MarkHin=int(input("Enter Marks of Hindi Subject")) self.MarkEng=int(input("Enter Marks of Eglish Subject"))
def PutMarks(self):
print("Marathi Marks:", self.MarkMar) print("Hindi Marks:", self.MarkHin) print("English Marks:", self.MarkEng)
print("Total Marks:",self.MarkMar+self.MarkHin+self.MarkEng)

n=int(input("Enter How may students")) lst=[]
for i in range(0,n): obj=input("Enter Object Name:") lst.append(obj)
print(lst)
for j in range(0,n): lst[j]=Test() lst[j].GetStudent() lst[j].GetMarks()
print("\nDisplay Details of Student",j+1) lst[j].PutStudent()
lst[j].PutMarks()
Output:
Enter How may students2 Enter Object Name:A ['A']
Enter Object Name:B ['A', 'B']
Enter Student Roll No:101 Enter Student Name:Priti
 
Enter Student Age:10 Enter Student Gender:F
Enter Marks of Marathi Subject10 Enter Marks of Hindi Subject20 Enter Marks of Eglish Subject30 Display Details of Student 1 Student Roll No: 101
Student Name: Priti Student Age: 10 Student Gender: F Marathi Marks: 10
Hindi Marks: 20
English Marks: 30
Total Marks: 60
Enter Student Roll No:201 Enter Student Name:Suhas Enter Student Age:20 Enter Student Gender:M
Enter Marks of Marathi Subject30 Enter Marks of Hindi Subject40 Enter Marks of Eglish Subject50

Display Details of Student 2 Student Roll No: 201 Student Name: Suhas Student Age: 20
Student Gender: M Marathi Marks: 30
Hindi Marks: 40
English Marks: 50
Total Marks: 120

Slip 4:
A: Write Python GUI program to create background with changing colors
 
 

B: Define a class Employee having members id, name, department, salary. Create a subclass called manager with member bonus. Define methods accept and display in both the classes. Create n objects of the manager class and display the details of the manager having the maximum total salary (salary+bonus).
 
 
 


Slip5:
A: Write a Python script using class, which has two methods get_String and print_String. get_String accept a string from the user and print_String print the string in upper case.


Output:
Hello i am TYBBA(CA) Student HELLO I AM TYBBA(CA) STUDEN


B: Write a python script to generate Fibonacci terms using generator function.
 
 
Output:
How many terms? 6 Fibonacci sequence:
0
1
1
2
3
5

Slip 8:
A: Write a python script to find the repeated items of a tuple

Output:
Enter the number of elements in list:3 Enter element1:10
Enter element2:20 Enter element3:10
Repeated elements in given tuple 10

B: Write a Python class which has two methods get_String and print_String. get_String accept a string from the user and print_String print the string in upper case. Further modify the program to reverse a string word by word and print it in lower case.
 
 
 
Output:
Enter any String: Priti
String in Upper Case: PRITI
String in Reverse & Lower case: itirp

Slip 12:
A: Write a Python GUI program to create a label and change the label font style (font name, bold, size) using tkinter module.
 



B: Write a python program to count repeated characters in a string. Sample string: 'thequickbrownfoxjumpsoverthelazydog' Expected output: o-4, e-3, u-2, h-2, r-2, t-2
 
Output:
Enter the string you want: Hello I Am TYBBA(CA) Student 4
A 3
 
e 2
l 2
B 2
t 2

Slip 15:
A: Write a Python class named Student with two attributes student_name, marks. Modify the attribute values of the said class and print the original and modified values of the said attributes.
 
Output:
Enter Student Name:Geeta Enter Student Total Marks:67
Enter Student New Total Marks:78 Student Name: Geeta
Old Total Mark: 67 New Total Mark: 78

B: Write a python program to accept string and remove the characters which have odd index values of given string using user defined function
 
 
 print(odd_values_string(str))	
Output:
Enter the string you want:
Hello Hlo


Slip 18:
A: Create a list a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89] and write a python program that prints out all the elements of the list that are less than 5
 
Output:
[1, 1, 2, 3]

 
B: Write a python script to define the class person having members name, address. Create a subclass called Employee with members staffed salary. Create 'n' objects of the Employee class and display all the details of the employee.
 
Output:
Enter How may Employee: 1 Enter Object Name:A
['A']

Enter tne name of Person: Priti Enter Address of Person: Pune Enter Salary of Employee1234

Display Details of Employee 1 Person Name: Priti
Student Address: Pune Salary of Employee: 1234


Slip 20:
A: Write a python program to create a class Circle and Compute the Area and the circumferences of the circle.(use parameterized constructor)
 


Output:
200.96
50.24

B: Write a Python script to generate and print a dictionary which contains a number (between 1 and n) in the form(x,x*x). Sample Dictionary (n=5) Expected Output: {1:1, 2:4, 3:9, 4:16, 5:25}
 
Output:
Input a number 5
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

Slip 21:
A: Define a class named Rectangle which can be constructed by a length and width. The Rectangle class has a method which can compute the area and Perimeter.
 
Output:
120

B) Write a Python program to convert a tuple of string values to a tuple of integer values. Original tuple values: (('333', '33'), ('1416', '55')) New tuple values: ((333, 33), (1416, 55))
 
 
 print(Convert_Fun(tuple_str))	
Output:
Original tuple values:
(('333', '33'), ('1416', '55'))

New tuple values:
((333, 33), (1416, 55)



Slip 25:
A: Write a Python function that accepts a string and calculate the number of upper case letters and lower case letters. Sample String : 'The quick Brow Fox' Expected Output : No. of Upper case characters : 3 No. of Lower case Characters : 12
 
 
 

Output:MM
Enter string:Hello I am TYBBA(CA) Student The number of lowercase characters is:
12
The number of uppercase characters is:
10

B: Write a Python script to Create a Class which Performs Basic Calculator Operations
 
 

Output:

1.	Addtion
2.	Substraction
3.	Multiplication
4.	Exit
Enter choice to perform any opertaion1 Enter first no:10
Enter Second no:20 Addition is: 30

1.	Addtion
2.	Substraction
3.	Multiplication
4.	Exit
Enter choice to perform any opertaion4 Program Stop
Slip 28:
A: Write a Python GUI program to create a list of Computer Science Courses using Tkinter module (use Listbox).
 
 
 

Output:-

B: Write a Python program to accept two lists and merge the two lists into list of tuple.
 
Output:
Enter number of elements of first list : 3 10
20
30
[10, 20, 30]
Enter number of elements of second list : 3
 
20
30
40
[20, 30, 40]
After the merging of two list [(10, 20), (20, 30), (30, 40)]


 

