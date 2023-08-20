
React, takes some data and render it to DOM. When the data changes, React will also re-render the elements in the DOM. This is great but has some downsides to it such as

- Search Engine Optimization is not great as web-scrappers will need to wait some time before react actually renders the component into the DOM. In traditional Multi Page application, server would send html directly. This meant that web crawlers didnot have to wait for any rendering to happen.

- React cannot render html in the server. There might be cases where rendering a certain component is better done in server instead of client. Since, react generates a static build, it doesnot run in the server.

- Since, React cannot generate html pre-front, you also cannot cache any pages in CDN.

- When we build the app, we might want to generate html for some component at the build time itself. This means it is just a static HTML file. React cannot do that.


NextJs is a full stack framework for react. It lets you write both frontend and backend for your application. Frontend will be written in React and backend will be written in plain Javascript. Since next has backend that communicates with database, it needs a server to run.  The creator of Next, Vercel provides the most easy way to deploy next application.

All the limitations of react above are solved by Nextjs. 


## Nextjs Directory Structure

When you create a next project via (create-next-app), you get to decide if you want to use tailwind, typescript etc. Depending upon the choice, you will endup with different config files. Apart from config files, there are 2 directories, public and src.The main codebase will be under the src directory. Anything that is present in public will be accessible directly as a static file. 

Nextjs uses Webpack as the module bundler. It will bundle everything inside the src directory in the single Javascript file.  Nextjs uses file based routing. This means, we donot have to use any routing library inside Nextjs. 

The /src directory should compulsorily have app directory. /src/app directory will serve as the routing point for any kind of routes in the application. If you want to render some component at /about, then you should create a about directory inside app directory. Next will map the directory structure with the routes in the url.

