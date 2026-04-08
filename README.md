public partial class _Default : System.Web.UI.Page 
{ 
SqlConnection con = new 
SqlConnection(ConfigurationManager.ConnectionStrings["Conn
ectionString"].ConnectionString );   
protected void Page_Load(object sender, EventArgs e) 
{ 
} 
protected void TextBox2_TextChanged(object sender, 
EventArgs e) 
{ 
} 
protected void Button1_Click(object sender, EventArgs 
e) 
{ 
con.Open(); 
string sql = "INSERT INTO 
[dept1](dept_id,dname,ename,sal)VALUES("+TextBox1.Text+",'
"+TextBox2 .Text +"','"+TextBox3 .Text 
+"',"+TextBox4.Text+")"; 
SqlCommand cmd = new SqlCommand(sql,con); 
con.Close(); 
GridView1.DataBind(); 
} 
} 
 
 
 
 
 
 
Slip 1 - A) Write a java program to scroll the 
text from left to right and vice versa 
continuously. 
Solution: 
 
 
 
 
import java.applet.Applet;  
import java.awt.*;  
import java.awt.event.*;   
/* <APPLET CODE=ScrollingText.class WIDTH=400 HEIGHT=200 > 
</APPLET> */  
public class ScrollingText  extends Applet implements Runnable  
{  
   String msg="Welcome to Java Programming Language .......    ";  
                    Thread t=null;  
                    public void init()  
                        {  
                       setBackground(Color.cyan);  
                       setForeground(Color.red);  
                       t=new Thread(this);  
                       t.start();  
                    }   
                       public void run()  
                          {  
                           char ch;  
                           for(; ;)  
                               {  
                                 try  
                                   {  
                                      repaint();  
                                      Thread.sleep(400);  
                                      ch=msg.charAt(0);  
                                       msg=msg.substring(1,msg.length());  
                                       msg+=ch;  
                                   }  
                                               catch(InterruptedException e)  
                                               {}  
                                       }  
                              }  
                                               public void paint(Graphics g)  
                                                 {  
                                                    g.drawString(msg,10,10);  
                                                 }  
                 } 
 
 
Slip 1 - B) Write a socket program in java for 
chatting application.(Use Swing) 
 
Server code: 
import java.awt.event.*; 
import java.awt.*; 
import java.net.*; 
import java.io.*; 
 
class MyServer extends Frame implements ActionListener 
{ 
 static TextField t1=new TextField(20); 
 static Button b1=new Button("Send"); 
 static TextArea ta=new TextArea(5,20); 
 static DataOutputStream dos; 
 static DataInputStream dis; 
 static ServerSocket st; 
 static Socket s; 
 static String r; 
 MyServer() 
 { 
  setLayout(new FlowLayout()); 
  add(t1);add(b1);add(ta); 
  b1.addActionListener(this);   
  setVisible(true); 
  setSize(300,300); 
 } 
 public void actionPerformed(ActionEvent e) 
 { 
  String cmd=e.getActionCommand(); 
  if(cmd.equalsIgnoreCase("send")) 
  { 
   try 
   { 
   r=t1.getText(); 
   dos.writeUTF(r); 
   } 
   catch(Exception p) 
   { 
   } 
  } 
 } 
 public static void main(String[] d ) throws IOException 
 { 
  new MyServer(); 
st=new ServerSocket(1281);  
s=st.accept(); 
dos=new DataOutputStream(s.getOutputStream()); 
dis=new DataInputStream(s.getInputStream()); 
while(true) 
{ 
} 
} 
} 
Client code: 
r=dis.readUTF(); 
ta.append("client:"+r+"\n"); 
import java.awt.event.*; 
import java.awt.*; 
import java.net.*; 
import java.io.*; 
class MyClient extends Frame implements ActionListener 
{ 
static TextField t1=new TextField(20); 
static Button b1=new Button("Send"); 
static TextArea ta=new TextArea(5,20); 
static DataOutputStream dos; 
static DataInputStream dis; 
static Socket s; 
 static String r; 
 MyClient() 
 { 
  setLayout(new FlowLayout()); 
  add(t1);add(b1);add(ta); 
  b1.addActionListener(this);   
  setVisible(true); 
  setSize(300,300); 
 
 
 } 
 public void actionPerformed(ActionEvent e) 
 { 
  if(e.getSource()==b1) 
  { 
   try 
  { 
   r=t1.getText(); 
   dos.writeUTF(r); 
  } 
  catch(Exception p) 
  { 
  } 
  } 
 } 
 public static void main(String[] d ) throws IOException 
 { 
  MyClient x= new MyClient(); 
   
   
  s=new Socket("localhost",1281); 
  dos=new DataOutputStream(s.getOutputStream()); 
  dis=new DataInputStream(s.getInputStream()); 
  while(true) 
  { 
   r=dis.readUTF(); 
   ta.append("Server:"+r+"\n"); 
  } 
 } 
  
} 
 
A) Write a VB.Net Program to display the numbers continuously in TextBox by 
clicking on Button. 
 
 
Answer : 
Public Class Form1 
    Private Sub Timer1_Tick(sender As Object, e As EventArgs) Handles Timer1.Tick 
        TextBox1.Text = Second(DateTime.Now) 
    End Sub 
  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
        Timer1.Enabled = True 
        Timer1.Interval = 1000 
        Timer1.Start() 
    End Sub 
End Class 
 
 
B) Write a VB.Net program to accept the details of Employee (ENO, EName Salary) 
and store it into the database and display it on gridview control. 
Answer : 
Imports System 
Imports System.Data 
Imports System.Data.OleDb 
Public Class Form1 
    Dim con As New OleDbConnection("Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Users\Desktop\New 
folder\Emp.accdb") 
    Dim adpt As New OleDbDataAdapter("Select * from Emp", con) 
    Dim ds As New DataSet 
    Dim cmd As New OleDbCommand 
    Public Function display() 
        adpt.Fill(ds, "Emp") 
        DataGridView1.DataSource = ds 
        DataGridView1.DataMember = "Emp" 
        Return ds 
    End Function 
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load 
        display() 
    End Sub 
  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
        cmd.Connection = con 
        cmd.CommandType = CommandType.Text 
        cmd.CommandText = "insert into Emp values(" & TextBox1.Text & ",'" & TextBox2.Text & "'," & 
TextBox3.Text & ")" 
        con.Open() 
        cmd.ExecuteNonQuery() 
        con.Close() 
        ds.Clear() 
        display() 
    End Sub 
End Class 
 
 
Slip 2 
 
A) Write a JSP program to check whether given number is Perfect or not. (Use Include 
directive). 
Answer : 
 Slip2A.html 
<html> 
  
<body> 
    <h1>Find Perfect Number</h1> 
    <form action="http://127.0.0.1:8080/java/Slip2A.jsp" method="GET"> 
        Enter Number : <input type='text' name='no'> 
        <input type='submit' value='SUBMIT'> 
    </form> 
</body> 
  
</html> 
  
