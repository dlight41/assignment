Hi everybody!

Let's get started. I'm using Windows 7(x64)
Please download some stuff:
1. http://www.mongodb.org/downloads version 2.6.5
2. http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html jdk 1.7_45+,
3. http://eclipse.org/downloads/download.php?file=/jetty/9.2.3.v20140905/dist/jetty-distribution-9.2.3.v20140905.zip&r=1 jetty 9.2.3

Java:
Install java and ensure you have path to bin dir in jdk installation folder.(if 64x it would looks like C:\Program Files\Java\jdk1.7.0_45\bin)

Mongodb installation:
1. Choose typical
2. mkdir c:\mongodb
3. Copy all files from installation folder to the c:\mongodb(if you are using mongo Win7(x64) by default it would be C:\Program Files\MongoDB 2.6 Standard)
4. mkdir c:\mongodb\data folder

!!! With software I give you a data configure to show how software deal with transaction started
in previous month and ended in that month.
You can skip 6-10 if you place data folder to the c:\mongodb

5. Run C:\mongodb\bin\mongod.exe --dbpath c:\mongodb\data
6. Run C:\mongodb\bin\mongo.exe
7. print db, hit enter, you'll see one db - test
8. print use test, hit enter.
9. print db.createCollection("transactions", { size: 2147483648 } ) hit enter, you'll get { "ok" : 1 }.
10. print db.createCollection("tariffs", { size: 2147483648 } ) hit enter, you'll get { "ok" : 1 }.


Jetty:
1. Unzip jetty somewhere.(here C:\jetty-distribution-9.2.3.v20140905)
2. Place csm-core.war in C:\jetty-distribution-9.2.3.v20140905\webapps
3. Print java -jar C:\jetty-distribution-9.2.3.v20140905\start.jar



Great! You environment are configured. And you ready to send requests.
When you start to look at sources please read comments.

******************************************************************************
HOW TO:
Save transaction URL - http://localhost:8080/csm-core/scpp
Path to get overview - http://localhost:8080/csm-core/scpp/tariff/overview
Set tariff - http://localhost:8080/csm-core/scpp/tariff
Path to invoice http://localhost:8080/csm-core/invoices/year/month/id.txt

Notes:
- Some methods will respond as JS with ID of record in DB.
- Software designed to work with consistent data.
- All response dates provided in UTC.

