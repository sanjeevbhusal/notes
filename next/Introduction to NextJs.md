
React, takes some data and render it to DOM. When the data changes, React will also re-render the elements in the DOM. This is great but has some downsides to it such as

- Search Engine Optimization is not great as web-scrappers will need to wait some time before react actually renders the component into the DOM. In traditional Multi Page application, server would send html directly. This meant that web crawlers didnot have to wait for any rendering to happen.

- React cannot render html in the server. There might be cases where rendering a certain component is better done in server instead of client. Since, react generates a static build, it doesnot run in the server.

- Since, React cannot generate html pre-front, you also cannot cache any pages in CDN.

- When we build the app, we might want to generate html for some component at the build time itself. This means it is just a static HTML file. React cannot do that.


NextJs is a full stack framework for react. It lets you write both frontend and backend for your application. Frontend will be written in React and backend will be written in plain Javascript. Since next has backend that communicates with database, it needs a server to run.  The creator of Next, Vercel provides the most easy way to deploy next application.

All the limitations of react above are solved by Nextjs. 


## Nextjs Directory Structure

When you create a next project via (create-next-app), you get to decide if you want to use tailwind, typescript etc. Depending upon the choice, you will endup with different config files. Apart from config files, there are 2 directories, public and src.The main codebase will be under the src directory. Anything that is present in public will be accessible directly as a static file. 

Nextjs uses Webpack as the module bundler. It will bundle everything inside the src directory in the single Javascript file.  


### Src Directory Structure / Routing in Nextjs

Nextjs uses file based routing. This means, we don't have to use any routing library inside Nextjs.  Inside the src directory we can have different files such as eslint files, gitignore etc. However, we must have a directory called app.

/src/app directory will serve as the routing point for any kind of routes in the application. To render a certain component inside the root url (localhost:3000/), we must have at-least 2 files, layout.tsx and page.tsx.

page.tsx should contain the actual component that should be rendered at the root url. 
In page.tsx, you will not have the entire html structure such as, html, head, body element etc. You will just have the actual html element that user can see such as h1, p, etc. This means page.tsx doesnot contain the entire markup that should be rendered in the DOM.

This is where layout.tsx comes in. Next will pass the component from page.tsx as a children to component in layout.tsx. Layout component is a higher order component. It takes a component as an argument and returns a new component. The new component will wrap the component passed in as an argument in some markup and return the complete markup.

Generally, Layout.tsx will not contain metadata about the page itself. Metadata of the page is present in the head tag of the html document. Next will automatically generate the contents in the head tag.  We can also override this behavior.

Both page.tsx and layout.tsx can have multiple components inside it. The component that should be served as the layout and page should be exported as default from the files. 

If you want to render a page in /about url, then you should create a about directory inside app directory. This folder should also have a file called page.tsx. When you visit /about, next will take the default exported component inside /app/about/page.tsx and pass it as a prop to default exported component in /app/layout.tsx. There might be cases where you might have nested routes inside /about routes such as /about/company, /about/careers etc. In such scenarios, you have to create nested folders such as /app/about/company, /app/about/careers and have a page.tsx file in both the folders. If both page.tsx needs to share some code, you can create a layout.tsx in /app/about directory.  This way, to render the contents for a single url, single/multiple layout components and a single page component is needed.


### Server side vs Client side Rendering

In Server side rendering, the next server will generate html in the server and send it to the browser. User makes a request to a endpoint, nextjs server will map the url with the page and layouts, execute the component, generate html and send it to the browser.

In Client side rendering, the next server, will send javascript(react+next) to the browser, browser executes the javascript, nextjs server will map the url with the page and layouts, execute the component, generate html and render it to DOM. 

### Data Fetching in Client Side / Server Side

You can mark a component as being async if it is to rendered in the server. If the component is rendered client side, it cannot be marked as client. This is because react needs the return value of the component to render to DOM as soon as possible. 

If you need to do any kind of data fetching in client side component, you usually do it in useEffect. For data fetching in server side component, you can mark the component as async and make a api call directly in the component and await it. Once the await is over, you can take the data and return html.

This also has some of the downsides if you donot use it properly. Hence, It is important to know where do you want the data to be fetched, client side or server side. This will decide if the data fetched will be dynamic or static. 

### Different Rendering Methods in Nextjs

There are 3 different rendering methods in Nextjs, Static Generation, Incremental Static Generation and Dynamic Rendering.

Static Generation means running the component once, creating the final html document and then storing it in the cache for every subsequent request. This means the server will only run the component once and reuse the generated html for every request. This means if the component does some kind of api call, the api call will only be done once when the component is first rendered. This is only suitable for pages that have static content and will never change dynamically(Eg: About page of the company).

Incremental Static Generation is used when you the component needs dynamic data but the data doesnot change frequently. Just like Static Generation, you will run you component once, generate html and serve it in every request. But as your component relies on dynamic data, you might have to refetch the data and re-generate html document once the data is changed. So, you tell nextjs to regenerate the html document after certain intervals of time such as 5 seconds, 1 hour etc. This technique is useful only if you know you donot need to make a api call to get latest data on every network request because your data doesnot change much. If the data changes very frequently, then it is just better to do a dynamic rendering.

Dynamic Rendering means running the entire component again for each request. 

Incremental Static Generation is used when you have pages which have combination of both static and dynamic data. Since, the component uses dynamic data, you cannot perform Static Generation. It also doesnot mean, you need to always run the component for every request. In a component, you can extract all the static content and create a html document out of it. Then, for the dynamic part, you can ship the javascript with that html document itself. This way, when the client gets the html, it shows the static content first, then executes the javascript which renders dynamic content. This process is also called hydration.  