Slip2A.jsp 
<%@ page language="java" %> 
<html> 
    <body> 
        <% 
            int n = Integer.parseInt(request.getParameter("no")); 
            int n1=0; 
            for(int i=1; i<n; i++){ 
                if(n%i==0){ 
                    n1+=i; 
                } 
            } 
            if(n1==n){ 
                out.println("Perfect Number"); 
            }else{ 
                out.println("not Perfect Number"); 
            } 
        %> 
    </body> 
</html> 
 
 
B) Write a java program in multithreading using applet for drawing flag. 
Answer : 
import java.awt.*; 
  
public class Slip2B extends Frame{ 
  
    int f = 0; 
  
    public Slip2B(){ 
        Signal s = new Signal(); 
        s.start(); 
        setSize(500,500); 
        setVisible(true); 
    } 
  
    public void paint (Graphics g){ 
        switch (f){ 
            case 0 : 
            g.drawLine(150, 50, 150, 300); 
            case 1 : 
            g.drawRect(150, 50, 100, 90); 
        } 
    } 
  
class Signal extends Thread{ 
    public void run(){ 
        while(true){ 
            f = (f+1)%2; 
            repaint(); 
            try{ 
                Thread.sleep(1000); 
            }catch(Exception e){ 
  
            } 
        } 
    } 
} 
    public static void main(String args[]){ 
        new Slip2B(); 
    } 
} 
 
Slip: 2 
A) Write a Vb.Net program to move the Text “Pune University” continuously from Left 
 to Right and Vice Versa. 
 
Answer : 
 
Public Class Form1

    Dim direction As Integer = 1   ' 1 = right, -1 = left

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Timer1.Interval = 50
        Timer1.Start()
    End Sub

    Private Sub Timer1_Tick(sender As Object, e As EventArgs) Handles Timer1.Tick
        Label1.Left = Label1.Left + direction

        ' Right boundary
        If Label1.Right >= Me.Width Then
            direction = -1
        End If

        ' Left boundary
        If Label1.Left <= 0 Then
            direction = 1
        End If
    End Sub

End Class
  
 
B)Write a C#.Net program to create a base class Department and derived classes Sales and 
Human Resource. Accept the details of both departments and display them in proper 
format. 
 
namespace ConsoleApp4 
{ 
    
    class Department 
    { 
 
        public string name; 
 
        public void display() 
        { 
            Console.WriteLine("Here is department"); 
        } 
 
    } 
 
    // derived class of Sales  
    class Sales : Department 
    { 
 
        public void getName() 
        { 
            Console.WriteLine("Department name is " + name); 
        } 
    } 
    // derived class of Human Resource  
    class Human_Resource : Department 
    { 
 
        public void getName() 
        { 
            Console.WriteLine("Department name is " + name); 
        } 
    } 
    class Program 
    { 
 
        static void Main(string[] args) 
        { 
 
            // object of derived class 
            Sales dept = new Sales(); 
 
            // access field and method of base class 
            dept.name = "Sales"; 
            dept.display(); 
 
            // access method from own class 
            dept.getName(); 
 
            // object of derived class 
            Human_Resource dept1 = new Human_Resource(); 
 
            // access field and method of base class 
            dept1.name = "HR"; 
            dept1.display(); 
 
            // access method from own class 
            dept1.getName(); 
 
            Console.ReadLine(); 
        } 
 
    } 
} 
 
 
slip: 3 
A) Write a socket program in Java to check whether given number is prime or not. 
Display result on client terminal. 
//Client 
import java.io.*; 
import java.net.*; 
 public class Slip3A  
{ 
    public static void main(String args[]) throws Exception  
{ 
        Socket s = new Socket("localhost", 7500); 
        DataInputStream din = new DataInputStream(System.in); 
        System.out.print("Enter any number:"); 
  
        String n = din.readLine(); 
        System.out.println("===================="); 
  
        DataOutputStream dos = new DataOutputStream(s.getOutputStream()); 
        dos.writeBytes(n + "\n"); 
  
        DataInputStream dis = new DataInputStream(s.getInputStream()); 
        System.out.println(dis.readLine()); 
  
    } 
} 
//Server 
import java.io.*; 
import java.net.*; 
  
public class Slip3A1 { 
    public static void main(String args[]) throws Exception { 
        ServerSocket ss = new ServerSocket(7500); 
        Socket s = ss.accept(); 
         DataInputStream dis = new DataInputStream(s.getInputStream()); 
        int n = Integer.parseInt(dis.readLine()); 
  
        int i, cnt = 0; 
  
        for (i = 2; i < n; i++) 
 { 
            if (n % i == 0) 
                cnt++; 
            break; 
        } 
  
        DataOutputStream dos = new DataOutputStream(s.getOutputStream()); 
  
        if (cnt == 0) 
            dos.writeBytes(n + " is prime number."); 
        else 
            dos.writeBytes(n + " is not prime number."); 
  
        s.close(); 
  
    } 
} 
 
B) Write a java program using applet for bouncing ball, for each bounce color of ball 
should change randomly. 
  
Answer : 
import java.awt.*; 
import java.awt.event.*; 
  
public class Slip3B extends Frame implements Runnable { 
    private int x, y, w, h, f; 
    private Color c = Color.red; 
  
    public Slip3B() { 
        setTitle("Bouncing Boll"); 
        setSize(400, 400); 
        setVisible(true); 
        w = getWidth(); 
        h = getHeight(); 
        x = (int) (Math.random() * getWidth()); 
        y = (int) (Math.random() * getHeight()); 
        Thread t = new Thread(this); 
        t.start(); 
    } 
  
    public void run() { 
        while (true) { 
            switch (f) { 
                case 0: 
                    y++; 
                    if (y > h - 50) { 
                        c = new Color((int) (Math.random() * 256), (int) 
(Math.random() * 256), 
                                (int) (Math.random() * 256)); 
                        f = 1; 
                    } 
                    break; 
                case 1: 
                    y--; 
                    if (y < 0) { 
                        c = new Color((int) (Math.random() * 256), (int) 
(Math.random() * 256), 
                                (int) (Math.random() * 256)); 
                        f = 0; 
                    } 
            } 
            repaint(); 
            try { 
                Thread.sleep(10); 
            } catch (Exception e) { 
            } 
        } 
    } 
  
    public void paint(Graphics g) { 
        super.paint(g); 
        g.setColor(c); 
        g.fillOval(x, y, 20, 20); 
    } 
  
    public static void main(String args[]) { 
        new Slip3B(); 
    } 
} 
slip: 3 
 
Q.2 Dot Net Framework: 
A) Write a program in C# .Net to create a function for the sum of two numbers. 
namespace WinFormsApp18 
{ 
    public partial class Form1 : Form 
    { 
        public Form1() 
        { 
            InitializeComponent(); 
        } 
        public static int Sum(int a, int b) 
        { 
            return a + b; 
        } 
        private void button1_Click(object sender, EventArgs e){ 
               int a = Convert .ToInt32 (textBox1.Text); 
            int b = Convert .ToInt32 (textBox2.Text); 
            int c =  Sum (a, b); 
            label5.Text = c.ToString(); 
        } 
    } 
} 
 
 
 
