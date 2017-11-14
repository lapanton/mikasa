# mikasa
A simple framework for server side rendering react.

## Configuration

| Parameters    | Type               | Description  |
| ------------- |:------------------:| ----- |
| port          | Number             | The port that webserver will run on |
| routes        | Array              | An Array of Route Objects |
| static        | Object             | An configuration object |
| layout        | React Component    | The React Component that will be used as layout |
| store         | Object             | An Object containing the redux reducer and the initialState |
| promises       | Array             | An array of promises that need to be resolved before any render from server side |


## Routes
Routes are based on routes from react-router, they must be specified as an array of objects that must contain the following attributes.

| Parameters    | Type               | Cool  |
| ------------- |:------------------:| ----- |
| path          | String             | The route path, for example: /about |
| exact        | Boolean              | Exact parameter from react-router |
| component        | React Component             | The component that will be rendered for that route |
| loadData        | Function    | A function used for doing asynchronus actions before the render of the component. It must return a promise or an array of promises. The function takes three parameters: The context parameter from koa that contains the request, a shared object, and the redux store object for the dispatches before the render.  |

## Static
The static object must contain the following attributes.

| Parameters    | Type               | Cool  |
| ------------- |:------------------:| ----- |
| path          | String             | The path that will be used in browser, for exmaple: /public |
| local        | String              | The path to folder containing the static files. |
| options        | Object            | This object is used as options for koa-static. example: { gzip: true } |

## Store
The store object is used to create the redux storage on the backend. It must contain the following attributes:

| Parameters    | Type               | Cool  |
| ------------- |:------------------:| ----- |
| reducer          | Function             | It can be a simple reducer or a combined reducer. |
| initialState        | Object              | This will be used as initialState for the redux. |