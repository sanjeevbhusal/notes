
So any CPU intensive task (not I/O) would be preferred for parallelism. Think about calculating the factorial vs taking input for the factorial.
The input can come at any time from different sources and you will typically have to wait for a user to send that input. A great case for concurrency.
But once a user input is received it will actually start calculating which will be CPU intensive.
Assume 2 users, and a case where your factorial calculation takes 1-min. You have 8 CPU cores.
On 1 core, you run your fastAPI server, that receives an input from the user anytime a user sends one. 2 could also sent simultaneously.

**Case 1:**
User 1 : Sends input at 07:00:00, which is received by the server on Core 1. The core 1 starts another Python interpreter where the calculation starts at 07:00:01
User 2:  Sends input at 07:00:01, which is received by the server on Core 1. The core 1 starts another Python interpreter where the calculation starts at 07:00:02

**Case 2:**
User 1 : Sends input at 07:00:00, which is received by the server on Core 1. The core 1 starts the calculation at 07:00:01 but on the same Core 1.
User 2:  Sends input at 07:00:01, which should have been received by the server on Core 1. But the second user faces a delay of atleast 1 minute till the core gets free from the calculation.

In case 1, where the server was doing a similar task that involved waiting, i.e., receiving inputs from the user will benefit from async code because the async code. 
In case 2, if you don't add multiprocessing for a CPU intensive task, User 2 has to wait till all computations just before user 2 are over. Case 2 would benefit from multiprocessing.



sushila.bhusal@gmail.com
9851144703