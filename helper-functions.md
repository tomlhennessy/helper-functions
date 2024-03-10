# Helper Functions
Helper functions are essential for controlling the complexity of programs. Uncontrolled complexity leads to bugs and understanding issues.

## Decomposition
* Decomposition breaks down a large problem into smaller, more manageable sub-problems.
* Decomposition is about recognising sub-problems and solving them with helper functions.

Example: yellStrings(strings):

```javascript
// yellStrings(strings)
// Write a function that takes in an array of strings as an argument.
// It should return array where every string is "yelled", see the example below:

let yelled = yellStrings(['hello', 'how', 'are', 'you?']);
yelled; //=> ['HELLO!', 'HOW!', 'ARE!', 'YOU?!'];
```
Managing to change all the strings in the array is complex. Here is a problem that is more manageable to solve:

Example: yellStr(str):

```javascript
// yellStr(str)
// Write a function that takes in a string as an argument. The function
// should return the string but "yelled", see the example below:

let yelled = yellStr('bootcamp');
yelled; //=> 'BOOTCAMP!'
```

yellStr is a sub-problem of the yellStrings. Here is how to solve yellStrings (using yellStr as a helper function):

```javascript
function yellStr(str) {
  let upperString = str.toUpperCase();
  return upperString + '!';
}

function yelledStrings(strings) {
  let yelled = [];

  for (let i = 0; i < strings.length; i++) {
    let string = strings[i];
    let newString = yellStr(string);
    yelled.push(newString);
  }

  return yelled;
}
```
