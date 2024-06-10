Securitypal also needs to be able to communicate with external applications such as slack, salesforce etc do to some tasks. Example: Create a Questionnaire Task from salesforce. We have a api endpoint defined that can do this. However, this api endpoint is used by securitypal application. So, salesforce won't be able to communicate with this endpoint. 

To solve this, we create another endpoint that creates questionnaire task but is authenticated differently. We cannot make this api endpoint unauthenticated as we need information on who is sending the request.

Hence, we need to introduce API Tokens in the application. Once the user creates a api token, they can configure salesforce to include this this token when sending request for creating questionnaire task. The endpoint will validate the token and authenticate the request.  

We will also need a documentation page to document all the available api endpoints,  request params schema and returned response schema. For this, we use Django Ninja's default documentation setting. [[How django ninja serves default documentation]]

Currently, we expose 2 main urls that are publicly available. `/api/v1` and `/api/v1beta`/ . `/api/v1beta` is the new implementation of `/api/v1`. This new implementation contain better information around the schemas of the public endpoints.  