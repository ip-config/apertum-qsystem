=Setup instructions for customer care automation system=


### Step 1. Preparing to installation. ###
Prior to the installation make sure, that you have installed MySQL DBMS version 5.5 or later and OracleJRE version 1.7 or later. To check the JRE installation do the following:
Start->Execute->cmd-> java -version.

It is recommended to install graphical utilities for MySQL DBMS.

### Step 2. Start of the system installation. ###
Microsoft Windows:
Double click on install.jar.
Linux (a universal method suitable for any OS):
Installation start with the command line:
Open the folder containing the install.jar file and execute the following command
> java -cp install.jar com.izforge.izpack.installer.Installer
> !!!  java -jar install.jar

### Step 3.  System installation. ###
Press ''Next'' in the welcome window, in the next system presentation window press ''Next'' also, the next window shows system build version, build date and other product information, press ''Next''.
> The next window allows you to choose system installation folder, the default folder is the drive with OS installed to  the Program Files, press ''Next''. If there is no folder, the installer will create in automatically.

Then you are requested to choose the system components to be installed:
- application files and libraries (default, can not be changed).
- operator's workplace (default)
- server
- administration
- place of check-in
- documents the ''documents'' include: user manual and administrator manual, you can always use the context help.
As you have chosen the necessary components press ''Next''.

### Step 4. System setup. ###
As you finish to choose the components, you arerequested to enter the addresses and port names for cooperation of the system components:
- server address
- server port
- check-in address
- check-in port
- client port
- to make the check-in multilingual.
Please note! In the case of wrong server addresses and ports you can change them in the **.bat fails of the system installed components.
As you enter the data press ''Next''. You will see the list of the components chosen, if you are agree press ''Next''.**

### Step 5. Installation end. ###
The system program components installation begins. When it finished press ''Next''. You will see the window requesting you to put the shortcuts to the desktop. Shortcut creation to the specified folder is made as a default.

When the installation is finished, you may have to install some applications and drivers, if you have not installed them earlier.

### Step 6. How to add JavaFX library. ###
JavaFX is required from the version 1.3.1. The library is distributed as a part of OracleJRE, but usually it is not used as a default. To add the library copy a file from the one folder to another. Copy the file < jre >\lib\jfxrt.jar to the folder < jre >\lib\ext. That's all.

The mentioned above is enough to install the client module.

Now you have all the necessary components installed to your computer. You have only to activate the DB and set up the system to use the DB.

### Step 7. Data base activation. ###
**You have to use the utf8 encoding. Enter the appropriate settings to the MySQL administrator or to the my.ini(my.cnf). Example:
[mysql](mysql.md)
default-character-set=utf8
[mysqld](mysqld.md)
collation\_server=utf8\_unicode\_ci
character\_set\_server=utf8**

You can find the activation script qsystem.sql in the DB folder. The script creates a data base, necessary tables and fills the tables with starting data. If you have a DB and want to update it's version, you have to use an sql-script to update it. You may use the MYSQL DBMS console to activate sql-scripts, but t is better to use the MySQL Query Browser application, which you can download from the Internet for free and install to your computer. Add a DBMS user and give it access to the DB.
MySQL DBMS settings include wait\_timeout parameter, this is time in seconds that takes the server to watch inactivity in the non-interactive connection prior to closing it. The default value is 28800 seconds. If the server works at night or during long holidays, an error occurs at the work start, as DBMS can not address the request. You may set up the parameter in MySQL configuration file. It is the my.ini file in Windows, you may clarify it in server configurations of MySQL Administrator application. Add to the file the following line "wait\_timeout=xxxx". The server maintains connection by DBMS questioning on a hourly basis. Take that into account if you have more strict settings.

### Step 8. System configuration for DB. ###
Open the admdbcom.bat file in the application folder for OS Windows or the admdbcom.sh file for OS Linux. Open the admspt.bat file to setup the console. Enter correct data on the DB connection. Save the parameters. You may setup several DB servers. Mark one of them as current, and it's configurations will apply.

### Step 9. Configuration filling and server settings. ###

Open the StartAdmin.bat file. First, enter to the Administration program as "Administrator" without password. Fill in the Operators list, create the Service tree, assign services to operators. Create Service rendering schedule. Don't forget to save changes.

### Step 10. Main and operator's boards positioning. ###

Since version 1.3.7 specify the monitor number for the main board in the editor board in the central part. The parameters "number of additional monitor to display". That is enough. If the monitor is not plug in, coordinates from clientboard.xml and  mainboard.xml will be used. When parameter is 0, then the board is disabled.

There are 2 files in the < Qsystem >\config\ folder: clientboard.xml and mainboard.xml (for client machine and server respectively). These files contain board positioning coordinates, you can also turn it on\off there. If you have not connected the second monitor, the program opens it all on one monitor. To send the board to the second monitor enter to the clientboard.xml and mainboard.xml files the second monitor coordinates. Enter the x and y parameters to the setting files:


&lt;Board visible="1" x="-500" y="10" Name="Save table configuration"&gt;



The parameters allow to identify the board location and open it on the second monitor. When the second monitor connects, you need to upscale the desktop on it. The upscaled desktop has its own coordinates in relation to the main desktop. You have to enter coordinates of a point included to the upscale. Positioning will be carried out by that point. I.e., the upper left corner of the table will be positioned by the point. Remember, that the coordinates of the main monitor upper left corner are (0,0). For example, an aux. monitor is connected, the desktop is upscaled on it on the left from the main desktop. The aux. monitor has the extension of 640x480 px. The upper left corner of the auxiliary desktop has the coordinates (-640, 0) in relation to the main desktop. The settings are x="-500" y="10", which means that the board is positioned to the aux. desktop, but not to the aux. monitor corner. It is positioned 10 pixels down and 140 pixels from the edge of the aux. monitor. After that the desktop expanses to the entire screen.

After completion of all the steps the system is ready to use.