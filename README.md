Node & cpp  Practical Slips Solution
Slip 1) 
1
Slip1a)
#include<iostream.h>
inline int max(int a, int b) {
   return ((a > b) ? a : b);
}
inline int min(int a, int b) {
    return ((a < b) ? a : b);
}

int main() {
    int a, b;
    cout << "Enter 2 numbers" << endl;
    cout << "Number 1: ";
    cin >> a;
    cout << "Number 2: ";
    cin >> b;
    cout << "The maximum number is: " << max(a, b) << endl;
    cout << "The minimum number is: " << min(a, b) << endl;
    return 0;
}


Slip 1 b)
1

/*In this code we will create 2 text file */
 /*lmn.txt*/
Hiii
 /*xyz.txt*/
Good Morning
 
#include<iostream.h>
#include<stdlib.h>
#include<conio.h>
#include<ctype.h>
#include<fstream.h>
 #include<string.h>
#define MAXSIZE (10)
 
class myfile
{
    FILE *fp; //file pointer
    char fn[MAXSIZE]; //file name
 
    public:
       myfile(const char* fname)
       {
         strcpy(fn,fname);
       }
       myfile operator+(myfile);
       void operator!();
       void display();
};
 
void myfile::display()
{
    fp =fopen(fn, "r"); //open file in read mode
    char ch;
    while((ch=fgetc(fp))!=EOF) // read until end of file reached
    {
        cout<<ch;
    }
    fclose(fp);//close the file after reading
}
 
void myfile::operator!()
{
    myfile f4("sy.txt"); //create object for another file
    char ch;
    fp=fopen(fn,"r");  //open source file in read mode
    f4.fp=fopen(f4.fn, "w"); //open destination file in write mode
    while((ch=fgetc(fp))!=EOF){
        if(isupper(ch)){
            fputc(tolower(ch),f4.fp) ; //convert  upper to lower case and write into desi. file
        }
        else if(islower(ch)){
            fputc(toupper(ch),f4.fp); //convert lower to upper
        }
        else{
            fputc(ch,f4.fp); //write  other  characters as it is
        }
    }
    fclose(fp);//close both file
    fclose(f4.fp);
    remove("abc.txt");
    rename("sy.txt","abc.txt");
}
myfile myfile::operator+(myfile f2)
{
   myfile f3("abc.txt");
   fp=fopen(fn,"r");
   f2.fp=fopen(f2.fn, "r");
   f3.fp=fopen(f3.fn,"w");
   char ch;
   while((ch=fgetc(fp))!=EOF)
   {
     fputc(ch,f3.fp);
   }
   fclose(fp);
   while((ch=fgetc(f2.fp))!=EOF)
   {
     fputc(ch,f3.fp);
   }
 
   return f3;
}
 
int main()
{
 
    myfile f1("xyz.txt");
    myfile f2("lmn.txt");
    myfile f3("abc.txt");
    clrscr();
    cout<<"first file\n";
    f1.display();
    cout<<"\nsecond file\n";
    f2.display();
 
    f3=f1+f2;
    cout<<"\nAfter concatnation file is:";
    f3.display();
    cout<<"\nAfter changes case\n";
    !f3;
    f3.display();
    getch();
    return 0;
}

1

Q.2) a.
var http = require('http');
var str = "hello world";
http.createServer(function (req, res) 
{
res.writeHead(200, {'Content-Type': 'text/html'});
res.write(str.toUpperCase());
res.end();
}).listen(8083);
console.log('server running');

Q.2 b)
db.js
var mysql = require('mysql');
var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345"
});
con.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
  con.query("CREATE DATABASE studentdb", function (err, result) {
    if (err) throw err;
    console.log("Database created");
  });
});

stable.js
var mysql = require('mysql');

var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345",
  database: "stud123"
});

con.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
  var sql = "CREATE TABLE c1(name VARCHAR(255), address VARCHAR(255))";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Table created");
  });
});

1
Slip2a:

#include<iostream.h>
#include<conio.h>
#include<math.h>
 

float volume(int r,int h)
{
    return(3.14*r*r*h);
}
 
float volume(float r,float h)
{
    return(3.14*r*r*h/3);
}
 
float volume(float r)
{
    return(0.33*3.14*r*r*r);
}


int main()
{
int cylinder_h,cylinder_r,cone_h,cone_r;
float sphere_r;
clrscr();
cout<<"Enter Dimension"<<endl;
cout<<"1. Cylinder"<<endl;
cout<<"Height : ";
cin>>cylinder_h;
cout<<"Radius : ";
cin>>cylinder_r;
cout<<endl;
 
cout<<"2. Cone"<<endl;
cout<<"Height : ";
cin>>cone_h;
cout<<"Radius : ";
cin>>cone_r;
cout<<endl;
 
cout<<"3. Sphere"<<endl;
cout<<"Radius : ";
cin>>sphere_r;
cout<<endl;
 
cout<<"\n\nThe Volume of Cylinder is : "<<volume(cylinder_r,cylinder_h)<<endl;
cout<<"The Volume of Cone is : "<<volume(cone_r,cone_h)<<endl;
cout<<"The Volumer of Sphere is : "<<volume(sphere_r)<<endl;
getch();
return 0;
}
 
 
 
Slip 2 b


2.Write a C++ program to create a class Movie with data members M Name, Release Year, Director Name and Budget. (Use File Handling) 
Write necessary member functions to: 
Accept details for ‘n’ Movies from user and store it in a file “Movie.txt . 
ii.Display Movie details from a file. 
iii. Count the number of objects stored in a file. [25 }Marks]

/* Create movie.txt file for storing movie details*/
 
#include<iostream.h>
#include<conio.h>
#include<fstream.h>
 
class movie
{
    public:
        int year;
        char mname[20];
        char dname[20];
        int budget;
    public:
        void accept()
        {
            cout<<"\n\nEnter Movie Name : ";
            cin>>mname;
            cout<<"Enter Release Year : ";
            cin>>year;
            cout<<"Enter Director Name : ";
            cin>>dname;
            cout<<"Enter Budget : ";
            cin>>budget;
        }
 
        void display()
        {
            cout<<"\n\nThe Movie Name : "<<mname<<endl;
            cout<<"The Release Year : "<<year<<endl;
            cout<<"The Director Name : "<<dname<<endl;
            cout<<"The Budget : "<<budget<<endl;
        }
};
 
 
void main()
{
movie m[5];
int n,i;
clrscr();
fstream file;
file.open("movie.txt",ios::in | ios::out);
 
cout<<"\nEnter the no of records you want to accept : ";
cin>>n;
for(i=0;i<n;i++)
{
m[i].accept();
file.write((char *) &m[i],sizeof(m[i]));
}
cout<<"\nDetils of movie from file :\n ";
for(i=0;i<n;i++)
{
file.read((char *) &m[i],sizeof(m[i]));
m[i].display();
}
file.close();
getch();
}


1

a)

fact.js

var fact={  

    factorial: function(n)
  
  {
  
      var f=1,i;
  
    for(i=1;i<=n;i++)
  
     {     f=f*i;
  
     }
  
    console.log('factorial of '+n+' is:'+f);}};
  
   module.exports=fact

Factdemo.js

var mymod=require('./fact.js');
mymod.factorial(5);


b) 

// employee.js

const readline = require('readline');

const rl = readline.createInterface({

input: process.stdin,

output: process.stdout

});

 function registerEmployee() {

rl.question('Enter employee name: ', (name) => {

rl.question('Enter Date of Birth (YYYY-MM-DD): ', (dob) => {

rl.question('Enter Joining Date (YYYY-MM-DD): ', (joiningDate) => {

rl.question('Enter Salary: ', (salary) => {

if (!isValidDate(dob) || !isValidDate(joiningDate) || !isValidSalary(salary)) {

console.log('Invalid input. Please try again.');

rl.close();

return;

}

// Display employee details

console.log('\nEmployee Details:');
//console.log(`Name: ${name}`);

console.log(`Name: ${name}`);

console.log(`Date of Birth: ${dob}`);

console.log(`Joining Date: ${joiningDate}`);

console.log(`Salary: ${salary}`);

 
rl.close();

});

});

});

});

}

function isValidDate(dateString) {

return /^\d{4}-\d{2}-\d{2}$/.test(dateString);

}
 
function isValidSalary(salary) {

return /^\d+$/.test(salary) && parseInt(salary) > 0;

}
 
// Start the employee registration process

registerEmployee();


Slip3:

1



Slip3a:

#include<iostream> 
using namespace std; 
void swap(int * x, int * y) 
{ 
int swap; 
swap = *x; 
*x = *y; 
*y=swap; 
} 
int main() 
{ 
int x=500, y=100; 
swap(&x, &y); // passing reference to function 
cout<<"Value of x is: "<<x<<endl; 
cout<<"Value of y is: "<<y<<endl; 
return 0; 
} 


Slip3 b)


