# Java-Notes
Java Notes (Points and Code)

Coupling: 
Tight – Changes in one are reflected in another. Abstract Classes are recommended!
Loose – Changes in one do not affect the other partner. Interfaces are recommended!
Example:  Vehicle and Employee Classes are not related but Print() can be used for both of them. Hence Create a Printable Interface.
Interfaces can have “ public  static  final “ Variables only!!!

Marking Or Tagging Interfaces:
Already Built-in interfaces to help Devs.
Eg: Clonable(To create DEEP Copies of obj)
Serializable (Persisting to save the state of the obj)
Just a Tag To get the authorization or permission from the JVM.

String:
String Buffer:
Synchronized or Thread Safe.
It is Mutable.
Returns False in the equals method.
String Builder:
…

Inner Classes:
Used for more Modularity.
Automatically become private class of the outer class. 
It can use even the Private members of Outer Class.
No inner class can extend any other classes.
Ex: Human Body with lakhs of methods, again divided into many categories.
Types:
Inner Class
Static Inner Class (Cannot Implement but can only Extend) 
Method Local Class {
Class inside a Method of Outer Class.
Lifetime of the class is same as of the method. 
Cannot Create an object of this class outside the method. 
Simply an Overhead for the Compiler 
}
Anonymous Inner Class {
Cannot Extend or Implement
}

IO Packages: File Class (Abstract Operations such as Opening, closing) , RandomAccessFile (Read from  a particular point and not from start by using Seek() )

Streams – Flow of Bytes (Go for Stream Classes when you deal with Bytes)
Types: Reader , Writer

Reader/Writer – Unicode Characters
Types: InputStream (FileInputStream, DataInputStream, ObjectInputStream)
OutputStream (FileOutputStream)

Serialization:
To Store the State of an Object. 
Encrypts and serializes the data.

Auto Boxing:
Automatically convert primitive to Wrapper Type.
Auto Un-Boxing:
Automatically convert Wrapper type to Primitive data type.
Interfaces:
Interfaces can Extend other interfaces But 
Classes must Implement the Interfaces.
Collection: (Map is not a part of Collection Interface and Collections is a Class)
Collection(i) is Classified into : List(i) and Set(i), Stack and Queue

List:
Ordered
Duplicates Allowed 
n NULL allowed
List(i) has ArrayList(i), LinkList(i) and Vector(i);

Set:
Ordered
Duplicates Not Allowed 
only 1  NULL allowed
Set(i) has HashSet(i) and SortedSet(i)   NavigableSet(i)  TreeSet(i) 


Map:
Only in case of Key and Value data.
Duplicate Keys not allowed but Values can be Duplicated!
1 null for keys, Multiple nulls for values.
Map(i) is Classified into  HashMap and TreeMap(c)
TreeMap:
Sorting is According to the Keys
Iterator Interface:
Not a part of Collection(i)
ListIterator(i)  extends Iterator(i).
ListIterator can update but not Iterator(i).
What to Use and When to Use:
ArrayList is Faster than Vector (Which is now known Legacy class)
When dealing with Hashing Concept, Make sure to override both Equals and hashCode methods.
If you want Sorted, Go for TreeMap.
If you want Duplicate and Sorted, Go for Comparable (java.util, compareTo(), Can Compare only one Object) and Comparator(java.lang, compare(),Can Compare two Object)
Iterator :
Always points to a location before data, to -1 (Not 0);
That is why we have hasNext(); 
JDBC Notes
Four Types:
1. JDBC ODBC (2 Stages of Data Conversion, Every Client must have a ODBC Driver)
2. The Native API Driver (Depends on OS, Vendor –Based Driver, Simple Distributed Systems)
3. Net Protocol All Java Driver (Most Efficient and Stable, Web Based)
4. Pure Java Driver (Written in Java, Fastest Among all Drivers, Vendor-Specific)
The Process:
1. Load the Driver.  (Explicitly load the Class, and Link the MySQL-Connector)
2. Connect to the Database. 
The First Two Steps are Common for every Connection.
3. Prepare Statement and Fire the Query.
You can use Either Statement Interface (For DDL Statements, Or Only Once for Static Data)
or  Prepared Statement (For runtime or Parameterized Queries)

4. Read and Get the Data from DB, Using ResultSet!
4. Close the Connection (If not, Then Changes might not get Committed!)
PLSQL:
On MySQL Terminal,
delimiter //  	(Change the Delimiter, since we use a ‘ ; ‘ for our statements)
create procedure MyProcedure (IN eid int, IN ename varchar(20))
begin
insert into emp values (eid, ename);
end
//
On Our Interface,
CallableStatement cst = con.prepareCall("call MyProcedure3(?,?)");
Scanner sc = new Scanner(System.in);
			
System.out.println("Enter ID: ");
int id = sc.nextInt();

cst.setInt(1, id);
cst.registerOutParameter(2, Types.VARCHAR); 
			
cst.execute();
ResultSet rs = cst.executeQuery("select * from emp");
while (rs.next()) {
	System.out.println(rs.getInt(1) + " " + rs.getString(2));
}
System.out.println("Name From Database: " + cst.getString(2));
System.out.println("Executed! Closing the Prepared Statement!");
cst.close();
System.out.println("Closing the Connection!");
con.close();


Database Metadata:

getDatabaseMetadata();


Java API XML Processing (JAXP , XMP Parser in JAVA)

Package Name : Java.xml.parsers

Two Ways to Parse XML in JAVA:  SAX  and DOM

SAX: Simple API for XML (Used for Large XML files)
Event Driven. Read only, Cannot Update!
Reads some part of the file and parses the data.
Parsers send event to 

DOM: Document Object Model (For Reading as well as Updating)
Good for Complex Documents where Your Application number of times
Common Methods:
Node.getNodeType() – Type of the Underlying object
Node.getNodeName()
Node.getNextSibling()
Node.getPreviousSibling()
Node.getAttributes()

We Use Document Factory and Document Builder

 
Logging:

Logger for letting the Dev know till where the Program is running correctly.

Levels:
SEVERE
WARNING
IN FO
CONFIG
FINE
FINER
FINEST


DATE Class : 

4 Classes:
Date, DateFormat, SimpleDateFormat, Calender

DateFormat: To Display in some Pre-Defined Format (Small, Medium, etc)
SimpleDateFormat : User Defined Format
Calender :  Used to set Date rather than using the system time.


Generics :
ArrayList<Vehicle> varr = new ArrayLsit<vehicle>();
ArrayList<FourWheeler> farr = new ArrayLsit<FourWheeler>();
ArrayList<Audi> audiarr = new ArrayList<Audi>();

Static void disp(List <? super FourWheeler> obj){
	
}

The ? is like a WildCard and takes in any Object
Variations:
? extends Vehicle : It takes Objects of Vehicle and its sub classes. Not Some other Class (Like Employee)
? super FourWheeler : This takes only the Super Classes of 4 Wheeler Class (Like Vehicle and Object)

