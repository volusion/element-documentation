# How to Fetch Data Fast

In this how to, we will learn how to fetch data needed by blocks as fast as possible.

## 1. Find Serial Data Fetching

Assuming your `src/getDataProps.js` file looks like this, we have some room for optimizations.

```js
export const getDataProps = (utils, props) => {
    return utils.client.categories.get().then(categories => {
        return utils.client.menus.get().then(menus => {
            return {
                categories,
                menus
            }
        });
    });
}
```

As you can see, both calls are performed serially, but they do not depend the one on the other.

We can reduce request latency by making both request in parallel.

## 2. Fetch Independent Data Concurrently

We can make the data way faster by making the requests concurrently 

```js
export const getDataProps = (utils, props) => {
    const categoriesPromise = utils.client.categories.get();
    const menusPromise = utils.client.menus.get();

    return Promise.all([categoriesPromise, menusPromise]).then(([categories, menus]) => {
        return {
            categories,
            menus
        }
    });
}
```

With this simple change, our data will be fetch concurrently and the latency will be reduced.

## 3. Think About Data Dependencies

When fetching data, think what's the dependency between the information you are fetching. If no
dependency exists, fetch the data concurrently to reduce latency and exploit the fastest server side
rendering possible.
