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

### 4. How to remove a specific element fron an array in javascript?
A) By using ```indexOf()``` and ```splice()``` method
```
const arrayObj = [1,2,3,4,5,6,7];
const deleteElement = 5;
const index = arrayObj.indexOf(deleteElement);  // It will give you 4
if(index > -1) {
   arrayObj.splice(index, 1);  
}
console.log(arrayObj)  //It will give you: [1,2,3,4,6,7]
```
B) By using ```for()``` loop
```
const arrayObj = [1,2,3,4,5,6,7];
const deleteElement = 5;

removeElement(arrayObj, deleteElement);

function removeElement(arrayObj, deleteElement) {
   for(let i = 0; i <= arrayObj.length - 1; i++) {
       if(arrayObj[i] === deleteElement) {
          arrayObj.splice(i, 1);
          break; // Note: if you want to remove all elements that value is 5 then remove break statement from here 
       }
   }
}

console.log(arrayObj)  //It will give you: [1,2,3,4,6,7]
```
C) By using filter
```
arrayObj = arrayObj.filter( item => item !== deleteElement);
```
Note: Don't use  ```delete arrayObj[index]```


