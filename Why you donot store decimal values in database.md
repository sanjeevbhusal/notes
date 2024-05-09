
In database, we try not to store decimal values as much as possible. This is because of something known as precision errors in programming languages. Example: You might have stored 3.88 in database but when you get that in javascript, it might be represented as 3.799999. This is specially true in payments app where you donot even want to lose a single cent of users money. 

However, user will want to move money in decimals as well. Example: Transfer 75 cents from Account A to Account B. How do you handle that ? 

In order to handle such requirement, every payment system will multiply the value with 10 or 100 or 1000 etc. Assuming your payments app multiplies the value by 100, if you want to store 0.75 cents, it will be stored as 75 and not 0.75 in database. When the balance is returned from backend to frontend, frontend will then truncate the value by 100. So, even if backend returns 75, frontend will display it as 0.75 (`75/100`). 

This is not limited to only decimal values. If you want to store 100 dollars, it will be stored as 10000 (`100 * 100`) in database. And when the frontend receives the data, it changes it back to 100. 

However, you have to limit the decimal values you want to support. Example: If user wants to store `0.757684`

Since we are no longer dealing with precision values (`decimal values`), we donot care how our programming language handles the precision value. 