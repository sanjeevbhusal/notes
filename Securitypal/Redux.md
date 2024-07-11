

**Redux**
Redux is used to store values globally and read/write them from various parts of our application. 

**React-Redux**
React-Redux is another package that is used to bind react with redux. You can think of this like react context. We wrap our entire app with a Provider component from react-redux. This Provider Component has access to redux store. 

react-redux also supplies a hook called useAppSelector. All our components that use this hook directly or indirectly re-render anytime redux store changes.

<img width="603" alt="image" src="https://github.com/SecurityPal/security-pal/assets/79491041/a2793f7c-fd0f-4463-b19a-7530a0369341">

<img width="805" alt="image" src="https://github.com/SecurityPal/security-pal/assets/79491041/ceaf1660-d7fc-4684-9d9d-3d97a5153a51">


and can use a hook to access values of this component.

Redux Toolkit (RTK) is built on top of react. Redux Toolkit Query is a part of RTK.


The issue arises when we pass date object in the params since date objects are not serializable i.e. you cannot serialize a date object into string and parse it back into a date object without data loss. The goal here will be to convert the date object into iso string so that they can be serialized.

