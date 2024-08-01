
A Workflow is created to accomplish certain task. For eg: 
- Send a Message to a channel 
- Add a emoji reaction to a slack message.
- Create a new google meet etc.


A workflow is broken down into multiple steps. Each step requires certain input and produces certain output. Steps are executed in order. For example, to Send a Message to a channel, you need at least one step.

This step will require user to input a message and channel name. Then, this step will do a api call to slack to post that message. Once the api call is successful, the step is over. Since there is only one step, the workflow will end here. 

What if you also want to store the input message in a google sheet ? You can then create a new step. This step will take the output of previous step (the message) and make a api call to google to store the information. What happens if you again want to send the link of the google sheet to a channel ? You need another step. 

However, you could also do all these in a single step. It would get a bit complicated but it is possible. 

Since steps such as sending a message to slack channel is very common, slack already provides these steps. These steps behind the scenes use slack api to send message. 

What if you want to have a workflow that takes some user input in a form, then do a api call to a endpoint, retrieve the response and post in in a slack channel ? You can make this workflow possible in a single step or multiple steps. 

- First Step, Create a form to take user input
- Second Step, Take the output of first step and make a api call to the endpoint.
- Third Step, Take the output of second step and post it to a slack channel. 

When should you create a single step or multiple step to complete a certain task ? If a task is very specific (such as calling your api) and sending response to a slack 




Manifest file defines what a application name will be. Manifest files have workflows. A workflow has multiple steps. A workflow is triggered by a event. 

Some of the possible events: 

- Link Event

