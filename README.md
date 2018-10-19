# Important JavaScript Question and Answers

### 1. How can I check an array contains objects

```
let array = [{a:20},{a:30},{a:40}];

function isArrayContainObject(array) {
   return array[0].constructor === Object ? true : false;
}

isArrayContainObject(array); //It will return true

isArrayContainObject([1,2,3,4,5]) //It will return false
```
