Slack App have full access to the all the features offered by Slack. 
- They can send messages using rest apis (web apis) or webhook.
- receive notifications of user events via Events API.

Slack can also do other things that human cannot 
- Apps can have a separate space to have conversations with user. This space is called Home Tab. This is like talking to a user. 
- Apps can also have shortcuts. Using shortcuts, user can give commands to a application. Application can then respond to these commands. These commands are different compared to messages since commands are pre-defined. 
- Apps can publish interactive components such as a button. When user presses that button, certain interaction can take place.

### App Surface
A App Surface is anywhere a app can display some information or interact with user. Some of the app surfaces are App Home, Modals and Messages. 

#### App Home
App Home represents the UI that is displayed when you click on the app. It is like a app's profile page but with other features. It has 3 sections/tabs. 
- Home: This tab can be fully customized by app to display whatever it wants. Google calendar app lets user create a new meeting and edit some settings from this tab.
- Messages: This tab is used to interact with application by sending messages. You can send a message to a application and a application can respond to it. A Application can also initiate the conversation. Google calendar app sends you a summary of all the meetings you have for a given day early in the morning.  
- About: This tab serves as a about page for the application. You can give more details on how to interact with the app, the commands app supports etc in this tab. 


### Interactivity
Interactivity means having 2 way conversation between a slack application and a user. It is a 2 step process.
- Something happens that triggers/invokes the interaction.
- The application respond to the interaction.

There are multiple ways to trigger the interaction and multiple ways a app can respond to the interaction. 

#### User Triggers the interaction
- User can interact with your application by using app surface. As discussed above, app surface represents App Home, Modals and Messages. User can go to App Home and send a message in Messages tab. Or they can go to App Home and press some button in Home tab. 
- User can interact with your application by 
- User can use slash commands exposed by your application. 
#### Interaction gets Triggered without User input
- Interactions can be scheduled at a fix time. For eg: Google calendar app posts a message in the Home Tab of App Surface at sharp 7 am. A interaction gets triggered at this time automatically and google calendar app responds by posting a message. This is like a cron job. 
- Interactions can be initiated by external services. For eg: Everytime sentry catches a error, it sends the error to a slack channel. The error is sent via sentry slack application. A interaction gets triggered when sentry catches a error and the sentry slack app responds by posting a message. 
- Interactions can be initiated because of some events. A user might join a channel in slack and that might trigger a interaction. A slack app can then respond with some welcome message. Although the user joined a channel and that's what caused the interaction, the joining user had no idea about the app. The user didnot directly interact with the application. 