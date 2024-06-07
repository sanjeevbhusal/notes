
When you hit `http://localhost:8000/api/docs`, a page will be displayed showing all the documentation for the application. Django Ninja uses Open API format to display documentation. You can choose if you want to use Swagger UI or Redoc for displaying those documentation. 

When you visit the docs page, these are the things that happen.

- Django ninja sends a html file to frontend. This html file is mostly empty and only contains link to css and javascript files. This file will be different depending upon if you configure Ninja to use Swagger UI or Redoc.
- When browser renders the html, it fetches all the css and javascript files linked in the html. These are mostly fetched from the nearest CDN. 
- This html file also has a link to `/api/openapi.json`. This is a predefined url in django ninja. When request gets sent to this url, django ninja will take all the registered api endpoint and make a json file called openapi.json. This json file has all the api routes registered, the params type that they take, the response type that they send etc.  
- When css, javascript, and openapi.json file is downloaded, javascript will then construct a html page. This page is the final documentation page.

