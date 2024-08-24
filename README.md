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
```str.split('.').join('')```

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
### 8. Find longest sub-string from string with start index and length:
example: if str = "aabbbcd" then output will be {index: 2, length: 3, subString: "bbb", };
```
function getLongestSubString(str) {
  if(!str.trim()) {
    return "Plesae enter string";
  }
  const strArray = str.trim().split('');
  let count = 0, maxLength = 0, index;
  for(let i = 0; i<strArray.length; i++) {
    if(strArray[i] === strArray[i+1]) {
      count++;
    } else {
      if(count> maxLength) {
        maxLength = count;
        index=i;
      } 
      count=0;
    }
  }
  
  const subStrIndex = index - maxLength;
  const subString = str.slice(subStrIndex, subStrIndex + maxLength+1)
  
  if(subString) {
    return {index: subStrIndex, length: maxLength + 1, subString: subString };
  }
  
  return "No sub-string found";
}

const str = "aabbbcd";
console.log(largestSubString(str)) // {index: 2, length: 3, subString: "bbb", }

const str = "abbttrrrrer";
console.log(largestSubString(str)) // { index: 5, length: 4, subString: "rrrr" }


```

### 9. What is a first class function?
A programming language is said to have First-class functions when functions in that language are treated like any other variable. 

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable.

Checkout this:  https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function

### 10. What is a first order function?
First-order function is a function that doesn’t accept other function as an argument and doesn’t return a function as its return value.
```
function foo(a,b) {
   return a+b;
}
```

### 11. What is a higher order function?
Higher-order function is a function that accepts other function as an argument or returns a function as a return value.

```
// foo is the first order function
function foo(a,b) {
    return a+b;
}

// hof is the higher order function
function hof(fn) {
   return function(x,y,z) {
      return fn(x,y) + z;
   }
}

hof(foo)(5, 10, 15) // It will return 30

```
### 12. What is a pure function?
A Pure function is a function where the return value is only determined by its arguments without any side effects. 

If you call a function with the same arguments 'n' number of times and 'n' number of places in the application then it will always return the same value.

Example:

```
function pureFunction(a, b) {
   return a+b;
}
```
A pure function produces no side effects, which means that it can’t alter any external state.

JavaScript’s object arguments are references, which means that if a function were to mutate a property on an object or array parameter, that would mutate state that is accessible outside the function. Pure functions must not mutate external state.

### 13. Symmetrical difference between two arrays
```
if a = [1, 3, 5, 6, 7] and b = [1, 2, 4, 5, 7, 9] then symmetrical difference will be [2, 3, 4, 6, 9]
```
See the programs in JS
```
function symmetricalDiff(a, b) {
  var newAr = [];

 for(var i = 0; i < a.length || i < b.length; i++) {
  
  if(b.length > i  && !a.includes(b[i]))
    newAr.push(b[i]);
  
  if(a.length > i && !b.includes(a[i]))
    newAr.push(a[i]);
 }
  return newAr;
}

```

```
var a = [1, 3, 5, 6, 7 ], b = [1, 2, 4, 5, 7, 9];

console.log(symmetricalDiff(a, b)); ---->>> [2, 3, 4, 6, 9]
```

```
var a = [1, 3, 5, 6, 7, undefined ], b = [1, 2, 4, 5, 7, 9, 0, null];

console.log(symmetricalDiff(a, b))  ---->>>>  [2, 3, 4, 6, 9, undefined, 0, null]
```
### 14. How to randomize (shuffle) a JavaScript array?
```
var a = [1,2,3,4,5,6,7,8];

function shuffle(arr) {
  var ar = [...arr];
  var newAr = [];
  while(ar.length) {
    var rindex = Math.floor(Math.random()*ar.length);
    var item = ar.splice(rindex,1)[0];
    newAr.push(item)
  }
  return newAr;
}

console.log(shuffle(a))
```

### 15. decamelize the string

Examples: bodyShape -> body_Shape, counterValue -> counter_Value etc.
```
const convertKeyIntoString = (strKey, separator = '_') => {
    if(!strKey) {
        return;
    }
	return strKey
        .replace(/([a-z\d])([A-Z])/g, '$1' + separator + '$2')
        .replace(/([A-Z]+)([A-Z][a-z\d]+)/g, '$1' + separator + '$2');
};
```

### 16. Find most frequently occurring character
```
function findCharOccurance(str) {
  const occurances = new Map();
  for(const char of str) {
    /*
      if(occurances.get(char)) {
        occurances.set(char, occurances.get(char) + 1);
      } else {
        occurances.set(char, 1);
      }
    */
    occurances.set(char, (occurances.get(char) || 0) + 1);
  }
  
  const maxCount = Math.max(...occurances.values());
  
  const result = [];
  for(const [key, value] of occurances) {
    if(value === maxCount) {
      result.push(key);
    }
  }
  return result.length > 1 ? result : result[0];
}

console.log(findCharOccurance("abcacde")); // ['a', 'c'];

console.log(findCharOccurance("abca")); // a

```


