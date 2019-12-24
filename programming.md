# Programming


## JavaScript

### API

**Combine multiple requests into one**


Using AxiosJS


```JavaScript
let promisesArr = []

for(let i = 0; i < 10; i++){
  promisesArr.push(axios.get("https://example.com/api?page=${i}"))
}

axios.all(promisesArr)
  .then(resp => {
    // Optionally, Do something with the response
    return resp
  })
  .catch(err => {
    // Optionally, Do something with the error
    return err
  })
```


In this example resp will be an array of responses from each request. 

This is possible using simply using Promise and any other data fetching method.



## Go

### WebAssembly

## Python

