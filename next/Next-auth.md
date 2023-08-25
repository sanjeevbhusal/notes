

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

Lets say, we used CredentialsProvider while configuring next-auth. This means at this route we will see a input page for email and password. We fill the data and make the request.
The request goes to localhost:3000/api/auth/callback/credentials. This is a route that is exposed by next-auth itself. When the request reaches the route, next-auth runs the code that we defined while setting up Credentials Provider. The code generally includes logic to  make a database call and validate if the user exists.

If the user exists, next-auth will return a 200 status code. However, next-auth will set a redirect location as well. This means, the browser will redirect the user to some other location. This is expected since we donot want user to be in login page if the request was successful. We donot have to explicitly run some redirect function just as we used to do in react-router-dom.  This means, when you inspect the request through devtools, you will find couple of things such as 

- The status code will be 302 found.  
- The response header will consist of location property. This is the url where browser will redirect the user.
- next-auth will also set the session cookie for subsequent request validation.

Now, the next important part will be to actually get the user present in the session in order to know who is the logged in user. The way we do this actually differs in client component and server component. In total, you might need session information in 3 places.

- React Server Component (runs in server)
- Api routes  (runs in server)
- Client Component (runs in browser)

- React Server Component:  In order to get session information from react server component, you can use a hook called getServerSession() and pass the options object that you configured while setting up nex-auth as a argument.

- Api Routes: It is same as React Server Component. You just call getServerSesscion() in the api route itself.

- Client Component: Next-auth cannot decode the jwt session token in the client. It needs to do it in the server. Hence, the first-time you try to get session information in the client, a network request will be made. After the session data arrives, next-auth will store this session information in a Context Provider. This Context Provider and the hook that will retrieve the data from the provider is already made available by next-auth.

next-auth provides 2 function called signIn and signOut. signIn function will redirect user to signin page whereas signout function will remove the session from cookie.