2.Write a C++ program to accept ‘n’ numbers from user through Command Line Argument. Store all Even and Odd numbers in file “Even.txt” and “Odd.txt” respectively. [25 Marks]


/*In this program we will create also 2 text file like odd.txt for storing odd numbers and even.txt for storing even numbers*/
 
#include<stdlib.h>
#include<iostream.h>
#include<conio.h>
#include<fstream.h>
 
 
void main()
{
ofstream out;
int a[10]={1,2,3,4,5,6,7,8,9},b[10],i;
clrscr();
out.open("input.txt");
out.write((char *)&a,sizeof(a));
out.close();
ifstream in;
ofstream fp1,fp2;
in.open("input.txt");
in.read((char *)&b,sizeof(b));
fp1.open("even.txt");
fp2.open("odd.txt");
for(i=0;i<10;i++)
{
if(b[i]%2==0)
{
fp1<<b[i]<<"";
}
else
{
fp2<<b[i]<<"";
}
}
 
in.close();
fp1.close();
fp2.close();
ifstream fp;
char ch;
fp.open("even.txt");
cout<<"The even file contents are :\n ";
while(fp)
{
fp.get(ch);
cout<<"\t"<<ch;
}
fp.close();
fp.open("odd.txt");
cout<<"\n\nThe odd file contents are :\n ";
while(fp)
{
fp.get(ch);
cout<<"\t"<<ch;
}
fp.close();
 
getch();
}

1


a)

circle.js
var circle={  

    area: function(r)
  
  {
  
      var pi=3.14,a;  
  
       a=pi*r*r;
  
    
  
    console.log('area of circle is:'+a);
  
  },
  
  circumference: function(r)
  
  {
  
      var pi=3.14,c;
  
    c=2*pi*r;
  
    console.log('circumference of circle is:'+c);
  
  }
  
  };
  
   module.exports=circle;

cdemo.js

var mymod=require('./circle.js');

mymod.area(5);

mymod.circumference(5);


b)

 studentRegistration.js


const readline = require('readline');

const rl = readline.createInterface({

input: process.stdin,

output: process.stdout

});

 

// Function to validate student registration form

function validateStudentForm() {

rl.question('Enter student name: ', (name) => {

rl.question('Enter age: ', (age) => {

rl.question('Enter email: ', (email) => {

if (isValidAge(age) && isValidEmail(email)) {

 // Display success message

console.log('\nStudent Registration Successful!');

console.log(`Name: ${name}`);

console.log(`Age: ${age}`);

console.log(`Email: ${email}`);

 

rl.close();

}

else {

console.log('Invalid input. Please check your age and email format.');

rl.close();

}

});

});

});

}

 

// Function to validate age (must be a positive integer)

function isValidAge(age) {

return /^\d+$/.test(age) && parseInt(age) > 0;

}

 

// Function to validate email format

function isValidEmail(email) {

const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

return emailRegex.test(email);

}

 

// Start the student registration form validation process

validateStudentForm();

Slip4

1

Slip4a:
#include<iostream.h>
class worker
{
 char name[10];
 int hr;
 public:
 void accept()
 { 
 cout<<"enter name";
 cin>>name;
 cout<<"enter hours";
 cin>>hr;
 }
 void calculate(int rate=50)
 {
 cout<<"salary of worker is Rs."<<(hr*30)*rate;
 }
};
int main()
{
 worker ob;
 ob.accept();
 ob.calculate(100);
 return 0;
}

Slip 4 b)


1
#include <iostream.h>
#include <conio.h>
#include<stdlib.h>

const int m = 50;

class emp {
public:
    int empcode;
    char empname[30];
    void get() {
cout << "Enter Employee Code: ";
cin >> empcode;
cout << "Enter Employee Name: ";
cin.ignore();
cin.getline(empname, 30);
    }
};


class fulltime : public emp {
public:
    int no_of_days, daily_wages, salary1;

    void getdata() {
cout << "Enter number of days worked: ";
cin >> no_of_days;
cout << "Enter daily wages: ";
cin >> daily_wages;
    }

    void cal() {
salary1 = no_of_days * daily_wages;
    }

    void show() {
cout << "\n...............\n";
cout << "Employee Number: " << empcode << endl;
cout << "Employee Name: " << empname << endl;
cout << "Full-time Salary: " << salary1 << endl;
    }
};

class parttime : public emp {
public:
    int no_of_working_hours, hourly_wages, salary2;

    void getdata() {
cout << "Enter hourly wages: ";
cin >> hourly_wages;
cout << "Enter number of working hours: ";
cin >> no_of_working_hours;
    }

    void cal1() {
salary2 = hourly_wages * no_of_working_hours;
    }

    void show1() {
cout << "\n...............\n";
cout << "Employee Number: " << empcode << endl;
cout << "Employee Name: " << empname << endl;
cout << "Part-time Salary: " << salary2 << endl;
    }
};

int main() {
    int num, ch, k, l, cnt;
    fulltime f1[5];
    parttime p1[5];

    cout << "\n******MENU**********";
    cout << "\n1. Enter details of Full-time employee";
    cout << "\n2. Enter details of Part-time employee";
    cout << "\n3. Display Full-time employee with highest salary";
    cout << "\n4. Display Part-time employee with highest salary";
    cout << "\n5. Exit";

    do {
cout << "\nEnter your choice: ";
cin >> ch;
switch (ch) {
    case 1: {
cout << "\nHow many records you wish to enter for Full-time: ";
cin >> k;
for (int i = 0; i < k; i++) {
    f1[i].get();
    f1[i].getdata();
    f1[i].cal();
    f1[i].show();
}
break;
    }
    case 2: {
cout << "\nHow many records you wish to enter for Part-time: ";
cin >> l;
for (int i = 0; i < l; i++) {
    p1[i].get();
    p1[i].getdata();
    p1[i].cal1();
    p1[i].show1();
}
break;
    }
    case 3: {
cout << "\nHow many Full-time employees you want to display: ";
cin >> cnt;
int temp = 0;
for (int i = 0; i < cnt; i++) {
    f1[i].show();
    if (f1[temp].salary1 < f1[i].salary1) {
temp = i;
    }
}
cout << "\nEmployee with highest salary: " << f1[temp].empname;
cout << "\nSalary: " << f1[temp].salary1 << endl;
break;
    }
    case 4: {
cout << "\nHow many Part-time employees you want to display: ";
cin >> cnt;
int temp = 0;
for (int i = 0; i < cnt; i++) {
    p1[i].show1();
    if (p1[temp].salary2 < p1[i].salary2) {
temp = i;
    }
}
cout << "\nEmployee with highest salary: " << p1[temp].empname;
cout << "\nSalary: " << p1[temp].salary2 << endl;
break;
    }
    case 5:
exit(0);
    default:
cout << "\nYou entered an incorrect choice.";
}
    } while (ch != 5);

    return 0;
}


Slip4 

1

a)
1

b)

teacher.js

const readline = require('readline');
const rl = readline.createInterface({
input: process.stdin,
output: process.stdout

});

// Function to create and display a teacher profile

function createTeacherProfile() {

rl.question('Enter teacher name: ', (name) => {

rl.question('Enter subject: ', (subject) => {

rl.question('Enter years of experience: ', (experience) =>  {

// Display teacher profile

console.log('\nTeacher Profile:');
console.log('Name:'+`${name}`);

console.log('Subject:'+`${subject}`);

console.log('Experience:'+`${experience}`+ 'years');


rl.close();

});

});

});

}

// Start the teacher profile creation process
createTeacherProfile();
Slip 5



1
Slip 5 a)

#include<iostream>
using namespace std;

class Point {
    int x, y;

    public:
        void setpoint(int a, int b) {
            x = a;
            y = b;
        }

        void showpoint() {
            cout << "(" << x << ", " << y << ")";
        }
};


int main() {
    int a, b;
    Point p;

    cout << "Enter coordinates" << endl;
    cout << "Enter x: ";
    cin >> a;
    cout << "Enter y: ";
    cin >> b;

    p.setpoint(a, b);
    p.showpoint();

    return 0;
}

Slip 5 b)

/*
Create a C++ base class Shape. Derive three different classes Circle, Sphere and Cylinder from shape class. Write a C++ program to calculate area of Circle, Sphere and Cylinder. (Use pure virtual function)
*/

#include<iostream>
using namespace std;


class shape {
    public:
    virtual void area() = 0;
};


class circle: public shape {
   float r;

   public:
        void area() {
            cout << "\nEnter radius : ";
            cin >> r;
            cout << "\nArea of circle : " << (2.146*r*r);
        }
};


class rectangle: public shape {
int l,b;

    public:
    void area() {
        cout << "\nEnter length : ";
        cin >> l;
        cout << "\nEnter breadth : ";
        cin >> b;
        cout << "\nArea of rectangle : " << (l*b);
    }
};


class triangle: public shape {
int h,b;
    float a;

