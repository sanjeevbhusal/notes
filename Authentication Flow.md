
When user logs in, we generate 2 tokens, access token and refresh token. Access token is valid for only 10 minutes (for a day during development mode) and Refresh token is valid for 30 days.

For endpoint authentication, we send access token in request header. `Authorization: Bearer {access_token}`

Once the access token expires, frontend sends a refresh token to get the new access token. We generate new access and refresh tokens and send it to frontend. The existing refresh token is blacklisted. So, we are essentially `Rotating Refresh tokens`

This approach ensures we balance usability with security. If the access token is compromised, the attacker only has a short window before the token expires. Since refresh token is only used to get new tokens, its exposed less and has a less chance of being compromised. without the refresh token, the attacker cannot get new tokens. This approach also ensures we have a way to invalidate the compromised Refresh Token. If the legitimate user continues using the app, he will request a new access token shortly. Since we are Rotating Refresh tokens, we blacklist existing refresh tokens when a new access token is requested. This immediately invalidates the compromised Refresh token. 

