# Data structure in JavaScript

## Array

- 0-indexed
  - for loop i starts from 0 to length - 1, first 0, last length - 1, current is array[i]
  - burn candle from both ends, array swap (i, length - 1 - i)
  - step \* 2 and step /2, heapify and binary search
- fixed size, length

- inline change / mutation

- for loop
  - predicate tests and yields true / false

Common array operations

- initialization
- swap values of two boxes
- find the index or value
  - find max
  - find min
  - find first
  - find last
  - find all
- reverse
  - candle, swap(i, length - 1 - i)
  - push and pop in JavaScript
- rotation
  - inline, three reverse
  - push and pop in JavaScript
- reshuffle
- dutch flag partition
  - kth largest
  - kth smallest
  - segregate even / old
- aggregation
  - average
  - sum
- add item
  - to the front, `unshift` in JavaScript
  - to the end, `push` in JavaScript
  - to the specific index, `splice(index, 0, item)` in JavaScript
- remove item <https://love2dev.com/blog/javascript-remove-from-array/>
  - to the front, `pop` in JavaScript
  - to the end, `shift` in JavaScript
  - to the specific index remove 1 item, `splice(index, 1)` in JavaScript
- copy an array
  - `slice()` in JavaScript
- create a new array instance

  - Array.from()
  - array.map()

- filter items

- test the items

## control flow

for loop

while loop

early return

foreach enumeration

## Two arrays

concat

array1.concat(array2)

## Resources

[array in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

[array on GeeksForGeeks](https://www.geeksforgeeks.org/array-data-structure/)
