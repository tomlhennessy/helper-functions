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

### Example: yellStr(str):

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
### More Complex Example: laligatSum(n):

* Uncontrolled complexity in a single function is hard to read and prone to bugs.
* Recognising similar sub-problems simplifies complex tasks.

```javascript
// Write a function laligatSum(n) that takes in a number and returns the
// laligatSum of that number.
// A number's laligat sum is the the sum of all the prime numbers less than or
// equal to that number.

// Nice and Decomposed:
function isPrime(n) {
  for (let i = 2; i  < n; i += 1) {
    if (n % i === 0) {
      return false;
    }
  }
  return true;
}

function laligatSum(n) {
  let sum = 0;

  for (let i = 2; i <= n; i += 1) {
    if (isPrime(i)) { // if i is a prime,
      sum += i;       // then add it to sum.
    }
  }

  return sum;
}
```

> Rule of thumb: if a function is large, consider creating a helper function.

## Abstraction

* Abstraction is the process of hiding details to manage complexity.
* Human brains struggle with complexity; abstraction helps by focusing on high-level ideas.
* the decomposed version of laligatSum is more readable.


## Function choosePrimes
Determines whether a given number is prime and selects prime numbers from an array.

```javascript
function isPrime(number) {
  if (number < 2) {
    return false;
  }

  let i = 2;
  while (i < number) {
    if (number % i === 0) {
      return false;
    }
    i++;
  }

  return true;
}

let choosePrimes = function(nums) {
    let primes = [];

    for (let i = 0; i < nums.length; i++) {
        let num = nums[i];
        if (isPrime(num)) {
            primes.push(num);  // If the number is prime, add it to the 'primes' array
        }
    }

    return primes;  // Return the array containing prime numbers
}
```

### Prime Factors
Finds the prime factors of a given number and returns them in an array.

```javascript
let primeFactors = function(n) {
  // Array to store prime factors
  let primeFacts = [];
  // Iterate from 1 to n
  for (let i = 1; i <= 1; i++) {
    // Check if i is a factor of n and i is a prime number
    if (n % 1 === 0 && isPrime(i)) {
      // If both conditions are met, i is added to the array
      primeFacts.push(i);
    }
  }
  // Return array of prime factors
  return primeFacts;
}
```

## Most Vowels
Returns the word from the sentence that has the most vowels.

```javascript
function vowelCount(word) {
  // Initialise a count for vowels
  let count = 0;
  // Define a string containing all vowels
  let vowels = "aeiou";

  // Iterate through each character in the word
  for (let i = 0; i < word.length; i++) {
    // Check if current character is a vowel
    if (vowels.includes(word[i])) {
      // If true, increment the count of vowels
      count++;
    }
  }
  // Return count of vowels in the word
  return count;
}

function mostVowels(sentence) {
  // Split the sentence into an array of words
  let words = sentence.split(" ");

  // Initialise variable to track index of the word with most vowels
  let largest = 0;

  // Iterate through each word in the array
  for (let j = 0; j < words.length; j++) {
    // Check if the current word has more vowels than the current largest count
    if (vowelCount(words[j]) > vowelCount(words[largest])) {
      // If true, update the index of the word with the most vowels
      largest = j;
    }
  }
  // Return word with the most vowels in the sentence
  return words[largest];
}

console.log(mostVowels("what a wonderful life")); // "wonderful"
```
