
Django Ninja automatically provides a documentation page via swagger UI or Redoc. The documentation page is served in route `/api/docs`. 

To go to the documentation page locally, hit: `http://localhost:8000/api/docs`. It is available without any authentication.

However, it is not available in the production application. 


We have a django app called `documentation`. This app initializes a ninja router and exposes a api endpoint `/docs`. This endpoint is protected via app authentication. 

This router is then added to the main ninja router of the application. So, to reach the `/docs` endpoint, you need to hit `http://localhost:8000/api/documentation/docs`