# Important JavaScript Question and Answers

### 1. How can I check an array contains objects?

```
let array = [{a:20},{a:30},{a:40}];

function isArrayContainObject(array) {
   return array[0].constructor === Object ? true : false;
}

isArrayContainObject(array); //It will return true

isArrayContainObject([1,2,3,4,5]) //It will return false
```
### 2. How to deep clone an object?

Most concise and efficient way is 

```
const obj = {a:{a1: 100, a2: 200},b: {b1: 300}};

const cloneObj = JSON.parse(JSON.stringify(obj));
```
### 3. How to remove a property of an object?

By using ```delete``` we can remove propert from an object in JavaScript. See the following code:

```
const obj = {a: 20, b: 30, c: 40};

delete obj.a

//OR

delete obj['a']
```
Note: Don't use the following code for delete:
```obj.a = undefined```
```console.log(obj) will give you {a: undefined}```
Problem with this code is the key remains on its place in the hashmap, only the value is replaced with undefined. 
Understand, that for..in loop will still iterate over that key.
