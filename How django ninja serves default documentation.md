
When you hit `http://localhost:8000/api/docs`, a page will be displayed showing all the documentation for the application. Django Ninja uses Open API format to display documentation. You can choose if you want to use Swagger UI or Redoc for displaying those documentation. 

When you visit the docs page, these are the things that happen.

- Django Ninja will take all the registered api endpoint and make a json file called openapi.json. This json file has all the api routes registered, the params type that they take, the response type that they send etc.  
- Django ninja then sends a html file to frontend. This html file is mostly empty and only contains

Django Ninja will take all the registered api endpoint and make a json file called openapi.json. It then serves a doc file  this file alongside other html, css and javascript files. 