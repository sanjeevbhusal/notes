#security #javascript #localstorage #authentication

the main reason boils down to security concerns in local storage. if someone is able to run javascript on your website (Cross site scripting attack), they can retrieve the information stored in local storage and send it to their own domain. This puts user's security at risk.

	If your site contains code from third party libraries, you are never sure if any of the library gets compromised. Hence, it is better to just use cookies to store credentials as cookies cannot be accessed from javascript code.

The article explains it further.

https://www.rdegges.com/2018/please-stop-using-local-storage/