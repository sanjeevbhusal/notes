

Next-auth is a library used in Nextjs for authentication purposes. This library handles most/all of the authentication needs for almost all applications. 

This library creates both frontend and backend part of the authentication. For backend authentication, you need to configure this library with some of the options. You need to put this configuration in /src/api/auth/[...nextauth]/route.ts file. [...nextauth] directory is also known as catch all directory.

Next-auth supports email and pasword based authentication as well as authentication with google, github, microsoft etc. All of the authentication with all these third party providers will be taken care of by next-auth itself. 

Next-auth has a concept of Provider. If you want to authenticate with Google, you need to configure next-auth to use Google Provider. If you want to authenticate with simple email and password, you need to use Credentials Provider. All of these Providers are present in the package itself. We just need to tell next-auth which are the providers we want to use and configure those providers.

Configuring each provider takes different arguments. 

- Credentials Provider: This provider will need you to specify which fields you need, what should be their type, label etc. Based on this Input, it will automatically generate the form. You should also specify the logic for validating the user supplied input against your database schema. After successful validation, you might want to return to a certain url. You should also specify it. 

-  Google Provider: This provider will need you to specify certain values such as Secret Key, Client Key etc that can be obtained via Google Developer Console. You also need to specify some other details discussed in Credentials Provider


In nextjs, if you want to expose api's you should create function which name are based  upon HTTP Verb such as GET, POST.  Since, next-auth is a authorization library, it handles both get request as well as post request.  Get request is needed if you want to validate a user session. POST request is needed if you want to send the credentials inorder to log in.

Next-auth makes it preety easy to declare both GET and POST functions.  You have to create a function known as handler. Then you need to export this function as both GET and POST. This way, whenever there is an api call to this route, nextjs will either call GET or POST function. Although both GET and POST function is the same, next-auth under the hood will run the correct code based upon the request verb.


Next-auth requires a secret key in order to encrypt jwt token. So, you need to declare a secret key in the environment file. 

Once you have exported both GET and POST function and set up the secret key, some routes will be created for you by next-auth. One of such route is localhost:3000/api/auth/signin. When you visit this route, you will see a signin page. The signin page could have multiple options to signin such as Github, Google, email and password etc based upon the providers you selected while configuring next-auth. 



