

- Donot create notification for commenter themselves.
- If action is create
	-  The person creating the thread is the submitter. If the recently created comment isn't from submitter i.e. `commenter != submitter` , send notification to the submitter. If not, submitter should not receive the notification.
	- We then send notifications to all the mentioned users in the comment.
	- We then get all the previous commenters and send them notifications. While getting previous commenters, we exclude certain users. These users are 
		- Submitter user. We exclude Submitter user because we already sent a notification to submitter user in the first point above.


Current flow:

- We create a set called `non_mentioned_users_to_notify`. This set will hold users that are not mentioned but have to be notified. Previously, these users would contain the thread creator if he was different than the comment submitter. 
- Currently as well, if `commenter != submitter` , add submitter to the above set. 