    public:
       void area() {
           cout << "\nEnter height : ";
            cin >> h;
            cout << "\nEnter breadth : ";
            cin >> b;
            cout << "\nArea of triangle : " << (0.5*h*b);
       }
};


int main() {
    circle c;
    c.area();

    cout << endl;

    rectangle r;
    r.area();

    cout << endl;

    triangle t;
    t.area();

    cout << endl;

   return(0);
}


Slip 5

1

a)

var buffer1 = Buffer.from('SYBCA');
var buffer2 = Buffer.from('Node Learning');
var buffer3 = Buffer.concat([buffer1,buffer2]);

console.log("buffer3 content: " + buffer3.toString());

var result = buffer1.compare(buffer2);

if(result < 0) {

   console.log(buffer1 +" comes before " + buffer2);

} else if(result === 0) {

   console.log(buffer1 +" is same as " + buffer2);

} else {

   console.log(buffer1 +" comes after " + buffer2);

}

 

buffer1.copy(buffer2);

console.log("buffer2 content: " + buffer2.toString());

b)

var mysql = require('mysql');
var con = mysql.createConnection({
 host: "localhost",
 user: "root",
 password: "12345",
 database: "stud123"
});

con.connect(function(err) {
 if (err) throw err;
 console.log("Connected!");
 con.query("SELECT * FROM c1", function (err, result, fields) {
   if (err) throw err;
   console.log(result);
   var sql = "DELETE FROM c1 WHERE address='nashik'";
   con.query(sql, function (err, result) {
     if (err) throw err;
     console.log("Number of records deleted: " + result.affectedRows);
   });
 });
 
});

Slip 6

1


Slip6a:

#include<iostream.h>
#include<conio.h>
 
 class sqaure
 {
    public:
        int s;
        void getdata()
        {
        cout<<"Enter side of square : ";
        cin>>s;
        }
 
        int calarea()
        {
        return(s*s);
        }
        friend void compare(int s,int r);
 };
 
 class rectangle
 {
    public:
        int l,w;
        void getdata()
        {
        cout<<"Enter Length of Rectangle : ";
        cin>>l;
        cout<<"Enter Breadth of Rectangle : ";
        cin>>w;
        }
 
        int calarea()
        {
        return(l*w);
        }
 
        friend void compare(int s,int r);
 };
 
 void compare(int s,int r)
 {
 if(s>r)
 {
 cout<<"\nThe area of sqaure is greater than area of rectangle"<<endl;
 }
 else
 {
 cout<<"\nThe area of rectangle is greater than area of sqaure"<<endl;
 }
 }
 
 int main()
 {
 int s_area,r_area;
 clrscr();
 sqaure s;
 rectangle r;
 
 s.getdata();
 s_area=s.calarea();
 
 r.getdata();
 r_area=r.calarea();
 
 cout<<"\nSquare : " <<s_area<<endl;
 cout<<"Rectangle : "<<r_area<<endl;
 
 compare(s_area,r_area);
 getch();
 return 0;
 }

Slip6b:


#include<iostream.h>
#include<conio.h>
 
class matrix
{
    int a[5][5];
    int r,c,i,j;
    public:
        matrix(int x,int y) //constructor
        {
        r=x;
        c=y;
        }
 
        ~matrix()
        {
        cout<<"destructor invoked";
        }
 
        void accept()
        {
        cout<<"Enter elements of matrix : ";
        for(i=0;i<r;i++)
        {
        for(j=0;j<c;j++)
        {
        cin>>a[i][j];
        }
        }
        }
 
        void display()
        {
        cout<<"Element of matrix are : \n";
        for(i=0;i<r;i++)
        {
        for(j=0;j<c;j++)
        {
        cout<<a[i][j]<<"\t";
        }
        cout<<endl;
        }
        }
 
        void transpose()
        {
        cout<<"\nTranspose of matrix is :\n ";
        for(i=0;i<c;i++)
        {
        for(j=0;j<r;j++)
        {
        cout<<a[j][i]<<"\t";
        }
        cout<<endl;
        }
        }
};
 
int main()
{
int m,n;
clrscr();
cout<<"Enter order of matrix : ";
cin>>m>>n;
matrix obj1(m,n);
obj1.accept();
obj1.display();
obj1.transpose();
getch();
return 0;
}

Slip6
1
a)
var http = require('http');
var url = require('url');
var fs = require('fs');

 http.createServer(function (req, res) {

  var q = url.parse(req.url, true);

  var filename = "." + q.pathname;

  fs.readFile(filename, function(err, data) {

    if (err) {

      res.writeHead(404, {'Content-Type': 'text/html'});

      return res.end("404 Not Found");

    } 

    res.writeHead(200, {'Content-Type': 'text/html'});

    res.write(data);

    return res.end();

  });

}).listen(8080);

b)

var mysql = require('mysql');
 var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345",
  database: "stud2025"

});

con.connect(function(err) {

  if (err) throw err;

  console.log("Connected!");

  var sql = "INSERT INTO sales (sno,pname,price) VALUES ?";  

var values = [  

[4,'abc', 77.6],  

[5,'def', 89.6],  

[6,'ghi', 91.6]  

];  

con.query(sql, [values], function (err, result) 

 {

    if (err) throw err;
    console.log("Number of records inserted: " + result.affectedRows);  

  });

con.query("SELECT * FROM sales", function (err, result, fields) {

    if (err) throw err;

    console.log(result);

  });

});


Slip8

1

Slip8a:

#include<iostream.h>
class Number
{
static int cnt;
int n;
public:
 /* void set_n()
{
cnt++;
}
*/
void Display()
{
 cnt++;
cout<<"Number of times display operation performed is:"<<cnt<<endl;
}
};
int Number::cnt=0;
int main()
{
Number ob1,ob2,ob3;
//ob1.set_n();
//ob2.set_n();
//ob3.set_n();
ob1.Display();
ob2.Display();
ob3.Display();
ob1.Display();
return 0;
}


Slip 8 b)



#include<iostream.h>
#include<conio.h>
#include<string.h>
 
class person
{
    public:
        int mob;
        char name[10],city[20];
        void acc() //function overloading
        {
        cout<<"Enter Person Name : ";
        cin>>name;
        cout<<"Enter Person City : ";
        cin>>city;
        cout<<"Enter Person Mobile Number : ";
        cin>>mob;
        }
 
        void acc(char nme[]) //function overloading
        {
        if(strcmp(nme,name)==0)
        {
        cout<<"\nPerson Name : "<<name;
        cout<<"\nPerson Mobile Number : "<<mob<<endl;
        }
        }
 
        void acc(int mno) //function overloading
        {
        if(mno==mob)
        {
        cout<<"\nPerson Name : "<<name;
        cout<<"\nPerson Mobile Number : "<<mob<<endl;
        }
        }
 
        void dis()
        {
        cout<<"\nPerson Details :"<<endl;
        cout<<"\n\nPerson Name : "<<name;
        cout<<"\nPerson Mobile Number : "<<mob;
        cout<<"\nPerson City : "<<city;
        }
};
 
int main()
{
char name[10];
int mno,i,ch,no;
clrscr();
person p[20];
do
{
    cout<<"\n1.Accept Person Details";
    cout<<"\n2.Display Person Details";
    cout<<"\n3.To Search mobile number of a given person";
    cout<<"\n4.To Search Person details of a given mobile number";
    cout<<"\n5.Exit";
    cout<<"\nEnter your choice : ";
    cin>>ch;
    switch(ch)
    {
    case 1:
        cout<<"\nEnter how many record to insert : ";
        cin>>no;
        for(i=0;i<no;i++)
        {
        p[i].acc();
        }
        break;
 
    case 2:
        for(i=0;i<no;i++)
        {
        p[i].dis();
        }
        break;
 
    case 3:
        cout<<"Enter person name search for mobile number : ";
        cin>>name;
        for(i=0;i<no;i++)
        {
        p[i].acc(name);
        }
        break;
 
    case 4:
        cout<<"Enter mobile number to search for person name : ";
        cin>>mno;
        for(i=0;i<no;i++)
        {
        p[i].acc(mno);
        }
        break;
    }
}while(ch!=5);
getch();
return 0;
}




1

a)
first create following text files 
 1)file1.txt
2)file2.txt
3)outputFile.txt

Then create slip8a.js file & write following code

const express = require('express');
const fs = require('fs');
const path = require('path');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

// Set up body-parser middleware
app.use(bodyParser.urlencoded({ extended: true }));

// Serve the HTML form for input
app.get('/', (req, res) => {
    res.send(`
        <h1>Combine Two Files into a Third File (Uppercase)</h1>
        <form method="POST" action="/combine">
            <label for="file1">File 1 Name:</label>
            <input type="text" id="file1" name="file1" required><br><br>

            <label for="file2">File 2 Name:</label>
            <input type="text" id="file2" name="file2" required><br><br>

            <label for="outputFile">Output File Name:</label>
            <input type="text" id="outputFile" name="outputFile" required><br><br>

            <button type="submit">Combine Files</button>
        </form>
    `);
});

