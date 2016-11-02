appengine-endpoints-helloendpoints-java-maven
=============================================

Set up instruction prior to running the project

1.Download jdk1.8 from this link 
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

2. Updating the PATH Environment Variable:--

To set the PATH variable permanently, add the full path of the jdk1.8.0_111\bin directory to the PATH variable. Typically, this full path looks something like C:\Program Files\Java\jdk1.8.0_111\bin.
Set the PATH variable as follows on Microsoft Windows:

Click Start, then Control Panel, then System.

Click Advanced, then Environment Variables.

Add the location of the bin folder of the JDK installation to the PATH variable in System Variables. The following is a typical value for the PATH variable:

C:\WINDOWS\system32;C:\WINDOWS;C:\Program Files\Java\jdk1.8.0_111\bin

3. Add a new entry of JAVA_HOME=c:\Program Files\Java\jdk1.8.0_111 in the environment variables.

4. Install Maven from this link

http://maven.apache.org/download.cgi

5. Check the path where maven is installed and extract it. Copy the path of the bin directory

C:\apache-maven-3.3.9\bin

6. Go to Environment variable and append it in the PATH  for example 

Adding to PATH: Add the unpacked distribution’s bin directory to your user PATH environment variable by opening up the system properties (WinKey + Pause), selecting the “Advanced” tab, and the “Environment Variables” button, then adding or selecting the PATH variable in the user variables with the value C:\Program Files\apache-maven-3.3.9\bin at the end.

7. Open a new command prompt (Winkey + R then type cmd) and run mvn -v to verify the installation and java -version

8. Install git from this link

https://git-scm.com/download/win

9.  Creating OAuth 2.0 client IDs for the backend

You need to create a client ID for each client, in this example for the web client. The client ID is added to the backend API (in Constants.java) and to the web client.

To create a client ID:

1.Open the Credentials page for your project:
Go to the Credentials page


2.Click Create credentials > OAuth client ID.


3.Click Configure consent screen


4.Supply a product name, which you can change later, and click Save.


5.Select Web application as the application type to display the settings for web clients.


6.Specify a name for the web client.


7.In the textbox labeled Authorized JavaScript origins, specify the App Engine URL of your backend API, for example, https://your_project_id.appspot.com, replacing your_project_id with your actual App Engine project ID. Be sure to specify https:// in the URL, not http.

starNote: If you are testing the web client locally and want to try the auth protected feature, you must specify http://localhost:8080 in the textbox labeled Authorized JavaScript origins, using http://, not https://. You can always change it back to the deployment URL later.


8.Click Create.


Note the client ID that is generated. This is the client ID you need to use in your backend and in your client application. You can always return to the Credentials page later to view the client ID.



## Setup Instructions for the project
1. Update the value of `application` in `appengine-web.xml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Optional step: These sub steps are not required but will enable the "Authenticated
Greeting" functionality.
   1. Update the values in [src/main/java/com/example/helloendpoints/Constants.java](src/main/java/com/example/helloendpoints/Constants.java) to reflect the web client ID you have registered in the
[Credentials on Developers Console for OAuth 2.0 client IDs][6].
    1. Update the value of `google.devrel.samples.helloendpoints.CLIENT_ID` in
[src/main/webapp/js/base.js](src/main/webapp/js/base.js) to reflect the web client ID you have registered in the
[Credentials on Developers Console for OAuth 2.0 client IDs][6].
1. `mvn clean install`
1. Run the application with `mvn appengine:devserver`, and ensure it's running
   by visiting your local server's address (by default [localhost:8080][5].)
1. Deploy your application to Google App Engine with `mvn appengine:update`

