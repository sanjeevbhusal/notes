

Next-auth is a library used in Nextjs for authentication purposes. This library handles most/all of the authentication needs for almost all applications. 

This library creates both frontend and backend part of the authentication. For backend authentication, you need to configure this library with some of the options. You need to put this configuration in /src/api/[...nextauth]/route.ts file. [...nextauth] directory is also known as catch all directory.

Next-auth supports email and pasword based authentication as well as authentication with google, github, microsoft etc. All of the authentication with all these third party providers will be taken care of by next-auth itself. 

Next-auth has a concept of Provider. If you want to authenticate with Google, you need to configure next-auth to use Google Provider. If you want to authenticate with simple email and password, you need to use Credentials Provider. All of these Providers are present in the package itself. We just need to tell next-auth which are the providers we want to use and configure those providers.