// Handle form submission and combine files
app.post('/combine', (req, res) => {
    const { file1, file2, outputFile } = req.body;

    const filePath1 = path.join(__dirname, file1);
    const filePath2 = path.join(__dirname, file2);

    // Check if both files exist
    if (!fs.existsSync(filePath1) || !fs.existsSync(filePath2)) {
        return res.send("One or both files do not exist. Please check the file names and try again.");
    }

    // Read both files and combine their content
    fs.readFile(filePath1, 'utf8', (err, data1) => {
        if (err) return res.send("Error reading file 1: " + err.message);

        fs.readFile(filePath2, 'utf8', (err, data2) => {
            if (err) return res.send("Error reading file 2: " + err.message);

            // Combine both files' content and convert to uppercase
            const combinedContent = (data1 + '\n' + data2).toUpperCase();

            // Write the combined content to the output file
            const outputFilePath = path.join(__dirname, outputFile);
            fs.writeFile(outputFilePath, combinedContent, (err) => {
                if (err) return res.send("Error writing to output file: " + err.message);

                res.send(`Files combined successfully! Check the output file: ${outputFile}`);
            });
        });
    });
});

// Start the server
app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});



b)
create first ‘h8b.html' file

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Student Registration</title>
  </head>

  <body>
    <h2>STUDENT REGISTRATION FORM</h2>

    <form action="/register" method="post">
      <label for="firstName">First Name:</label>

      <input
        type="text"
        id="firstName"
        name="firstName"
        required
        pattern="[A-Za-z]+"
      />

      <br />

      <label for="lastName">Last Name:</label>

      <input
        type="text"
        id="lastName"
        name="lastName"
        required
        pattern="[A-Za-z]+"
      />

      <br />

      <label for="age">Age:</label>

      <input type="number" id="age" name="age" min="6" max="25" required />

      <br />

      <input type="submit" value="Register" />
    </form>
  </body>
</html>

Then create  slip8b.js file

const express = require('express');

const { body, validationResult } = require('express-validator');


const app = express();

const PORT = process.env.PORT || 3000;


app.use(express.urlencoded({ extended: true }));


app.get('/', (req, res) => {

    res.sendFile(__dirname + '/h8b.html');

});


app.post('/register', [

    body('firstName').isAlpha().withMessage('First name should contain only alphabets'),

    body('lastName').isAlpha().withMessage('Last name should contain only alphabets'),

    body('age').isInt({ min: 6, max: 25 }).withMessage('Age must be between 6 and 25'),

], (req, res) => {

    const errors = validationResult(req);

    if (!errors.isEmpty()) {

        return res.status(400).json({ errors: errors.array() });

    }

    // Save student details to database or perform other actions

    res.send('Registration successful!');

});


app.listen(PORT, () => {

    console.log(`Server running on port ${PORT}`);

});


Slip9
1


Slip9a:


#include<iostream.h>
#include<conio.h>
 
class person
{
    char name[20];
    char addr[20];
    float sal,tax;
    public:
        void get()
        {
        cout<<"Enter Name : ";
        cin>>name;
        cout<<"Enter Address : ";
        cin>>addr;
        cout<<"Enter Salary : ";
        cin>>sal;
        }
 
        void put()
        {
        cout<<"\n\n-----Person information-----";
        cout<<"\nPerson Name : "<<name;
        cout<<"\nPerson Address : "<<addr;
        cout<<"\nPerson Salary : "<<sal;
        cout<<"\nTax is : "<<tax;
        }
 
        void cal_tax()
        {
        if(sal<=20000)
        {
        tax=0;
        }
        else if(sal>20000 || sal<=40000)
        {
        tax=(sal*5)/100;
        }
        else if(sal>40000)
        {
        tax=(sal*10)/100;
        }
        }
};
 
void main()
{
person p;
clrscr();
p.get();
p.cal_tax();
p.put();
getch();
}

Slip9b:

2.Create a C++ class Time with data members Hours, Minutes and Seconds.
Write necessary member functions for the following: (Use Objects as arguments)
1. To accept a time.
2. To display a time In format hh:mm:ss.
3. To find difference between two time and display it in format hh:mm:ss.[25 Marks]

#include<iostream.h>
#include<conio.h>
#include<iomanip.h>
 
class time
{
    int h,m,s;
    public:
        void get();
        void display();
        time operator -(time t2);
};
 
void time::get()
{
    cout<<"\nEnter Hour, Minutes and Seconds : ";
    cin>>h>>m>>s;
}
 
void time::display()
{
    cout<<"\n----Time is----"<<setfill('0')<<setw(2)<<h;
    cout<<":"<<setfill('0')<<setw(2)<<m;
    cout<<":"<<setfill('0')<<setw(2)<<s<<endl;
}
 
time time::operator -(time t2)
{
    time t;
    t.h=h-t2.h;
    t.m=m-t2.m;
    t.s=s-t2.s;
    return t;
}
 
void main()
{
clrscr();
time t1,t2,t3;
t1.get();
t1.display();
t2.get();
t2.display();
t3=t1-t2;
cout<<"\nTime1-Time2:\n";
t3.display();
getch();
}

1

Slip 9 a)
var http = require('http');
http.createServer(function (req, res) {

  res.writeHead(200, {'Content-Type': 'text/html'});

  res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');

  res.write('<input type="file" name="filetoupload"><br>');

  res.write('<input type="submit">');

  res.write('</form>');

  return res.end();

}).listen(8000);



Slip9b)

const express = require('express');

const bodyParser = require('body-parser');

const app = express();

const port = 8000;

app.use(bodyParser.json());

const recipes = [

{
name: "Maggi",

ingredients: ["2 Bricks of Instant Ramen/Maggi Noodles",
    "Green Onions",
    "Corn",
    "Peas",
    "Green Cabbage"],

instructions: " Boil maggi & Add onion,corn, peas, and green cabbage cook it Garnish with green onions and serve."
},

{

name: "Chicken Stir-Fry",

ingredients: ["Chicken breast", "Broccoli", "Bell peppers", "Soy sauce", "Garlic", "Ginger"],

instructions: "Slice chicken and stir-fry until cooked. Add vegetables, soy sauce, garlic, and ginger. Cook until vegetables are tender."

},

// Add more recipes as needed

];

// Get all recipes

app.get('/recipes', (req, res) => {

res.json(recipes);

});

// Add a new recipe

app.post('/recipes', (req, res) => {

const newRecipe = req.body;

recipes.push(newRecipe);

res.json({ message: 'Recipe added successfully', recipe: newRecipe });

});

// Search for a specific recipe

app.get('/recipes/:name', (req, res) => {

const recipeName = req.params.name.toLowerCase();

const recipe = recipes.find(r => r.name.toLowerCase() === recipeName);

if (recipe) {

res.json(recipe);

} else {

res.status(404).json({ error: 'Recipe not found' });

}

});

app.listen(port, () => {

console.log('Server is running at http://localhost:${port}');

});




Slip 11
1

Slip 11 a) 
1 . Create a C++ class MyArray, which contains single dimensional integer array of a given size. Write a member function to display sum of given array elements. (Use Dynamic Constructor and Destructor)[15 Marks]

#include<iostream.h>
#include<conio.h>
#include<stdio.h>
 
class MyArray
{
    int size,*ptr,*p;
 
    public:
        MyArray(int no)
        {
            size=no;
            int i;
            ptr=new int[size];
            for(i=0;i<size;i++)
            {
                cout<<"\nEnter elements : \n";
                cin>>ptr[i];
            }
        }
 
        void display()
        {
            int i;
            cout<<"\nElements are :\n";
            for(i=0;i<size;i++)
            {
                cout<<ptr[i]<<"\t";
            }
 
        }
 
        void calculatesum()
        {
            int arr[10];
            int i,sum=0;
            cout<<"\nEnter 10 array elements : \n";
            for(i=0;i<10;i++)
            {
                cin>>arr[i];
                sum=sum+arr[i];
            }
            cout<<"\nThe array elements are :\n";
            for(i=0;i<10;i++)
            {
                cout<<arr[i]<<"\t";
            }
            cout<<"\n\nSum of all elements are : "<<sum;
        }
 
        ~MyArray()
        {
            delete ptr;
        }
};
 
void main()
{
    int n;
    clrscr();
    cout<<"\nEnter size : ";
    cin>>n;
    MyArray d(n);
    d.display();
    d.calculatesum();
    getch();
}

Slip 11 b)
2 . Create a base class Student with data members Roll No, Name. Derives two classes from it, class Theory with data members Ml, M2, M3, M4 and class Practical with data members PI, P2. Class Result(Total Marks, Percentage, Grade) inherits both Theory and Practical classes.
(Use concept of Virtual Base Class and protected access specifiers)
Write a C++ menu driven program to perform the following functions:
i. Accept Student Information
ii. Display Student Information
iii. Calculate Total marks, Percentage and Grade.[25 Marks]