B) Write a VB.NET program to create teacher table (Tid, TName, subject) Insert the 
 records (Max: 5). Search record of a teacher whose name is “Seeta” and display result. 
Imports System.Data.SqlClient 
Public Class Form1 
    Dim connection As SqlConnection 
 
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles 
MyBase.Load 
 
        connection = New SqlConnection("Data 
Source=(localdb)\v11.0;Initial Catalog=t26;Integrated 
Security=True") 
        MsgBox("conn succefully") 
        LoadData() 
    End Sub 
    Public Sub ExecuteQuery(query As String) 
        Dim command As New SqlCommand(query, connection) 
        connection.Open() 
        command.ExecuteNonQuery() 
        connection.Close() 
 
    End Sub 
Sub LoadData() 
        Dim da As New SqlDataAdapter("SELECT * FROM stud1", 
connection) 
        Dim dt As New DataTable() 
        da.Fill(dt) 
        DataGridView1.DataSource = dt 
    End Sub 
    Private Sub Button1_Click(sender As Object, e As EventArgs) 
Handles Button1.Click 
   Dim insertQuery As String = "INSERT INTO stud1 (rno,sname) 
VALUES("& TextBox1.Text &",'"&TextBox2.Text &"','"&textbox3.text 
&"')"         
        ExecuteQuery(insertQuery) 
        MessageBox.Show("Data Inserted succefully") 
    End Sub 
Private Sub Button5_Click(sender As Object, e As EventArgs) Handles 
Button5.Click 
   Dim da As New SqlDataAdapter( 
        "SELECT * FROM stud1 WHERE sname LIKE @sname", connection) 
        da.SelectCommand.Parameters.AddWithValue("@sname", "%" & 
TextBox2.Text & "%") 
        Dim dt As New DataTable() 
        da.Fill(dt) 
        DataGridView1.DataSource = dt 
    End Sub 
 
 
Imports System.Data.OleDb 
 Public Class Form1 
Dim con As New OleDbConnection("Provider=Microsoft.ACE.OLEDB.12.0;Data 
Source=C:\Users\Saurabh\Desktop\New folder\teacher.accdb") 
    Dim adpt As New OleDbDataAdapter("Select * from teacher", con) 
    Dim cmd As New OleDbCommand 
    Dim ds As New DataSet 
    Public Function display() 
        adpt.Fill(ds, "teacher") 
        DataGridView1.DataSource = ds 
        DataGridView1.DataMember = "teacher" 
        Return ds 
    End Function 
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load 
        display() 
    End Sub 
     Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
        cmd.Connection = con 
        cmd.CommandType = CommandType.Text 
        cmd.CommandText = "insert into teacher values(" & TextBox1.Text & ",'" & TextBox2.Text & "','" & 
TextBox3.Text & "')" 
        con.Open() 
  If cmd.ExecuteNonQuery() Then 
            MessageBox.Show("Inserted Successfully...!") 
        End If 
        con.Close() 
        ds.Clear() 
        display() 
    End Sub 
  
    Private Sub TextBox4_KeyDown(sender As Object, e As KeyEventArgs) Handles TextBox4.KeyDown 
        ds.Clear() 
        Dim adp As New OleDbDataAdapter("select * from teacher Where Name like '%" & TextBox4.Text & "%'", con) 
        adp.Fill(ds, "search") 
        DataGridView1.DataSource = ds 
        DataGridView1.DataMember = "search" 
    End Sub 
End Class 
slip: 4 
<asp:SqlDataSource ID="SqlDataSource1" runat="server" 
ConnectionString="<%$ ConnectionStrings:ConnectionString 
%>"  
SelectCommand="SELECT * FROM [dept1]"  
UpdateCommand="UPDATE[dept1] SET 
dname=@dname,ename=@ename,sal=@sal WHERE dept_id=@dept_id" 
DeleteCommand =" DELETE FROM[dept1] WHERE 
dept_id=@dept_id"> 
</asp:SqlDataSource> 
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Web; 
using System.Web.UI; 
using System.Web.UI.WebControls; 
using System.Data.SqlClient; 
using System.Configuration; 
public partial class _Default : System.Web.UI.Page 
{ 
SqlConnection con = new 
SqlConnection(ConfigurationManager.ConnectionStrings["Conn
ectionString"].ConnectionString );   
protected void Page_Load(object sender, EventArgs e) 
{ 
} 
protected void TextBox2_TextChanged(object sender, 
EventArgs e) 
{ 
} 
protected void Button1_Click(object sender, EventArgs 
e) 
{ 
con.Open(); 
//  string sql = "INSERT INTO 
[dept1](dept_id,dname,ename,sal)VALUES("+TextBox1.Text+",'
"+TextBox2 .Text +"','"+TextBox3 .Text 
+"',"+TextBox4.Text+")"; 
SqlCommand cmd = new SqlCommand("Insert into dept1 
values(@dept_id,@dname,@ename,@sal)",con); 
cmd.Parameters.AddWithValue("@dept_id", 
TextBox1.Text); 
cmd.Parameters.AddWithValue("@dname", 
TextBox2.Text); 
cmd.Parameters.AddWithValue("@ename", 
TextBox3.Text); 
cmd.Parameters.AddWithValue("@sal", 
TextBox4.Text); 
cmd.ExecuteNonQuery(); 
Response.Write("insert succefully"); 
con.Close(); 
GridView1.DataBind(); 
} 
protected void Button2_Click(object sender, EventArgs e) 
{ 
con.Open(); 
SqlCommand cmd = new SqlCommand("update dept1 set 
sal=sal+(sal*0.15) where ename=@ename ", con); 
cmd.Parameters.AddWithValue("@ename", 
TextBox3.Text); 
cmd.ExecuteNonQuery(); 
con.Close(); 
GridView1.DataBind(); 
} 
} 
Q.1. Advanced Java: 
A) Write a JSP program to calculate sum of first and last digit of a given number. 
Display sum in Red Color with font size 18. 
<%@page contentType="text/html" pageEncoding="UTF-8"%> 
<!DOCTYPE html> 
<html> 
<head> 
<title>Sum of First and Last Digits</title> 
</head> 
<body> 
<h2>Enter a Number:</h2> 
<form action="sum.jsp" method="post"> 
<input type="number" name="num" required> 
<input type="submit" value="Calculate"> 
</form> 
<% 
if(request.getParameter("num")!=null) { 
int num = Integer.parseInt(request.getParameter("num")); 
int lastDigit = num % 10; 
int firstDigit = num; 
while(firstDigit>=10) { 
firstDigit = firstDigit / 10; 
} 
int sum = firstDigit + lastDigit; 
%> 
<h2 style="color:red; font-size:18px;">Sum of First and Last Digits: <%=sum%></h2> 
    <% 
        } 
    %> 
</body> 
</html> 
 
 
 
B) Write a java program in multithreading using applet for Traffic signal. 
import java.awt.*; 
 public class Slip5B extends Frame  
{ 
     int f = 0; 
     public Slip5B() { 
        Signal s = new Signal(); 
        s.start(); 
        setSize(500, 500); 
        setVisible(true); 
    } 
  
    public void paint(Graphics g)  
{ 
        switch (f) { 
  
            case 0: 
                g.setColor(Color.red); 
                g.fillOval(60, 60, 50, 50); 
                g.setColor(Color.black); 
                g.fillOval(60, 120, 50, 50); 
                g.fillOval(60, 180, 50, 50); 
                break; 
  
            case 1: 
                g.setColor(Color.yellow); 
                g.fillOval(60, 120, 50, 50); 
                g.setColor(Color.black); 
                g.fillOval(60, 60, 50, 50); 
                g.fillOval(60, 180, 50, 50); 
                break; 
  
            case 2: 
                g.setColor(Color.green); 
                g.fillOval(60, 180, 50, 50); 
                g.setColor(Color.black); 
                g.fillOval(60, 120, 50, 50); 
                g.fillOval(60, 60, 50, 50); 
                break; 
        } 
    } 
  
    class Signal extends Thread { 
        public void run() { 
            while (true) { 
                f = (f + 1) % 3; 
                repaint(); 
                try { 
                    Thread.sleep(1000); 
                } catch (Exception e) { 
  
                } 
            } 
        } 
    } 
  
    public static void main(String args[]) { 
        new Slip5B(); 
    } 
} 
  
Q.2 Dot Net Framework: 
 A) Write a VB.NET program to accept a character from keyboard and check whether it 
 is vowel or consonant. Also display the case of that character. 
Public Class Form1 
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
        Dim a As Char 
        Dim str As String 
        a = TextBox1.Text 
  
        If (TextBox1.Text.Length <= 1) Then 
            If Char.IsUpper(a) Then 
                str = "Upper Case" 
            Else 
                str = "Lower Case" 
            End If 
            If (a = "a" Or a = "e" Or a = "i" Or a = "o" Or a = "u" Or 
                a = "A" Or a = "E" Or a = "I" Or a = "O" Or a = "U") Then 
                MessageBox.Show(TextBox1.Text & " is " & str & " Vowel") 
            Else 
                MessageBox.Show(TextBox1.Text & " is " & str & " Consonant") 
            End If 
        End If 
    End Sub 
  
    Private Sub TextBox1_Leave(sender As Object, e As EventArgs) Handles TextBox1.Leave 
        Dim a As String 
        a = TextBox1.Text 
        If (TextBox1.Text.Length > 1) Then 
            Label2.Text = "Only One Characters Allowed...!" 
        Else 
            Label2.Text = "" 
        End If 
  
    End Sub 
End Class 
  
B) Design a web application form in ASP.Net having loan amount, interest rate and 
duration fields. Calculate the simple interest and perform necessary validation i.e. 
Ensures data has been entered for each field. Checking for non-numeric value. Assume 
suitable web-form controls and perform necessary validation. 
Simple Interest Formula 
Where: 
 P = Loan Amount 
 R = Interest Rate (%) 
 T = Duration (Years) 
�
� Assumptions 
 ASP.NET Web Forms 
 Controls used: TextBox, Button, Label 
 Validation using: 
o RequiredFieldValidator 
o RegularExpressionValidator 
 Code-behind in C# 
�
� LoanForm.aspx 
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="LoanForm.aspx.cs" 
Inherits="LoanApp.LoanForm" %> 
<!DOCTYPE html> 
<html> 
<head runat="server"> 
<title>Loan Interest Calculator</title> 
</head> 
<body> 
<form id="form1" runat="server"> 
<h2>Loan Interest Calculator</h2> 
<!-- Loan Amount --> 
Loan Amount: 
<asp:TextBox ID="txtAmount" runat="server"></asp:TextBox> 
<asp:RequiredFieldValidator ID="rfvAmount" runat="server" 
ControlToValidate="txtAmount" 
ErrorMessage="Loan Amount is required" 
ForeColor="Red" /> 
<asp:RegularExpressionValidator ID="revAmount" runat="server" 
ControlToValidate="txtAmount" 
ErrorMessage="Enter numeric value only" 
ValidationExpression="^\d+(\.\d+)?$" 
ForeColor="Red" /> 
<br /><br /> 
<!-- Interest Rate --> 
Interest Rate (%): 
<asp:TextBox ID="txtRate" runat="server"></asp:TextBox> 
<asp:RequiredFieldValidator ID="rfvRate" runat="server" 
ControlToValidate="txtRate" 
ErrorMessage="Interest Rate is required" 
ForeColor="Red" /> 
<asp:RegularExpressionValidator ID="revRate" runat="server" 
ControlToValidate="txtRate" 
ErrorMessage="Enter numeric value only" 
ValidationExpression="^\d+(\.\d+)?$" 
ForeColor="Red" /> 
<br /><br /> 
<!-- Duration --> 
Duration (Years): 
<asp:TextBox ID="txtDuration" runat="server"></asp:TextBox> 
<asp:RequiredFieldValidator ID="rfvDuration" runat="server" 
ControlToValidate="txtDuration" 
ErrorMessage="Duration is required" 
ForeColor="Red" /> 
<asp:RegularExpressionValidator ID="revDuration" runat="server" 
ControlToValidate="txtDuration" 
ErrorMessage="Enter numeric value only" 
ValidationExpression="^\d+(\.\d+)?$" 
ForeColor="Red" /> 
<br /><br /> 
<!-- Button --> 
<asp:Button ID="btnCalculate" runat="server" 
Text="Calculate Interest" 
OnClick="btnCalculate_Click" /> 
<br /><br /> 
<!-- Result --> 
<asp:Label ID="lblResult" runat="server" 
ForeColor="Green"></asp:Label> 
</form> 
</body> 
</html> 
�
� LoanForm.aspx.cs (Code Behind) 
using System; 
namespace LoanApp 
{ 
public partial class LoanForm : System.Web.UI.Page 
{ 
protected void btnCalculate_Click(object sender, EventArgs e) 
{ 
if (Page.IsValid) 
{ 
double amount = Convert.ToDouble(txtAmount.Text); 
double rate = Convert.ToDouble(txtRate.Text); 
double duration = Convert.ToDouble(txtDuration.Text); 
double simpleInterest = (amount * rate * duration) / 100; 
lblResult.Text = "Simple Interest = " + 
simpleInterest.ToString("0.00"); 
} 
} 
} 
} 
Q.1. Advanced Java: 
Slip: 6 
A) Write a java program to blink image on the Frame continuously. 
import java.awt.*; 
import java.awt.event.WindowAdapter; 
import java.awt.event.WindowEvent; 
public class s6a extends Frame implements Runnable 
{ 
private Image i; 
private boolean isVisible=true; 
public s6a() 
{ 
setTitle("blink"); 
setSize(400,400); 
setLayout(null); 
setVisible(true); 
i=Toolkit.getDefaultToolkit().getImage("C:/Users/ADMIN/Desktop/.net practice pgm 25
2026/java pgm/single-inheritance.png"); 
Thread t =new Thread(this); 
t.start(); 
} 
public void paint(Graphics g) 
{ 
if(isVisible && i!= null) 
{ 
g.drawImage(i,100,100,200,200,this); 
} 
} 
public void run() 
{ 
while(true) 
{ 
try { 
isVisible=!isVisible; 
repaint(); 
Thread.sleep(500); 
} 
catch(InterruptedException e) 
{ 
System.out.println(e); 
} 
} 
} 
public static void main(String[] args) 
{ 
new s6a(); 
} 
} 
B) Write a SERVLET program which counts how many times a user has visited a web 
page. If user is visiting the page for the first time, display a welcome message. If the 
user is revisiting the page, display the number of times visited. (Use Cookie) 
 import java.io.*; 
import javax.servlet.*; 
import javax.servlet.http.*; 
 public class VisitCounterServlet extends HttpServlet { 
     public void doGet(HttpServletRequest request, HttpServletResponse response) 
            throws ServletException, IOException { 
        int visits = 0; 
        Cookie[] cookies = request.getCookies(); 
        if (cookies != null) { 
            for (Cookie cookie : cookies) { 
                if (cookie.getName().equals("visitCount")) { 
                    visits = Integer.parseInt(cookie.getValue()); 
                } 
            } 
        } 
        visits++; 
        Cookie visitCookie = new Cookie("visitCount", Integer.toString(visits)); 
        response.addCookie(visitCookie); 
        response.setContentType("text/html"); 
        PrintWriter out = response.getWriter(); 
        if (visits == 1) { 
            out.println("<html><head><title>Welcome</title></head><body>"); 
            out.println("<h2>Welcome to my website!</h2>"); 
            out.println("</body></html>"); 
        } else { 
            out.println("<html><head><title>Visit Count</title></head><body>"); 
            out.println("<h2>You have visited this website " + visits + " times.</h2>"); 
            out.println("</body></html>"); 
        } 
        out.close(); 
    } 
} 
Q.2Dot Net Framework: 
A) Write ASP.Net program that displays the names of some flowers in two columns. 
Bind a label to the RadioButtonList so that when the user selects an option from the list 
and clicks on a button, the label displays the flower selected by the user. 
protected void Button1_Click(object sender, EventArgs e) 
{ 
if (RadioButtonList1.SelectedItem != null) 
{ 
Label1.Text = "You selected: " + 
RadioButtonList1.SelectedItem.Text; 
} 
else 
{ 
} 
} 
Label1.Text = "Please select a flower."; 
ASP.NET Web Forms 
1
️⃣ Flowers.aspx 
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Flowers.aspx.cs" 
Inherits="Flowers" %> 
<!DOCTYPE html> 
<html> 
<head runat="server"> 
<title>Flower Selection</title> 
</head> 
<body> 
<form id="form1" runat="server"> 
<h3>Select a Flower</h3> 
<asp:RadioButtonList ID="rblFlowers" runat="server" 
RepeatColumns="2" 
RepeatDirection="Horizontal"> 
<asp:ListItem>Rose</asp:ListItem> 
<asp:ListItem>Lotus</asp:ListItem> 
<asp:ListItem>Jasmine</asp:ListItem> 
<asp:ListItem>Sunflower</asp:ListItem> 
<asp:ListItem>Lily</asp:ListItem> 
<asp:ListItem>Tulip</asp:ListItem> 
</asp:RadioButtonList> 
<br /> 
<asp:Button ID="btnSelect" runat="server" Text="Submit" 
OnClick="btnSelect_Click" /> 
<br /><br /> 
<asp:Label ID="lblResult" runat="server" 
Font-Bold="true" 
ForeColor="Green"> 
</asp:Label> 
</form> 
</body> 
</html> 
2
️⃣ Flowers.aspx.cs (Code Behind) 
using System; 
public partial class Flowers : System.Web.UI.Page 
{ 
protected void btnSelect_Click(object sender, EventArgs e) 
{ 
if (rblFlowers.SelectedItem != null) 
{ 
lblResult.Text = "You selected: " + 
rblFlowers.SelectedItem.Text; 
} 
else 
{ 
lblResult.Text = "Please select a flower."; 
} 
} 
} 
B) Write a VB.NET program to create movie table (Mv_Name, Release_year, 
Director). Insert the records (Max: 5). Delete the records of movies whose release year 
is 2022 and display appropriate message in message box. 
Imports System 
Imports System.Data 
Imports System.Data.OleDb 
Public Class Form1 
Dim con As New OleDbConnection("Provider=Microsoft.ACE.OLEDB.12.0;Data 
Source=C:\Users\Saurabh\Desktop\New folder\movie.accdb") 
Dim adpt As New OleDbDataAdapter("Select * from movie", con) 
    Dim cmd As New OleDbCommand 
    Dim ds As New DataSet 
    Public Function display() 
        adpt.Fill(ds, "movie") 
        DataGridView1.DataSource = ds 
        DataGridView1.DataMember = "movie" 
        Return ds 
    End Function 
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load 
        display() 
    End Sub 
  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
        cmd.Connection = con 
        cmd.CommandType = CommandType.Text 
        cmd.CommandText = "insert into movie values('" & TextBox1.Text & "'," & TextBox2.Text & ",'" & 
TextBox3.Text & "')" 
        con.Open() 
 If cmd.ExecuteNonQuery() Then 
            MessageBox.Show("Inserted Successfully...!") 
        End If 
  
        con.Close() 
        ds.Clear() 
        display() 
    End Sub 
  
    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click 
        cmd.Connection = con 
        cmd.CommandType = CommandType.Text 
cmd.CommandText = "DELETE FROM movie WHERE Release_year = " & TextBox2.Text 
con.Open() 
If cmd.ExecuteNonQuery() Then 
MessageBox.Show("Deleted Successfully...!") 
End If 
con.Close() 
ds.Clear() 
display() 
End Sub 
End Class 
Slip: 7 
Q.1. Advanced Java: 
A) Write a JSP script to validate given E-Mail ID. 
<%@ page language="java" %> 
<% 
String email = request.getParameter("email"); // retrieve email from form data 
String regex = "^[\\w-\\.]+@([\\w-]+\\.)+[\\w-]{2,4}$"; // regular expression for email 
validation 
if (email.matches(regex)) { 
out.println("Valid email address"); // if email matches the regex, print "Valid email 
address" 
} else { 
out.println("Invalid email address"); // if email does not match the regex, print "Invalid 
email address" 
} 
%> 
B) Write a Multithreading program in java to display the number’s between 1 to 100 
continuously in a TextField by clicking on button. (use Runnable Interface). 
//slip 7  
import java.awt.*; 
import java.awt.event.*; 
class slip7b extends Frame implements ActionListener,Runnable 
{ 
TextField t =new TextField(10); 
Button b =new Button("start"); 
Thread th; 
slip7b() 
{ 
setLayout(new FlowLayout()); 
add(t); 
add(b); 
b.addActionListener(this); 
setSize(200,200); 
setVisible(true); 
} 
public void actionPerformed(ActionEvent e) 
{ 
th=new Thread(this); 
th.start(); 
} 
public void run() 
{ 
try 
{ 
for(int i=1;i<=100;i++) 
{ 
t.setText(String.valueOf(i)); 
Thread.sleep(100); 
} 
} 
catch(Exception e) 
{} 
} 
public static void main(String args[]) 
{ 
new slip7b(); 
} 
} 
Q.2 Dot Net Framework: 
A) Write a ASP.Net program to accept a number from the user in a textbox control and 
throw an exception if the number is not a perfect number. Assume suitable controls on 
the web form. 
PerfectNumber.aspx 
<%@ Page Language="C#" AutoEventWireup="true" 
CodeBehind="PerfectNumber.aspx.cs" 
Inherits="NumberApp.PerfectNumber" %> 
<!DOCTYPE html> 
<html> 
<head runat="server"> 
<title>Perfect Number Check</title> 
</head> 
<body> 
<form id="form1" runat="server"> 
<h2>Perfect Number Checker</h2> 
Enter a Number: 
<asp:TextBox ID="txtNumber" runat="server"></asp:TextBox> 
<br /><br /> 
<asp:Button ID="btnCheck" runat="server" 
Text="Check Perfect Number" 
OnClick="btnCheck_Click" /> 
<br /><br /> 
<asp:Label ID="lblResult" runat="server" 
ForeColor="Red" 
Font-Bold="true"></asp:Label> 
</form> 
</body> 
</html> 
 
