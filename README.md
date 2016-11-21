1.  Creating OAuth 2.0 client IDs for the backend

You need to create a client ID for each client, in this example for the web client. The client ID is added to the backend API (in Constants.java) and to the web client.

To create a client ID:

1.Open the Credentials page for your project:
Go to the API Manager > Credentials page


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
1. Update the value of `application` in `appengine-web.xml` to you project name.
2. Optional step: These sub steps are not required but will enable the "Authenticated
Greeting" functionality.
   1. Update the values in [src/main/java/com/example/helloendpoints/Constants.java](src/main/java/com/example/helloendpoints/Constants.java) to reflect the web client ID you have registered in the
[Credentials on Developers Console for OAuth 2.0 client IDs][6].
    1. Update the value of `google.devrel.samples.helloendpoints.CLIENT_ID` in
[src/main/webapp/js/base.js](src/main/webapp/js/base.js) to reflect the web client ID you have registered in the
[Credentials on Developers Console for OAuth 2.0 client IDs][6].

Running the project :--
1. `mvn clean install`
2. Run the application with `mvn appengine:devserver`, and ensure it's running
   by visiting your local server's address (by default [localhost:8080][5].)
3. Deploy your application to Google App Engine with `mvn appengine:update`
    https://your_project_id.appspot.com

4. Test the authenticated version

 https://your-project-id.appspot.com/_ah/api/explorer