#include<iostream.h>
#include<stdlib.h>
#include<conio.h>
#include<string.h>
 
class student
{
    protected :
        int rno;
        char name[20];
    public:
        void getdetails();
};
 
class theory:public virtual student
{
    protected:
        int mark1,mark2,mark3,mark4;
    public:
        void getmarks();
};
 
class practical:public virtual student
{
    protected:
        int p1,p2;
    public:
        void getpractical();
};
 
class result:public theory,public practical
{
    int total_marks;
    float per;
    char grade[10];
 
    public:
        void cal();
        void display();
};
 
void student::getdetails()
{
    cout<<"\nEnter Roll no and Name :\n ";
    cin>>rno>>name;
}
 
void theory::getmarks()
{
    cout<<"\nEnter marks of 4 subject : \n";
    cin>>mark1>>mark2>>mark3>>mark4;
}
 
void practical::getpractical()
{
    cout<<"\nEnter practical details : \n";
    cin>>p1>>p2;
}
 
void result::cal()
{
    int i;
    total_marks=mark1+mark2+mark3+mark4+p1+p2;
    per=total_marks/6;
    if(per<50)
    strcpy(grade,"C");
 
    else if(per<60)
    strcpy(grade,"B");
 
    else if(per<75)
    strcpy(grade,"A");
 
    else
    strcpy(grade,"A+");
    cout<<"\nCalculation completed..";
}
 
 
void result::display()
{
    cout<<"\n\nRoll no = "<<rno<<"\nName = "<<name;
    cout<<"\n\nTheory Marks : \n"<<"Marks 1 = "<<mark1<<"\n"<<"Marks 2 = "<<mark2<<"\nMarks 3 = "<<mark3<<"\nMarks 4 = "<<mark4;
    cout<<"\n\nPractcal : \n"<<"Practical p1 = "<<p1<<"\nPractical p2 = "<<p2;
    cout<<"\n\nPercentage = "<<per;
    cout<<"\nGrade = "<<grade;
}
 
int main()
{
    int n,i,ch,j;
    result r[40];
    clrscr();
    do
    {
    cout<<"\n1.Accept student Information";
    cout<<"\n2.Display student Infromation";
    cout<<"\n3.Calculate percenatge and grade";
    cout<<"\n4.Exit";
    cout<<"\n\nEnter your choice : ";
    cin>>ch;
    switch(ch)
    {
        case 1:
            cout<<"\nEnter Number of student : ";
            cin>>n;
            for(i=0;i<n;i++)
            {
                cout<<"\nEnter student details :\n";
                r[i].getdetails();
                r[i].getmarks();
                r[i].getpractical();
            }
            break;
 
        case 2:
            for(i=0;i<n;i++)
            {
                r[i].display();
            }
 
            break;
 
        case 3:
            for(i=0;i<n;i++)
            {
                r[i].cal();
            }
            break;
 
        case 4:
            exit(0);
    }
    }while(ch<=4);
 
getch();
return 0;
}

Slip 11

1

const express = require('express');
const app = express();
const port = 3000;

// Define the college information
const collegeInfo = {
    name: 'R.N.C Arts,J.D.B Commerce and N.S.C Science College,Nashik ',
    location: 'Bytco college,nashik raod nashik',
    established: 1963,
    departments: ['Computer Science', 'computer application'],
    website: 'https://bcud.unipune.ac.in/utilities/college_search/CAAN017370_ENG/Pune_University_College'
};

// Route to show college info
app.get('/', (req, res) => {
    res.send(`
        <h1>Welcome to ${collegeInfo.name}</h1>
        <p>Location: ${collegeInfo.location}</p>
        <p>Established: ${collegeInfo.established}</p>
        <p>Departments: ${collegeInfo.departments.join(', ')}</p>
        <p>Website: <a href="${collegeInfo.website}" target="_blank">${collegeInfo.website}</a></p>
    `);
});

// Start the server
app.listen(port, () => {
    console.log(`Server is running at http://localhost:${port}`);
});


Create html file ‘h11b.html’ 
<!DOCTYPE html>

<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Department Portal</title>
  </head>

  <body>
    <h2>Department Portal Form</h2>

    <form action="/register" method="post">
      <label for="firstName">First Name:</label>

      <input
        type="text"
        id="firstName"
        name="firstName"
        required
        pattern="[A-Za-z]+"
      />

      <br />

      <label for="lastName">Last Name:</label>

      <input
        type="text"
        id="lastName"
        name="lastName"
        required
        pattern="[A-Za-z]+"
      />

      <br />

      <label for="class">class:</label>

      <input type="text" id="class" name="class" required pattern="[A-Za-z]+" />

      <br />

      <input type="submit" value="Register" />
    </form>
  </body>
</html>


Create slip11b.js file

const express = require('express');

const { body, validationResult } = require('express-validator');


const app = express();

const PORT = process.env.PORT || 8000;


app.use(express.urlencoded({ extended: true }));


app.get('/', (req, res) => {

    res.sendFile(__dirname + '/h11b.html');

});


app.post('/register', [

    body('firstName').isAlpha().withMessage('First name should contain only alphabets'),

    body('lastName').isAlpha().withMessage('Last name should contain only alphabets'),

    body('class').isAlpha().withMessage('class name should contain only alphabets')

], (req, res) => {

    const errors = validationResult(req);

    if (!errors.isEmpty()) {

        return res.status(400).json({ errors: errors.array() });

    }

    // Save student details to database or perform other actions

    res.send('Registration successful!');

});


app.listen(PORT, () => {

    console.log(`Server running on port ${PORT}`);

});


1


Slip 13
1
Slip 13 a) 

1 .Write a C++ program to create a class Product with data members Product id, Product Name, Qty, Price. Write member functions to accept and display Product information also display number of objects created for Product class. (Use Static data member and Static member function)
[15 Marks]

#include<iostream.h>
#include<conio.h>
 
class product
{
    int id,price,qty;
    char i_name[20];
    static int cnt;
    public:
        void getdata()
        {
            cout<<"\nEnter Producr Id : ";
            cin>>id;
            cout<<"Enter Product Name : ";
            cin>>i_name;
            cout<<"Enter Product Price : ";
            cin>>price;
            cout<<"Entre Product Qty : ";
            cin>>qty;
            cnt++;
        }
 
        void display()
        {
            cout<<"\n\nProcut Id = "<<id;
            cout<<"\nProduct Name = "<<i_name;
            cout<<"\nProduct Price = "<<price;
            cout<<"\nProduct Qty = "<<qty;
        }
 
        static void nob()
        {
            cout<<"\nNumber of object created for class are : "<<cnt;
        }
};
 
int product::cnt;
void main()
{
    product ob[10];
    clrscr();
    int n,i;
    cout<<"\nEnter No of product :";
    cin>>n;
    for(i=0;i<n;i++)
    {
    ob[i].getdata();
    }
 
    for(i=0;i<n;i++)
    {
    ob[i].display();
    }
 
    ob[n-1].nob();
    getch();
}

Slip 13 b) 
2.Create a C++ class Cuboid with data members length, breadth, and height. Write necessary member functions for the following:
i. void setvalues(float,float,float) to set values of data members.
ii. void getvalues( ) to display values of data members.
iii. float volume( ) to calculate and return the volume of cuboid.
iv. float surface area( ) to calculate and return the surface area of cuboid.
(Use Inline function)[25 Marks]

#include<iostream.h>
#include<conio.h>
 
class cuboid
{
    float len,bre,hei;
    public:
        void getdata()
        {
            cout<<"\nEnter Length,Breadth and Heigth of cuboid : \n";
            cin>>len>>bre>>hei;
        }
 
        void setdata()
        {
            cout<<len<<bre<<hei;
        }
 
        inline void volume()
        {
            cout<<"\nThe Volume of cuboid is : "<<len*bre*hei;
        }
 
        inline void surface_area()
        {
            cout<<"\nThe Surface area of cuboid is : "<<(2*len*bre + 2*bre*hei + 2*len*hei);
        }
};
 
void main()
{
    clrscr();
    cuboid c;
    c.getdata();
    c.volume();
    c.surface_area();
    getch();
}


1

Slip 13  
a)
rect.js
 var rect={ 
  area: function(l,b)
{
    var a; 
     a=l*b;
   console.log('area of rectangle is:'+a);
}
};
 module.exports=rect
 myrect.js
 var mymod=require('C:/Users/Public/node_prog/rect.js');
mymod.area(5,4);
 Initiate myrect.js file :
 C:\Users\Your Name>node myrect.js
Slip 13

b)
Set Up the MySQL Database:
create a database ‘studentdb’ and a ‘student’ table in it with the necessary fields.
Create conn.js file in node

const express = require('express');
const mysql = require('mysql');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

// Set up middleware
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