�
� PerfectNumber.aspx.cs (Code Behind) 
using System; 
 
namespace NumberApp 
{ 
    public partial class PerfectNumber : System.Web.UI.Page 
    { 
        protected void btnCheck_Click(object sender, EventArgs e) 
        { 
            try 
            { 
                int num = Convert.ToInt32(txtNumber.Text); 
                int sum = 0; 
 
                for (int i = 1; i <= num / 2; i++) 
                { 
                    if (num % i == 0) 
                    { 
                        sum += i; 
                    } 
                } 
 
                if (sum != num) 
                { 
                    throw new Exception("The number is not a perfect 
number."); 
                } 
 
                lblResult.ForeColor = System.Drawing.Color.Green; 
                lblResult.Text = num + " is a Perfect Number."; 
            } 
            catch (FormatException) 
            { 
                lblResult.Text = "Please enter a valid numeric value."; 
            } 
            catch (Exception ex) 
            { 
                lblResult.Text = ex.Message; 
            } 
        } 
    } 
} 
 
 
 
 
 
 
public partial class _Default : Page 
{ 
protected void Page_Load(object sender, EventArgs e) 
{ 
} 
protected void Button1_Click(object sender, EventArgs 
e) 
{ 
try 
{ 
int num = Convert.ToInt32(TextBox1.Text); 
int sum = 0; 
for (int i = 1; i <= num / 2; i++) 
{ 
if (num % i == 0) 
{ 
sum += i; 
} 
} 
if (sum != num) 
{ 
throw new Exception("The number is not a 
perfect number."); 
} 
Label1.ForeColor = System.Drawing.Color.Green; 
Label1.Text = num + " is a Perfect Number."; 
} 
catch (FormatException) 
{ 
Label1.Text = "Please enter a valid numeric 
value."; 
} 
} 
} 
catch (Exception ex) 
{ 
Label1.Text = ex.Message; 
} 
B) Write a VB.NET program to create a table student (Roll No, SName, Class,City). 
Insert the records (Max: 5). Update city of students to ‘Pune’ whose city is ‘Mumbai’ 
and display updated records in GridView. 
Slip: 8 
Q.1. Advanced Java: 
A) Write a Java Program to display all the employee names whose initial character of a 
name is ‘A’. 
Answer : 
import java.io.*; 
import java.sql.*; 
  
