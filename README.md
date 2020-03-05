# Important JavaScript Questions and Answers

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

By using ```delete``` we can remove property from an object in JavaScript. See the following code:

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

### 4. How to remove a specific element from an array in javascript?
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
       }
   }
}

console.log(arrayObj)  //It will give you: [1,2,3,4,6,7]
```
C) By using filter
```
arrayObj = arrayObj.filter( item => item !== deleteElement);
```
Note: Don't use  ```delete arrayObj[index]```. Keep in mind that when you use delete for an array you could get wrong results for anArray.length. In other words, delete would remove the element but wouldn't update the value of length property. The ```delete``` is good for deleting attributes of objects but not so good for arrays. It is better to use splice for arrays.

### 5. Remove all dot from the string ```const str = "a.b.c.d.e.f.g.h"```
Solution 1:
```str.replace(/\./g,'')```

Solution 2:
```str.split('.').join()```

### 6. What is event delegation in JS?

Answer:
1. Capturing and bubbling allow us to implement one of most powerful event handling patterns called event delegation.
2. The idea is that if we have a lot of elements handled in a similar way, then instead of assigning a handler to each of them – we put a single handler on their common ancestor.
3. In the handler we get event.target, see where the event actually happened and handle it.

### 7. How to convert string to title case in javascript?
for instance: if title = "good morning john" then the out "Good Morning John".

```
const str = "good morning john";

const titleCaseString = str.split(' ').map(w => w[0].toUpperCase() + w.slice(1)).join(' ');

or

const titleCaseString = str.split(' ').map(w => w.charAt(0).toUpperCase() + w.slice(1)).join(' ');

console.log(titleCaseString); // Good Morning John

```
