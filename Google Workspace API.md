
# Introduction

Google has a lot of services such as gmail, search engine, maps etc. A lot of this services can be managed via google workspace.

Google workspace is a term for products such as Drive, Gmail, Google Chat etc. If you want to connect your application with any of these Google workspace products, you can do so via Google cloud console.

Google Cloud Console is a centralized location for Google Workspace Products as well as its Cloud offering (similar to AWS).  You can find Google Workspace in Products and Solutions > All Products > Other Google Products. You can pin it so that it appears in the sidebar.

![[Pasted image 20230831173101.png]]


![[Pasted image 20230831173348.png]]

There are 6 main sections/options in the Google Workspace page. They are Overview, APIs, Metrics, Quotas, Credentials and Product Library.

- Overview is a place where you can get a quick overview related to all your services in Google Workspace. You can see which google workspace Apis are enabled for the project you are currently accessing. You can also see the request your project is getting. 

- APIs is a place where you can see all the enabled APIs as well as all the available APIs. You have to first enable a API in order to access it in your application. This means if your project doesnot have Gmail API enabled, it won't be able to access endpoints specific to Gmail. 

- Metrics is a place where you can see all sorts of metrics for your project. You can filter metrics by Specific API such a Gmail Metrics, Drive Metrics etc. You can see metrics such as total requests, errors, response time etc. 

- Quotas is a place where you can adjust the available quota for a service in a single day. APIs for google workspace products are not free. Google gives you generous free quota limit but you might have to buy the quotas if you exceed the free limit.  

- Credentials is a place where you can create, edit and delete credentials to access the APIs for enabled Google Workspace Products. 

- Product Library is a place where you can explore all the available Google Workspace Products in more detail.


# Google Workspace API Explorer

Google has a Workspace API Explorer at https://developers.google.com/workspace/explore. You can click any API you want and view the details of the API. You can see the parameters the API takes and execute the API itself in the browser. 

You also have to perform authentication/authorization directly in the browser itself. 


# 4 Steps to Working with Google Workspace Apps


1) Create a Google Cloud Project.
2) Enable APIs according to your requirement.
3) Set up OAuth Consent Screen
4) Create access Credentials


We have already discussed about Step 1 and Step 2 above. Step 3 and Step 4 falls under Authentication and Authorization. Now, we will discuss more about authentication and authorization with Google Workspace API.



# Authentication and Authorization with Google Workspace API

Authentication is a mechanism used to verify the identity of the user making the request whereas Authorization is a mechanism used to verify the access rights for a particular resource. Authentication is a prerequisite for Authorization.

Consider the following simplified example of a hotel reservation. When you arrive at the hotel, the front desk clerk requests your ID to verify your reservation. Your ID _authenticates_ you to the hotel. The front desk clerk gives you a hotel key. This key gives you access to certain resources at the hotel such as your hotel room, the gym, and the business center. The hotel key _authorizes_ you to access those resources.

There are mainly 2 parts to authentication, Authenticating your app and Authenticating your user.

- **Authenticating your app**: When you make a request to any google workspace API, you have to authenticate yourself. This authentication is not for the end user. This is for Google to know which project is sending the request. Google stores all the metrics for requests made to its API's. Hence, it should know which project is the one making the request. It does so by using a API token. You can generate a API token in the API and Services > Credentials section. The token uniquely identifies your project. You have to send this token with every request you make to google Api.    

- **Authenticating your end user:** Once the app is authenticated, google needs to authenticate the end user who wants to access their resources. If your application needs to have access to user's public profile (email, name, profile picture etc), then you must first ask the user for permission. You cannot just access their private/public information through google API. Google wants you to first configure the permission you need in the  OAuth Consent Screen Section located at API and Services > OAuth Consent Screen. 
	
	 - **OAuth Consent Screen**:  This is a screen that will be shown to end user. This screen contains information regarding the application name, developer email address and permissions the applications wants from user. User can either consent to giving all the permissions asked in the consent screen or reject it completely. They cannot choose to give consent to some of the asked permission and reject others. While confThe contents shown in the Consent Screen has to be configured 





![[Pasted image 20230831181838.png]]