class Slip8A { 
    public static void main(String args[]) throws Exception { 
  
        Statement stmt; 
        ResultSet rs; 
  
        Class.forName("com.mysql.jdbc.Driver"); 
  
        Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3
306/bcadb", "root", ""); 
  
        stmt = con.createStatement(); 
        rs = stmt.executeQuery("select ename from emp where ename like 'A%'"); 
        System.out.println("<<<<Employee Name>>>>>"); 
        System.out.println("=================="); 
  
        while (rs.next()) { 
            System.out.println(rs.getString(1)); 
        } 
        con.close(); 
    } 
} 
  
B) Write a java program in multithreading using applet for Digital watch. 
Answer : 
import java.applet.*; 
import java.awt.*; 
import java.util.*; 
import java.text.*; 
  
public class Slip8B extends Applet implements Runnable { 
    Thread t; 
    String str; 
  
    public void start() { 
        t = new Thread(this); 
        t.start(); 
    } 
  
    public void run() { 
        try { 
            while (true) { 
                Date date = new Date(); 
                SimpleDateFormat Nowtime = new SimpleDateFormat("hh:mm:ss"); 
                str = Nowtime.format(date); 
                repaint(); 
                t.sleep(1000); 
            } 
        } catch (Exception e) { 
        } 
    } 
public void paint(Graphics g) { 
g.drawString(str, 120, 100); 
} 
} 
/* 
* <applet code="Slip8B.class" width="300" height="300"> 
* </applet> 
*/ 
Slip: 8 
Q.2 Dot Net Framework: 
A) List of employees is available in listbox. Write ASP.Net application to add 
selected or all records from listbox to Textbox (assume multi-line property of textbox is 
true). 
 Employees listed in a ListBox 
 Multiple selection enabled 
 Add selected records OR all records 
 Display in a multi-line TextBox 