const con = mysql.createConnection({
  host: 'localhost',
  user: 'root', 
  password: ‘12345’,  
database: 'studentdb'
});

con.connect((err) => {
  if (err) {
    console.error('Error connecting to the database:', err.stack);
    return;
  }
  console.log('Connected to the database');
});

// Route to update student marks
app.post('/update-marks', (req, res) => {
  const { rollno, marks } = req.body;
  if (!rollno || !marks) {
    return res.status(400).send('Roll number and marks are required');
  }

  const sql = 'UPDATE student SET marks = ? WHERE rollno = ?';
  con.query(sql, [marks, rollno], (err, result) => {
    if (err) {
      console.error('Error updating marks:', err.stack);
      return res.status(500).send('Server error');
    }
    if (result.affectedRows === 0) {
      return res.status(404).send('Student not found');
    }
    res.send('Marks updated successfully');
  });
});

// Route to display all students
app.get('/students', (req, res) => {
  const sql = 'SELECT * FROM student';
  con.query(sql, (err, results) => {
    if (err) {
      console.error('Error fetching students:', err.stack);
      return res.status(500).send('Server error');
    }
    res.json(results);
  });
});

// Start the server
app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});

Slip14

1

Slip14a:

1.Write a C++ program to accept radius of a Circle. Calculate and display diameter, circumference as well as area of a Circle. (Use Inline function)[15 Marks]

#include<iostream.h>
#include<conio.h>
 
inline float diameter(float r)
{
    return(r/2);
}
 
inline float circlearea(float r)
{
    return(3.14*r*r);
}
 
inline float circumeference(float r)
{
    return(3.14*2*r);
}
 
int main()
{
    float radius;
    clrscr();
    cout<<"\nEnter Radius of circle : ";
    cin>>radius;
    cout<<"\n\nDiameter of circle : "<<diameter(radius);
    cout<<"\nArea of circle : "<<circlearea(radius);
    cout<<"\nCircumeference of circle : "<<circumeference(radius);
    getch();
    return 0;
}

Slip 14 b) 
2 .Create a C++ class MyString with data members a character pointer and str length. (Use new and delete operator).
Write a C++ program using operator overloading to perform following operation:
i. To reverse the case of each alphabet from a given string.
ii. To compare length of two strings.
iii. To add constant ‘n’ to each alphabet of a string.[25 Marks]

#include <iostream.h>
#include <cstring.h>
 
class MyString {
private:
    char *str;
    int length;
 
public:
    // Constructor
    MyString(const char *s) {
        length = strlen(s);
        str = new char[length + 1];
        strcpy(str, s);
    }
 
    // Destructor
    ~MyString() {
        delete[] str;
    }
 
    // Function to reverse the case of each alphabet
    MyString& reverseCase() {
        for (int i = 0; i < length; ++i) {
            if (isalpha(str[i])) {
                if (islower(str[i]))
                    str[i] = toupper(str[i]);
                else
                    str[i] = tolower(str[i]);
            }
        }
        return *this;
    }
 
    // Function to compare length of two strings
    bool operator<(const MyString &other) const {
        return length < other.length;
    }
 
    // Function to add a constant 'n' to each alphabet of a string
    MyString& operator+(int n) {
        for (int i = 0; i < length; ++i) {
            if (isalpha(str[i])) {
                str[i] += n;
            }
        }
        return *this;
    }
 
    // Function to display the string
    void display() const {
        cout << str << endl;
    }
};
 
int main() {
    MyString str1("Hello World!");
    MyString str2("Goodbye");
 
    cout << "Original strings:" << endl;
    str1.display();
    str2.display();
 
    // Reverse the case of each alphabet
    str1.reverseCase().display();
 
    // Compare lengths of two strings
    if (str1 < str2) {
        cout << "String 1 is shorter than String 2." << endl;
    } else {
        cout << "String 1 is longer than or equal to String 2." << endl;
    }
 
    // Add a constant 'n' to each alphabet of a string
    str2 + 1;
   cout << "After adding 1 to each alphabet of String 2:" <<endl;
    str2.display();
 
    return 0;
}


Slip No.14.
1

Slip No.14. A Create a Node.js application to search particular word in fille and display result on console.
 search_word.js
var fs=require('fs');
fs.readFile('C:/Users/Public/node_prog/searchf.txt', function (err, data) {
  if (err) throw err;
 
  if(data.includes('dfgdf')){
   console.log(data.toString())
  }
else
{
  console.log('word not found');
}
});

b)

//billCalculator.js

function calculateBill(units) {

    let billAmount = 0;
    
    if (units <= 100) {
    
    billAmount = units * 1.50; // Replace 1.50 with your applicable rate
    
    } else if (units <= 200) {
    
    billAmount = 100 * 1.50 + (units - 100) * 2.00; // First 100 units at 1.50, remaining at 2.00
    
    } else if (units <= 300) {
    
    billAmount = 100 * 1.50 + 100 * 2.00 + (units - 200) * 2.50; // First 100 units at 1.50, next 100 at 2.00, remaining at 2.50
    
    } else {
    
    billAmount = 100 * 1.50 + 100 * 2.00 + 100 * 2.50 + (units - 300) * 3.00; // First 100 units at 1.50, next 100 at 2.00, next 100 at 2.50, remaining at 3.00
    
    }
    
    return billAmount;
    
    }
    
    module.exports = { calculateBill };

s14b.js

const readline = require('readline');

const { calculateBill } = require('./billcalculator.js');

const rl = readline.createInterface({

input: process.stdin,

output: process.stdout

});

rl.question('Enter the number of units consumed: ', (units) => {

const billAmount = calculateBill(units);

console.log(`Your electricity bill amount is: $${billAmount.toFixed(2)}`);

rl.close();

});


Slip 16

Slip 16 a) 

1.Write a C++ program to create a class Machine with data members Machine Id, Machine Name, Price. Create and initialize all values of Machine object by using parameterized constructor and copy constructor.
Display details of Machine using setw( ) and setprecision( ).[15 Marks]


#include<iostream.h>
#include<conio.h>
#include<string.h>
#include<iomanip.h>
 
class machine
{
    private:
        int machine_id,price;
        char name[20];
        public:
            //parameterized constructor
            machine(int x1,int y1,char *z1)
            {
                strcpy(name,z1);
                machine_id=x1;
                price=y1;
            }
 
            //copy constructor
            machine(const machine &same)
            {
                strcpy(name,same.name);
                machine_id=same.machine_id;
                price=same.price;
            }
 
            void display()
            {
                cout<<"\nName : "<<name;
                cout<<"\nMachine id : "<<setprecision(2)<<machine_id;
                cout<<"\nPrice : "<<setw(3)<<price;
            }
};
 
int main()
{
    clrscr();
    machine o1(13,345,"deep"); //normal or parameterised constructor
    machine o2=o1; //copy constructor
    cout<<"\n\nNormal constructor : ";
    o1.display();
    cout<<"\n\nCopy constructor : ";
    o2.display();
    getch();
    return 0;
}

Slip 16 b) 

2.Create a class Matrix Write necessary member functions for the following:
i. To accept a Matrix
ii. To display a Matrix
iii. Overload unary ‘-‘ operator to calculate transpose of a Matrix.
iv. Overload unaryoperator to increment matrix elements by I[25 Marks]

#include<iostream.h>
#include<string.h>
#include<conio.h>
 
class mystring
{
    int a[3][3],i,j;
    public:
        void get();
        void put();
        void operator-();
        void operator++();
};
 
void mystring::get()
{
    int i,j;
    cout<<"\nEnter matrix elements : \n";
    for(i=0;i<3;i++)
    {
    for(j=0;j<3;j++)
    {
    cin>>a[i][j];
    }
    }
}
 
void mystring::put()
{
    int i,j;
    cout<<"\nMatrix is : \n";
    for(i=0;i<3;i++)
    {
    for(j=0;j<3;j++)
    {
    cout<<a[i][j];
    cout<<"\t";
    }
    }
}
 
void mystring::operator-()
{
    for(i=0;i<3;i++)
    {
    for(j=0;j<3;j++)
    {
    a[i][j]=-a[i][j];
    }
    }
}
 
void mystring::operator++()
{
    for(i=0;i<3;i++)
    {
    for(j=0;j<3;j++)
    {
    a[i][j]=++a[i][j];
    }
    }
}
 
int main()
{
    mystring m1;
    clrscr();
    cout<<"\nEnter matrix value ";
    m1.get();
    m1.put();
    -m1;
    cout<<"\nAfter negetion matrix : \n";
    m1.put();
    ++m1;
    cout<<"\nAfter increment : \n";
    m1.put();
    m1++;
    m1.put();
    getch();
    return 0;
}

Slip 16

1
Slip 16 a)

// Import the EventEmitter class from the 'events' module
const EventEmitter = require('events');

const eventEmitter = new EventEmitter();

function onEventTriggered() {
  console.log('Event has been triggered!');
}

