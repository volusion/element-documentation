# How to Fetch Data from Third Party Services

Sometimes we need our blocks to consume third party data. For example, a blog API. In this how-to, we will see
how to achieve just that.

We will be consuming data from `https://jsonplaceholder.typicode.com/posts`

## 1. Locate Your Get Data File 

Open up your block's code and find /src/getDataProps.js. It should look like this:

```js
export const getDataProps = (utils, props) => Promise.resolve();
```

## 2. Make the Request Call You Need

```js
export const getDataProps = (utils, props) => {
      return utils.client.request("https://jsonplaceholder.typicode.com/posts")
          .then(res => res.json())
          .catch(e => []);
}
```

The `request` function is exactly the [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) function that works both in the server and in the client.
You don't have to care about importing the right version of the function depending on which environment you are in.

## 3. Use the Data from Your Block

From your render function located in src/Block.js, you will have the data available:

```js
function StarterBlock(props) {
     const posts = props.data;
     ...
}
```