1⃣ Employees.aspx 
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Employees.aspx.cs" 
Inherits="Employees" %> 
<!DOCTYPE html> 
<html> 
<head runat="server"> 
<title>Employee List</title> 
</head> 
<body> 
<form id="form1" runat="server"> 
<h3>Employee List</h3> 
 
        <asp:ListBox ID="lstEmployees" runat="server" 
            SelectionMode="Multiple" 
            Height="120px"> 
            <asp:ListItem>Rahul</asp:ListItem> 
            <asp:ListItem>Amit</asp:ListItem> 
            <asp:ListItem>Neha</asp:ListItem> 
            <asp:ListItem>Pooja</asp:ListItem> 
            <asp:ListItem>Vikas</asp:ListItem> 
        </asp:ListBox> 
 
        <br /><br /> 
 
        <asp:Button ID="btnSelected" runat="server" 
            Text="Add Selected" 
            OnClick="btnSelected_Click" /> 
 
        <asp:Button ID="btnAll" runat="server" 
            Text="Add All" 
            OnClick="btnAll_Click" /> 
 
        <br /><br /> 
 
        <asp:TextBox ID="txtEmployees" runat="server" 
            TextMode="MultiLine" 
            Rows="6" 
            Columns="30"> 
        </asp:TextBox> 
 
    </form> 
</body> 
</html> 
 
2️⃣ Employees.aspx.cs (Code Behind) 
using System; 
 
public partial class Employees : System.Web.UI.Page 
{ 
    protected void btnSelected_Click(object sender, EventArgs e) 
    { 
        txtEmployees.Text = ""; 
 
        foreach (var item in lstEmployees.Items) 
        { 
            if (((System.Web.UI.WebControls.ListItem)item).Selected) 
            { 
                txtEmployees.Text += 
((System.Web.UI.WebControls.ListItem)item).Text + Environment.NewLine; 
            } 
        } 
    } 
 