// Listen for an event named 'customEvent' and call the callback function when it's emitted

eventEmitter.on('customEvent', onEventTriggered);

function mainLoop() {
  let count = 0;
  
  // Simulate events being triggered every 2 seconds
  setInterval(() => {
    console.log('Main loop running...');
    count++;
    
    // Emit the 'customEvent' every 3 iterations
    if (count % 3 === 0) {
      console.log('Emitting customEvent...');
      eventEmitter.emit('customEvent');
    }
  }, 2000);  // The loop runs every 2 seconds
}

// Start the main loop
mainLoop();

Slip 16 b)
var mysql = require('mysql');
var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345",
  database: "empdb"
});
con.connect(function(err) {
  if (err) throw err;
  var sql = "update employee set sal=500000 where eno=1";
  con.query(sql, function (err, result,display) {
    if (err) throw err;
    console.log(result.affectedRows+"record updated");
  });
con.query("select * from employee",function (err, result,fields) {
if (err) throw err;
    console.log(result);
});
});


Slip 20:

1

1.Create a C++ class Number with integer data member. Write necessary member functions to overload the operator unary pre and post increment ‘++’[15 Marks]

#include<iostream.h>
#include<conio.h>
 
class number
{
    private:
        int i;
        public:
            number(){}
            number(int num)
            {
                i=num;
            }
 
            number operator++()
            {
            ++i;
            return *this;
            }
 
            number operator++(int)
            {
            number temp=*this;
            i++;
            return temp;
            }
 
            void display()
            {
                cout<<"i = "<<i<<endl;
            }
};
 
int main()
{
    number o(5),o1(5);
    clrscr();
 
    cout<<"\nOriginal Number = "<<endl;
    o.display();
    ++o;
    cout<<"\n\nAfter pre-increment number = "<<endl;
    o.display();
    o1++;
    cout<<"\n\nAfter post-increment number = "<<endl;
    o1.display();
    getch();
    return 0;
}

2. Create a C++ class for inventory of Mobiles with data members Model, Mobile Company, Color, Price and Quantity. Mobile can be sold, if stock is available, otherwise purchase will be made.
Write necessary member functions for the following:
i.To accept mobile details from user.
ii. To sale a mobile. (Sale contains Mobile details & number of mobiles to be sold.)
iii. To Purchase a Mobile. (Purchase contains Mobile details & number of mobiles to be purchased)[25 Marks]

#include<iostream.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>
 
class inventory
{
    int mno;
    char mname[20];
    int stock;
    float price;
 
    public:
        void accept()
        {
            cout<<"\nEnter model no : ";
            cin>>mno;
            cout<<"Enter model name : ";
            cin>>mname;
            cout<<"Enter price : ";
            cin>>price;
            cout<<"Enter stock : ";
            cin>>stock;
        }
 
        void display()
        {
            cout<<"\n\nModel no : "<<mno;
            cout<<"\nModel name :"<<mname;
            cout<<"\nModel price : "<<price;
            cout<<"\nModel stock : "<<stock;
        }
 
        int sale(int no,int q)
        {
        if(mno==no)
            {
                if(stock>=q)
                    {
                        stock=stock-q;
                        cout<<"\nSale is done";
                        display();
                        return 2;
                    }
                else
                    {
                        cout<<"\nPurchase is required";
                        purchase(q,no);
                        return 1;
                    }
 
          /*    else
        {
        cout<<"\nPlease enter correct model no";
        } */
        }
        }
 
        void purchase(int no,int q)
        {
 
            if(no==mno)
                {
                    stock=stock+q;
                    cout<<"\nPurchse is done..";
                    display();
                }
        }
};
 
int main()
{
    inventory in[20];
    int qt,ans,no,i,n;
    clrscr();
 
    cout<<"\nEnter no of models : ";
    cin>>no;
 
    for(i=0;i<no;i++)
    {
    in[i].accept();
    }
 
    for(i=0;i<no;i++)
    {
    in[i].display();
    }
 
    cout<<"\n\nEnter model number to be purchase and quantity : ";
    cin>>n>>qt;
    for(i=0;i<no;i++)
    {
    ans=in[i].sale(n,qt);
    if(ans==1)
    {
        cout<<"\nEnter model to be purchse and quantity : ";
        cin>>n>>qt;
        for(i=0;i<no;i++)
        {
        in[i].purchase(n,qt);
        }
    }
    }
    getch();
    return 0;
}


Slip 20 


1

a)
const fs = require('fs');
const filePath = './f111.txt';

// Define a function to handle the file reading operation
function readFileHandler() {
    // Open and read the content of the file asynchronously
    fs.readFile(filePath, 'utf8', (err, data) => {
        if (err) {
            // If there's an error, log it
            console.error('Error reading the file:', err);
        } else {
            // If successful, output the file content
            console.log('File content:', data);
        }
    });
}

// Event listener to trigger the file reading when called
// Here we use a simple eventEmitter to trigger an event for file reading
const EventEmitter = require('events');
class FileReader extends EventEmitter {}

const fileReader = new FileReader();

// Registering the 'readFile' event and associating it with the readFileHandler function
fileReader.on('readFile', readFileHandler);

// Trigger the 'readFile' event to start reading the file
fileReader.emit('readFile');

b)

const express = require('express');
const app = express();
const port = 8083;
const collegeInfo = {
    name: 'R.N.C Arts,J.D.B Commerce and N.S.C Science College,Nashik ',
    location: 'Bytco college,nashik raod nashik',
    established: 1963,
    departments: ['Computer Science', 'computer application'],
    website: 'https://bcud.unipune.ac.in/utilities/college_search/CAAN017370_ENG/Pune_University_College'
};

// Define the college information
const courseStructure = {
    
      sem1: 'Semester I :Principles of Management Business Communication',
      Sem2:'Semester II :C,DBMS',
      sem3:'Bigdata,R programming , Software Engineering',
      sem4: 'node ,cpp,Networking' 
        
}
          
// Route to show college info
app.get('/', (req, res) => {
    res.send(`
        <h1>Welcome to SYBBA (CA)Courses </h1>
        <p>Sem-I : ${courseStructure.sem1}</p>
        <p>Sem-II: ${courseStructure.sem2}</p>
        <p>Sem-III: ${courseStructure.sem3}</p>
        <p>Sem-IV: ${courseStructure.sem4}</p>
            `);
});
 app.listen(port, () => {
    console.log(`Server is running at http://localhost:${port}`);
});


Slip 27 :
1.Create a C++ class College, with data members College Id, College Name, Establishment_year, University Name. Overload operators>> and << to accept and display College information.[15 Marks]
#include<iostream.h>
#include<conio.h>

class college
{
private:
int id,year;
char name[20],uname[20];
public:
college(){}

friend ostream&operator<<(ostream &out,const college &c);
friend istream&operator>>(istream &in,college &c);
};

ostream &operator<<(ostream &out,const college &c)
{
out<<"\nCollege Id : "<<c.id;
out<<"\nCollege name : "<<c.name;
out<<"\nEstablishment year : "<<c.year;
out<<"\nUniversity name : "<<c.uname<<endl;
return out;
}

istream &operator>>(istream &in,college &c)
{
cout<<"\nEnter college id : ";
in>>c.id;
cout<<"Enter college name : ";
in>>c.name;
cout<<"Enter year of establishment : ";
in>>c.year;
cout<<"Enter university name : ";
in>>c.uname;
return in;
}

int main()
{
clrscr();
college c1;
cin>>c1;
cout<<"\nThe college details are : \n";
cout<<c1;
getch();
return 0;
}
Slip 27 
2)
Create a base class Travels with data members T no, Company Name. Derive a class Route with data members Route id, Source, and Destination from Travels class. Also derive a class Reservation with data members Number of Seats, Travels Class, Fare, and Travel Date from Route. Write a C++ program to perform following necessary member functions:i. Accept details of ‘n’ reservations.ii. Display details of all reservations.iii. Display reservation details of a specified Date.[25 Marks]
#include<iostream.h>
#include<conio.h>

class travels
{
protected:
int tno;
char cname[30];
public:
void accept()
{
cout<<"\nEnter Travelling no : ";
cin>>tno;
cout<<"Enter company name : ";
cin>>cname;
}
};

class route:public travels
{
public:
int id;
char s[10],d[10];
void acc()
{
cout<<"\nEnter route id : ";
cin>>id;
cout<<"Enter source station : ";
cin>>s;
cout<<"Enter Destination station : ";
cin>>d;
}
};

class reservation:public route
{
public:
int no_of_seats,fare,dd,mm,yyyy;
char tclass[20];
void get()
{
cout<<"\nEnter no of seats : ";
cin>>no_of_seats;
cout<<"Enter travel class : ";
cin>>tclass;
cout<<"Enter date(DD/MM/YYYY) : ";
cin>>dd>>mm>>yyyy;
}

void put()
{
cout<<"\n\nTravel no : "<<tno;
cout<<"\nCompany name : "<<cname;
cout<<"\nRoute id : "<<id;
cout<<"\nRoute source : "<<s;
cout<<"\nRoute destination : "<<d;
cout<<"\nNo of seats : "<<no_of_seats;
cout<<"\nTravel class : "<<tclass;
cout<<"\nTrain date : "<<dd<<"/"<<mm<<"/"<<yyyy;
}
};

