
When user logs in, we generate 2 tokens, access token and refresh token. Access token is valid for only 10 minutes (for a day during development mode) and Refresh token is valid for 30 days.

For endpoint authentication, we send access token in request header. `Authorization: Bearer {access_token}`

Once the access token expires, frontend sends a refresh token to get the new access token. We generate new access and refresh tokens and send it to frontend. The existing refresh token is blacklisted. So, we are essentially `Rotating Refresh tokens`

This approach ensures we balance usability with security. If the access token is compromised, the attacker only has a short window before the token expires. Since refresh token is only used to get new tokens, its exposed less and has a less chance of being compromised. without the refresh token, the attacker cannot get new tokens. This approach also ensures we have a way to invalidate the compromised Refresh Token. If the legitimate user continues using the app, he will request a new access token shortly. Since we are Rotating Refresh tokens, we blacklist existing refresh tokens when a new access token is requested. This immediately invalidates the compromised Refresh token. 

https://django-rest-framework-simplejwt.readthedocs.io/en/latest/blacklist_app.html

In order to know if a refresh token has been blacklisted, we need it to store it in database. Overtime we will have a lot of tokens that have been blacklisted. In order to clean those tokens, we also run a management command that cleans these tokens. The management command is run every day as a cron job. 

**In this flow, is it possible to remove all the tokens such that every logged in device will be logged out ?**
It is not possible to log out every device instantly. We can blacklist all the refresh tokens which will ensure we do not generate a new refresh/access token pair next time it is requested. However, we do not have a mechanism to blacklist access tokens. access tokens are the ones that are used to authenticate a user in an endpoint. These tokens are short-lived. When the token expires and user requests a new access token, the server will reject the request since the current refresh token has already been blacklisted. 

We donot check if a token is valid or not in every request. This increases the request speed. But this means we also can't detect if the associated refresh token has been blacklisted. **We are trading security for speed.**
Fortunately our access tokens are short lived (10 minutes), so once the time passes, the user will be logged out from all devices. The user can only login again by providing valid password. 