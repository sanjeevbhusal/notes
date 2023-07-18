
React Query is all about fetching data from server. it doesnot deal with client side state management. So, you can use any other ways of managing client state such as context and other libraries.

React Query has 2 main components.

- QueryClient
- QueryClientProvider


### Query Client

Query Client manages the cache of each of the queries. It tracks the state of each query. 

### Query Client Provider

Query Client Provider is a react context provider that makes query client available across the entire application.


#### useQuery hook

This hooks is used to perform data fetching, caches the result and also provides the state of the query (pending, failed, completed)

It accepts 2 arguments. 

- query key
- query function

Query key is a array of keys (string, object etc). It is used to keep track of the query in the cache.  If any of the key change, a new request is sent to the server to fetch the data. Think of it like useEffect which runs anytime its dependencies change.

Example: Lets say one of the component takes a username as a prop and makes a api call to fetch the user. It doesnot make sense to make api call everytime the component gets re-run if the username has not changed. In such cases, you can use this usename as a key. Anytime the key changes, react query will make a new api call.

Query function is the actual function that has the logic of making a api call. In almost all cases, you will define the function elsewhere and only pass the reference of it. The function should return a promise.

useQuery hook returns a object that contains the actual api response, state of the request, error, a way to refetch the data again etc.

If you make a api call twice for the same url,  react query will not send the second call and will instead pick the value from the output of first call. This is called caching.

Example: If you let user pick between loading profile of 5 users (user1,...user5), you have to do a minimum of 5 api calls to load data for all 5 users. If the user loads data for user1, user2 and again user1, only 2 api calls will be dispatched.  React query will remember that it has already fetched the information of user1 before. Hence, in the third request, it will just pick the value from cache. 