int main()
{
int i,n;
reservation r[20];
clrscr();
cout<<"\nEnter number of records : ";
cin>>n;
for(i=0;i<n;i++)
{
r[i].accept();
r[i].acc();
r[i].get();
}

for(i=0;i<n;i++)
{
r[i].put();
}
getch();
return 0;
}

Slip 27:

1
a)

const fs = require('fs');
const path = require('path');

function createDirectoryAndFiles() {
    const dirPath = path.join(__dirname, 'myDirectory');
    
    // Check if the directory exists
    if (!fs.existsSync(dirPath)) {
        // Create directory
        fs.mkdirSync(dirPath);
        console.log('Directory created:', dirPath);
    } else {
        console.log('Directory already exists:', dirPath);
    }

    // Add some files to the directory
    const filePath1 = path.join(dirPath, 'file1.txt');
    const filePath2 = path.join(dirPath, 'file2.txt');

    // Check if file1 exists, if not create it
    if (!fs.existsSync(filePath1)) {
        fs.writeFileSync(filePath1, 'This is file 1 content');
        console.log('File created:', filePath1);
    }

    // Check if file2 exists, if not create it
    if (!fs.existsSync(filePath2)) {
        fs.writeFileSync(filePath2, 'This is file 2 content');
        console.log('File created:', filePath2);
    }
}

// Run the function to create the directory and files
createDirectoryAndFiles();

b)

// studentRegistration.js


const readline = require('readline');

const rl = readline.createInterface({

input: process.stdin,

output: process.stdout

});

 

// Function to validate student registration form

function validateStudentForm() {

rl.question('Enter student name: ', (name) => {

rl.question('Enter age: ', (age) => {

rl.question('Enter email: ', (email) => {

if (isValidAge(age) && isValidEmail(email)) {

 // Display success message

console.log('\nStudent Registration Successful!');

console.log(`Name: ${name}`);

console.log(`Age: ${age}`);

console.log(`Email: ${email}`);

 rl.close();

}

else {

console.log('Invalid input. Please check your age and email format.');

rl.close();

}

});

});

});

}

 

// Function to validate age (must be a positive integer)

function isValidAge(age) {

return /^\d+$/.test(age) && parseInt(age) > 0;

}

 

// Function to validate email format

function isValidEmail(email) {

const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

return emailRegex.test(email);

}
 

// Start the student registration form validation process

validateStudentForm();



Slip 30:

1.Write C++ program to create two classes Integer Array and Float Array with an array as a data member. Write necessary member functions to accept and display array elements of both the classes. Find and display average of both the array. (Use Friend function)[15 Marks]

#include<iostream.h>
#include<conio.h>
 
class array2;
class array1
{
    int *a;
    int n1,i;
    public:
        void accept()
        {
            cout<<"\nEnter length of first array : ";
            cin>>n1;
            a=new int[n1];
            for(i=0;i<n1;i++)
            {
                cout<<"\nEnter value for array : ";
                cin>>a[i];
            }
        }
 
        void display()
        {
            for(i=0;i<n1;i++)
            {
            cout<<a[i]<<"\t";
            }
        }
 
        friend void avg(array1,array2);
};
 
class array2
{
    int *b;
    int n2,i;
        public:
        void accept1()
        {
            cout<<"\nEnter length of second array : ";
            cin>>n2;
            b=new int[n2];
            for(i=0;i<n2;i++)
            {
                cout<<"\nEnter value for array : ";
                cin>>b[i];
            }
        }
 
        void display()
        {
            for(i=0;i<n2;i++)
            {
            cout<<b[i]<<"\t";
            }
        }
 
        friend void avg(array1,array2);
};
 
void avg(array1 ob1,array2 ob2)
{
int s1,s2;
int i,sum,avg;
for(i=0;i<ob1.n1;i++)
{
sum=sum+ob1.a[i];
avg=sum/ob1.n1;
}
cout<<"Average of eneterd numbers are : "<<avg;
for(i=1;i<ob2.n2;i++)
{
sum=sum+ob2.b[i];
avg=sum/ob2.n2;
}
 
cout<<"\nAverage of eneterd numbers are : "<<avg;
}
 
void main()
{
array1 a1;
array2 a2;
clrscr();
a1.accept();
a2.accept1();
cout<<"\n1st array : ";
a1.display();
cout<<"\n2nd array : ";
a2.display();
avg(a1,a2);
getch();
}

2.Create a C++ class Marksheet with data members Seat No, Student Name, Class, Subject Name[], Int Marks[], Ext Marks[], Total[], Grand Total, Percentage, Grade. Write member function to accept Student information for 5 subjects. Calculate Total, Grand Total, Percentage, Grade and use setw(), setprecision()and setfill()to display Marksheet.[25 Marks]


#include<iostream.h>
#include<conio.h>
#include<iomanip.h>
#include<stdlib.h>
 
class student
{
    int rollno,total_sub,marks[10];
    char sub_name[10][10],name[20];
    float per;
    char grade;
    public:
        void getdata()
        {
            int i;
            cout<<"\nEnter roll no : ";
            cin>>rollno;
            cout<<"Enter name : ";
            cin>>name;
            cout<<"How many subject : ";
            cin>>total_sub;
            for(i=0;i<total_sub;i++)
            {
            cout<<"\nEnter subject name : ";
            cin>>sub_name[i];
            cout<<"\nEnter marks : ";
            cin>>marks[i];
            }
        }
 
        void display()
        {
               int tot_marks=0;
            int i;
            cout<<"\nRoll number : "<<rollno;
            cout<<"\nStudent name : "<<name;
            for(i=0;i<total_sub;i++)
            {
            cout<<"\nSubject name  : "<<sub_name[i];
            cout<<"\nSubject marks : "<<marks[i];
            tot_marks=tot_marks+marks[i];
            }
            per=tot_marks/total_sub;
            cout<<"\nTotal obtain marks : "<<tot_marks;
            cout<<"\n\nPercentage : "<<per;
            if(per>=70)
            {
            cout<<"\nGrade=Distinction";
            }
            else if(per>=60)
            {
            cout<<"\nGrade=A";
            }
            else if(per>=50)
            {
            cout<<"\nGrade=B";
            }
            else if(per>=40)
            {
            cout<<"\nGrade=Pass";
            }
            else
            {
            cout<<"\nGrade=Fail";
            }
            }
};
void main()
{
clrscr();
student s;
s.getdata();
s.display();
getch();
}





Slip 30

1

First file circle.js

var circle={  

    area: function(r)
  
  {
  
      var pi=3.14,a;  
  
       a=pi*r*r;
  
    
  
    console.log('area of circle is:'+a);
  
  },
  
  circumference: function(r)
  
  {
  
      var pi=3.14,c;
  
    c=2*pi*r;
  
    console.log('circumference of circle is:'+c);
  
  }
  
  };
  
   module.exports=circle;      

create second file democircle.js

var mymod=require('./circle.js');
mymod.area(5);
mymod.circumference(5);


b)
createdb.js
var mysql = require('mysql');
var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345"
});
con.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
  con.query("CREATE DATABASE hospitaldb", function (err, result) {
    if (err) throw err;
    console.log("Database created");
  });
});
create_table.js
var mysql = require('mysql');
var con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345",
  database: "hospitaldb"
});
con.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
 
  var sql = "CREATE TABLE hospital(hredno int,hname VARCHAR(40), add varchar(30),contact int)";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Table created");
  });
});
Initiate :
 C:\Users\Your Name>node createdb.js
 C:\Users\Your Name>node createtable.js


web hos
var mymod=require('./circle.js');

mymod.area(5);

mymod.circumference(5);

var circle={  
a)aa
a
    area: function(r)
  
  {
  
      var pi=3.14,a;  
  
       a=pi*r*r;
  
    
  
    console.log('area of circle is:'+a);
  
  },
  
  circumference: function(r)
  
  {
  
      var pi=3.14,c;
  
    c=2*pi*r;
  
    console.log('circumference of circle is:'+c);
  
  }
  
  };
  
   module.exports=circle;
var circle={  

    area: function(r)
  
  {
  
      var pi=3.14,a;  
  
       a=pi*r*r;
  
    
  
    console.log('area of circle is:'+a);
  
  },
  
  circumference: function(r)
  
  {
  
      var pi=3.14,c;
  
    c=2*pi*r;
  
    console.log('circumference of circle is:'+c);
  
  }
  
  };
  
   module.exports=circle;
# Hi there 👋

<!--
**riteshhhhshirole/riteshhhhshirole** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
