

- Donot create notification for commenter themselves.
- If action is create
	-  The person creating the thread is the submitter. If the recently created comment isn't from submitter i.e. `commenter != submitter` , send notification to the submitter. If not, submitter should not receive the notification.
	- We then send notifications to all the mentioned users in the comment.
	- We then get all the previous commenters and send them notifications. While getting previous commenters, we exclude certain users. These users are 
		- Submitter user. We exclude Submitter user because we already sent a notification to submitter user in the first point above. In case `commenter = submitter`, we donot send notification to submitter in the first point. We also donot want to send notification here since the person commenting was submitter themselves.
		- Mentioned users. We do this because we already sent notification to mentioned users in point 2 above.


Current flow:

- We create a set called `non_mentioned_users_to_notify`. This set will hold users that are not mentioned but have to be notified. Previously, these users would contain the thread creator if he was different than the comment submitter. 
- Currently as well, if `commenter != submitter` , add submitter to the above set. 
- We then get all the previous commenters and add them to the set. These commenters might also include submitter. point 2 might have added submitter to the set. Since it is a set, submitter will also appear once in the set. However if the submitter is the commenter as well as is a part of previous commenters, then he will also be added to the set. **We probably donot want this. We donot want to send notification to the user that is making the request. This applies even if that user is part of previous_commenters
- If questionnaire task has a assigned customer user, also add them to the set.
- If we have mentioned users and if some of them are part of previous commenters, then they are added to the set. We remove them since we send different notification to them. 
- We then remove commenter from the set.