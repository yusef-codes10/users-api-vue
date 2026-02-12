# Vue Concepts & Practice

## Overview

This is where I practice new and ambigeous vue concepts such as fetching data from an API, promises and Computed props.

## Concpets practiced in this repo

1. API Fetching
2. Filtering with computed props
3. live search with computed props

### 1. API Fetching

First of all, the lifecycle methods in Vue are most critical concepts to consider when building reactive websites.<br>
In this case we need the **onMounted()** lifecycle method, which gets invoked when the DOM content loads to the page.<br>
inside that method we fetch and await for the promise.

And here are the steps to do that:

#### 1. define the **onMounted()**

```vue
onMounted( async () => { })
```