    protected void btnAll_Click(object sender, EventArgs e) 
    { 
        txtEmployees.Text = ""; 
 
        foreach (var item in lstEmployees.Items) 
        { 
            txtEmployees.Text += 
((System.Web.UI.WebControls.ListItem)item).Text + Environment.NewLine; 
        } 
} 
} 
�
� How It Works 
 Add Selected → Copies only selected employees 
 Add All → Copies all employees 
 TextBox shows each name on a new line 
✍ Exam Tip (1–2 Lines) 
ListBox with SelectionMode="Multiple" allows selecting multiple items. Selected or all 
items are iterated and added to a multi-line TextBox using Environment.NewLine. 
If you want: 
B) Write a c#.Net program for multiplication of matrices. 
Matrix Multiplication 
using System; 
class MatrixMultiplication 
{ 
static void Main() 
{ 
int i, j, k; 
int[,] a = new int[3, 3]; 
int[,] b = new int[3, 3]; 
int[,] c = new int[3, 3]; 
Console.WriteLine("Enter elements of Matrix A (3x3):"); 
for (i = 0; i < 3; i++) 
{ 
for (j = 0; j < 3; j++) 
{ 
a[i, j] = Convert.ToInt32(Console.ReadLine()); 
} 
} 
Console.WriteLine("Enter elements of Matrix B (3x3):"); 
for (i = 0; i < 3; i++) 
{ 
for (j = 0; j < 3; j++) 
{ 
b[i, j] = Convert.ToInt32(Console.ReadLine()); 
} 
} 
// Matrix Multiplication 
for (i = 0; i < 3; i++) 
{ 
for (j = 0; j < 3; j++) 
{ 
c[i, j] = 0; 
for (k = 0; k < 3; k++) 
{ 
c[i, j] += a[i, k] * b[k, j]; 
} 
} 
} 
Console.WriteLine("Resultant Matrix (A x B):"); 
for (i = 0; i < 3; i++) 
{ 
for (j = 0; j < 3; j++) 
{ 
Console.Write(c[i, j] + "\t"); 
} 
Console.WriteLine(); 
} 
Console.ReadLine(); 
} 
} 
Slip: 11 
) Write a java program to display IPAddress and name of client machine. 
Answer : 
import java.net.InetAddress; 
public class ClientMachineInfo { 
public static void main(String[] args) { 
try { 
InetAddress clientAddr = InetAddress.getLocalHost(); 
System.out.println("IP address of client machine: " + 
clientAddr.getHostAddress()); 
System.out.println("Name of client machine: " + 
clientAddr.getHostName()); 
} catch (Exception e) { 
            System.out.println("Error while getting client machine info: " + 
e.getMessage()); 
        } 
    } 
} 
 
Output : 
  
B) Write a Java program to display sales details of Product (PID, PName, Qty, Rate, 
Amount) between two selected dates. (Assume Sales table is already created). 
Answer : 
import java.sql.*; 
import java.util.Scanner; 
 
public class ProductSalesDetails { 
    public static void main(String[] args) { 
        Scanner sc = new Scanner(System.in); 
         
        // Prompt user to enter start and end dates 
        System.out.print("Enter start date (YYYY-MM-DD): "); 
        String startDate = sc.next(); 
        System.out.print("Enter end date (YYYY-MM-DD): "); 
        String endDate = sc.next(); 
 
        // Define database connection variables 
        String url = "jdbc:mysql://localhost:3306/mydatabase"; 
        String user = "root"; 
        String password = "password"; 
 
        // Define SQL query to fetch sales details of product between two 
dates 
        String query = "SELECT PID, PName, Qty, Rate, Amount FROM Sales WHERE 
SaleDate BETWEEN ? AND ?"; 
 
        try { 
            // Establish database connection 
            Connection conn = DriverManager.getConnection(url, user, 
password); 
 
            // Prepare SQL statement with parameters for start and end dates 
            PreparedStatement pstmt = conn.prepareStatement(query); 
            pstmt.setString(1, startDate); 
            pstmt.setString(2, endDate); 
 
            // Execute the SQL statement and get the result set 
            ResultSet rs = pstmt.executeQuery(); 
 
            // Display the sales details in tabular form 
            System.out.println("PID\tPName\tQty\tRate\tAmount"); 
            System.out.println("-------------------------------------------------"); 
            while (rs.next()) { 
                int pid = rs.getInt("PID"); 
                String pname = rs.getString("PName"); 
                int qty = rs.getInt("Qty"); 
                double rate = rs.getDouble("Rate"); 
                double amount = rs.getDouble("Amount"); 
                System.out.println(pid + "\t" + pname + "\t" + qty + "\t" + 
rate + "\t" + amount); 
            } 
 
            // Close the database connection 
            conn.close(); 
 
        } catch (SQLException e) { 
            e.printStackTrace(); 
        } 
    } 
} 
 
 
Q.2 Dot Net Framework: 
A) Write a ASP.Net program that gets user input such as the user name, mode of 
payment, appropriate credit card. After the user enters the appropriate values the 
Validation button validates the values entered. 
 
 User Name 
 Mode of Payment 
 Credit Card Number 
 Uses ASP.NET validation controls 
 A Validate button to check entered values 
 
1⃣ Payment.aspx 
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Payment.aspx.cs" 
Inherits="Payment" %> 
 
<!DOCTYPE html> 
<html> 
<head runat="server"> 
    <title>Payment Validation</title> 
</head> 
<body> 
    <form id="form1" runat="server"> 
 
        <h3>Payment Details</h3> 
 
        User Name: 
        <asp:TextBox ID="txtUserName" runat="server"></asp:TextBox> 
        <asp:RequiredFieldValidator ID="rfvName" runat="server" 
            ControlToValidate="txtUserName" 
            ErrorMessage="* Enter User Name" 
            ForeColor="Red" /> 
        <br /><br /> 
 
        Mode of Payment: 
        <asp:RadioButtonList ID="rblPayment" runat="server"> 
            <asp:ListItem>Credit Card</asp:ListItem> 
            <asp:ListItem>Debit Card</asp:ListItem> 
            <asp:ListItem>Net Banking</asp:ListItem> 
        </asp:RadioButtonList> 
        <asp:RequiredFieldValidator ID="rfvPayment" runat="server" 
            ControlToValidate="rblPayment" 
            InitialValue="" 
            ErrorMessage="* Select Payment Mode" 
            ForeColor="Red" /> 
        <br /> 
 
        Credit Card Number: 
        <asp:TextBox ID="txtCard" runat="server"></asp:TextBox> 
        <asp:RequiredFieldValidator ID="rfvCard" runat="server" 
            ControlToValidate="txtCard" 
            ErrorMessage="* Enter Card Number" 
            ForeColor="Red" /> 
        <asp:RegularExpressionValidator ID="revCard" runat="server" 
            ControlToValidate="txtCard" 
            ValidationExpression="\d{16}" 
            ErrorMessage="* Enter 16 digit card number" 
            ForeColor="Red" /> 
        <br /><br /> 
 
        <asp:Button ID="btnValidate" runat="server" 
            Text="Validate" 
            OnClick="btnValidate_Click" /> 
 
        <br /><br /> 
 
        <asp:Label ID="lblResult" runat="server" 
            Font-Bold="true" 
            ForeColor="Green"> 
        </asp:Label> 
 
    </form> 
