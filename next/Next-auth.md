

Next-auth is a library used in Nextjs for authentication purposes. This library handles most/all of the authentication needs for almost all applications. 

This library creates both frontend and backend part of the authentication. For backend authentication, you need to configure this library with some of the options. You need to put this configuration in /src/api/[...nextauth]/route.ts file. [...nextauth] directory is also known as catch all directory.

Next-auth supports email and pasword based authentication as well as authentication with google, github, microsoft etc. All of the authentication with all these third party providers will be taken care of by next-auth itself. 

Next-auth has a concept of Provider. If you want to authenticate with Google, you need to configure next-auth to use Google Provider. If you want to authenticate with simple email and password, you need to use Credentials Provider. All of these Providers are present in the package itself. We just need to tell next-auth which are the providers we want to use and configure those providers.

Configuring each provider takes different arguments. 

- Credentials Provider: This provider will need you to specify which fields you need, what should be their type, label etc. Based on this Input, it will automatically generate the form. You should also specify the logic for validating the user supplied input against your database schema. After successful validation, you might want to return to a certain url. You should also specify it. 

-  Google Provider: This provider will need you to specify certain values such as Secret Key, Client Key etc that can be obtained via Google Developer Console. You also need to specify some other details discussed in Credentials Provider


