# Task 4

For the following functions:
1) Create control flow graph of function
2) Define equavalence classes of input data
3) Create test-cases (inputs and expected outputs)

--------------------

1) [Fibonacci Number](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/math/fibonacci/README.md)

```
function fibonacci(n) {
  const fibSequence = [1];

  let currentValue = 1;
  let previousValue = 0;

  if (n === 1) {
    return fibSequence;
  }

  let iterationsCounter = n - 1;

  while (iterationsCounter) {
    currentValue += previousValue;
    previousValue = currentValue - previousValue;

    fibSequence.push(currentValue);

    iterationsCounter -= 1;
  }

  return fibSequence;
}
```

--------------------

2) [Hamming Distance](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/string/hamming-distance/README.md)


```
function hammingDistance(a, b) {
  if (a.length !== b.length) {
    throw new Error('Strings must be of the same length');
  }

  let distance = 0;

  for (let i = 0; i < a.length; i += 1) {
    if (a[i] !== b[i]) {
      distance += 1;
    }
  }

  return distance;
}
```
  
--------------------

3) [Binary Search](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/search/binary-search/README.md)

```
function binarySearch(sortedArray, seekElement) {

  // These two indices will contain current array (sub-array) boundaries.
  let startIndex = 0;
  let endIndex = sortedArray.length - 1;

  // Let's continue to split array until boundaries are collapsed
  // and there is nothing to split anymore.
  while (startIndex <= endIndex) {
    // Let's calculate the index of the middle element.
    const middleIndex = startIndex + Math.floor((endIndex - startIndex) / 2);

    // If we've found the element just return its position.
    if (sortedArray[middleIndex] == seekElement) {
      return middleIndex;
    }

    // Decide which half to choose for seeking next: left or right one.
    if (sortedArray[middleIndex] < seekElement) {
      // Go to the right half of the array.
      startIndex = middleIndex + 1;
    } else {
      // Go to the left half of the array.
      endIndex = middleIndex - 1;
    }
  }

  // Return -1 if we have not found anything.
  return -1;
}
``` 
 
 