</body> 
</html> 
 
2️⃣ Payment.aspx.cs (Code Behind) 
using System; 
 
public partial class Payment : System.Web.UI.Page 
{ 
protected void btnValidate_Click(object sender, EventArgs e) 
{ 
if (Page.IsValid) 
{ 
lblResult.Text = "Validation Successful!"; 
} 
} 
} 
✅ Validations Used 
 RequiredFieldValidator → User Name 
 RequiredFieldValidator → Payment Mode 
 RegularExpressionValidator → 16-digit Credit Card 
 Page.IsValid → Final validation check 
�
� How It Works 
 User enters details 
 Clicks Validate 
 If all inputs are correct → success message 
 Errors are shown instantly near controls 
✔ Concept Used 
 Base class: Fruit 
 Derived classes: Apples, Mangoes 
 Calculate individual fruit counts 
 Display total number of fruits 
B) Write C# program to make a class named Fruit with a data member to calculate the 
number of fruits in a basket. Create two other class named Apples and Mangoes to 
calculate the number of apples and mangoes in the basket. Display total number of 
fruits in the basket. 
�
�🧩 C# Program – Fruit Basket 
using System; 
// Base class 
class Fruit 
{ 
protected int totalFruits; 
    public int GetTotalFruits() 
    { 
        return totalFruits; 
    } 
} 
 
// Derived class for Apples 
class Apples : Fruit 
{ 
    private int apples; 
 
    public Apples(int count) 
    { 
        apples = count; 
    } 
 
    public int GetApples() 
    { 
        return apples; 
    } 
} 
 
// Derived class for Mangoes 
class Mangoes : Fruit 
{ 
    private int mangoes; 
 
    public Mangoes(int count) 
    { 
        mangoes = count; 
    } 
 
    public int GetMangoes() 
    { 
        return mangoes; 
    } 
} 
 
class Program 
{ 
    static void Main() 
    { 
        Apples a = new Apples(10); 
        Mangoes m = new Mangoes(15); 
 
        int total = a.GetApples() + m.GetMangoes(); 
 
        Console.WriteLine("Number of Apples  : " + a.GetApples()); 
        Console.WriteLine("Number of Mangoes: " + m.GetMangoes()); 
        Console.WriteLine("Total Fruits     : " + total); 
 
        Console.ReadLine(); 
    } 
} 
 
�
� Sample Output 
Number of Apples  : 10 
Number of Mangoes: 15 
Total Fruits     : 25 
 
 
 
 
Slip: 30 
Q.1. Advanced Java: 
A) Write a JSP script to accept a String from a user and display it in reverse order. 
 
<%@ page language="java" %> 
<html> 
<head> 
  <title>Reverse String Example</title> 
</head> 
<body> 
  <h1>Reverse String Example</h1> 
 
  <form method="post"> 
    Enter a String: <input type="text" name="inputString"><br><br> 
    <input type="submit" value="Reverse"> 
  </form> 
 
  <br><br> 
 
  <% 
    String inputString = request.getParameter("inputString"); 
    if (inputString != null && !inputString.isEmpty()) { 
      String reversedString = new 
StringBuilder(inputString).reverse().toString(); 
      out.println("Original String: " + inputString + "<br>"); 
      out.println("Reversed String: " + reversedString); 
    } 
  %> 
 
</body> 
</html> 
 
 
 
 
 
 
 
 
 
 
B) Write a java program in multithreading using applet for moving car. 
import java.applet.Applet; 
import java.awt.*; 
 public class Slip30B extends Applet implements Runnable { 
    int x, z; 
    Thread t; 
    Image pic; 
  
    public void init() { 
        x = 50; 
        pic = getImage(getDocumentBase(), "./car.png"); 
        t = new Thread(this); 
        t.start(); 
    } 
  
    public void run() { 
  
        while (true) { 
            repaint(); 
            x = x + 10; 
            if (x >= this.getWidth()) { 
                System.exit(0); 
            } 
            try { 
                Thread.sleep(100); 
            } catch (Exception e) { 
            } 
        } 
    } 
  
    public void paint(Graphics g) { 
        g.drawLine(0, 165, this.getWidth(), 165); 
        g.drawImage(pic, x, 120, this); 
    } 
} 
/* 
* <applet code="Slip30B.java" width="800" height="500"> 
* </applet> 
*/ 
A) Write a VB.NET program to design following screen, accept the details from the user. Clicking 
on Submit button Net Salary should be calculated and displayed into the Textbox. Display the 
Messagebox informing the Name and Net Salary of employee. 
Answer : 
Public Class Form1 
Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
Label10.Text = (Int(TextBox2.Text) + Int(TextBox3.Text) + Int(TextBox4.Text) + Int(TextBox5.Text) + 
Int(TextBox6.Text) + Int(TextBox7.Text) + Int(TextBox8.Text)) 
Label12.Text = Int(TextBox6.Text) + Int(TextBox7.Text) + Int(TextBox8.Text) 
Label14.Text = Label10.Text - Label12.Text 
MessageBox.Show("Employee Name : " & TextBox1.Text &  "Total Salary is : " & Label14.Text) 
End Sub 
Private Sub TextBox2_Leave(sender As Object, e As EventArgs) Handles TextBox2.Leave 
TextBox3.Text = (TextBox2.Text * 31) / 100 
TextBox4.Text = (TextBox2.Text * 9) / 100 
End Sub 
End Class 
B) Write a VB.NET program to accept the details Supplier (SupId, SupName, Phone 
No, Address) store it into the database and display it. 
Answer : 
Imports System.Data.OleDb 
Public Class Form1 
Dim con As New OleDbConnection("Provider=Microsoft.ACE.OLEDB.12.0;Data 
Source=C:\Users\Saurabh\Desktop\New folder\Supplier.accdb") 
Dim adpt As New OleDbDataAdapter("Select * from Supplier", con) 
Dim cmd As New OleDbCommand 
Dim ds As New DataSet 
Public Function display() 
adpt.Fill(ds, "Supplier") 
DataGridView1.DataSource = ds 
DataGridView1.DataMember = "Supplier" 
Return ds 
End Function 
Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load 
display() 
End Sub 
Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click 
cmd.Connection = con 
cmd.CommandType = CommandType.Text 
cmd.CommandText = "insert into Supplier values(" & TextBox1.Text & ",'" & TextBox2.Text & "'," & 
TextBox3.Text & ",'" & TextBox4.Text & "')" 
con.Open() 
If cmd.ExecuteNonQuery() Then 
MessageBox.Show("Inserted Successfully...!") 
End If 
con.Close() 
ds.Clear() 
display() 
End Sub 
End Class 
Output : 
