# Some-sheet

<details>
<summary>

  ### Merge array without dub

</summary><br/>

// Not object array
```javascript
var a = [1, 2, 3], b = [101, 2, 1, 10] 
var c = a.concat(b.filter((item) => a.indexOf(item) < 0))

console.log(c) // c is [1, 2, 3, 101, 10] 
```
// With object array 
```javascript
const something = [{id: 1, "name": "somehting"}, {id: 2, "name": "gido"}]
const something2 = [{id: 3, "name": "somehting"}, {id: 4, "name": "gido"}, {id: 2, "name": "gido"}, , {id: 1, "name": "gido"}]

const something3= something.concat(something2.filter(item => !something.some(element => element.id === item.id)))

console.log(something3)
```
</details>

<details>
<summary>

  ### Sort array thingy

</summary>
// Asc

```javascript
var numArray = [140000, 104, 99];
numArray.sort(function(a, b) {
  return a - b;
});

console.log(numArray);
//result will be [99, 104, 140000]

//with object this is string btw...
arr.sort((a, b) => a.name.localeCompare(b.vid))
```

// Desc

```javascript
var numArray = [104, 140000, 99];
numArray.sort(function(a, b) {
  return b - a;
});

console.log(numArray);
//result will be [140000, 104, 99]

//with object this is string btw...
arr.sort((a, b) => b.name.localeCompare(a.vid))
```

</details>

<details>
<summary>
 
  ### Leetcode problem
  
</summary>

<details>
<summary>

  #### 1. Two sum leet code

</summary>
  
```
Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  let map = new Map()
  for(let i=0;i<nums.length;i++){
      let complement = target - nums[i];
      if(map.has(complement))
        return [map.get(complement),i]
    map.set(nums[i],i)
  } 
  
};
```
</details>

<details>
<summary>

  #### 21. Merge Two Sorted Lists

</summary>

```
Example 1:
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

Example 2:
Input: list1 = [], list2 = []
Output: []

Example 3:
Input: list1 = [], list2 = [0]
Output: [0]
```

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    if (!list1) return list2;
    if (!list2) return list1;
    if (list1.val < list2.val) {
        list1.next = mergeTwoLists(list1.next, list2);
        return list1;
    } else {
        list2.next = mergeTwoLists(list1, list2.next);
        return list2;
    }
};
```
</details>

<details>
<summary>

  #### 83. Remove Duplicates from Sorted List

</summary>

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var deleteDuplicates = function (head) {
    // Special case...
    if (head == null || head.next == null)
        return head;
    // Initialize a pointer curr with the address of head node...
    let curr = head;
    // Traverse all element through a while loop if curr node and the next node of curr node are present...
    while (curr != null && curr.next != null) {
        // If the value of curr is equal to the value of prev...
        // It means the value is present in the linked list...
        if (curr.val == curr.next.val) {
            // Hence we do not need to include curr again in the linked list...
            // So we increment the value of curr...
            curr.next = curr.next.next;
        }
        // Otherwise, we increment the curr pointer...
        else {
            curr = curr.next;
        }
    }
    return head;        // Return the sorted linked list without any duplicate element...
};
```
</details>

<details>
<summary>

  #### 2618. Check if Object Instance of Class

</summary>

```
Example 1:

Input: func = () => checkIfInstanceOf(new Date(), Date)
Output: true
Explanation: The object returned by the Date constructor is, by definition, an instance of Date.

Example 2:

Input: func = () => { class Animal {}; class Dog extends Animal {}; return checkIfInstanceOf(new Dog(), Animal); }
Output: true
Explanation:
class Animal {};
class Dog extends Animal {};
checkIfInstanceOf(new Dog(), Animal); // true

Dog is a subclass of Animal. Therefore, a Dog object is an instance of both Dog and Animal.

Example 3:

Input: func = () => checkIfInstanceOf(Date, Date)
Output: false
Explanation: A date constructor cannot logically be an instance of itself.

Example 4:

Input: func = () => checkIfInstanceOf(5, Number)
Output: true
Explanation: 5 is a Number. Note that the "instanceof" keyword would return false. However, it is still considered an instance of Number because it accesses the Number methods. For example "toFixed()".
```

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var deleteDuplicates = function (head) {
    // Special case...
    if (head == null || head.next == null)
        return head;
    // Initialize a pointer curr with the address of head node...
    let curr = head;
    // Traverse all element through a while loop if curr node and the next node of curr node are present...
    while (curr != null && curr.next != null) {
        // If the value of curr is equal to the value of prev...
        // It means the value is present in the linked list...
        if (curr.val == curr.next.val) {
            // Hence we do not need to include curr again in the linked list...
            // So we increment the value of curr...
            curr.next = curr.next.next;
        }
        // Otherwise, we increment the curr pointer...
        else {
            curr = curr.next;
        }
    }
    return head;        // Return the sorted linked list without any duplicate element...
};
```
</details>

<details>
<summary>

#### 2620. Counter
  
</summary>

```javascript
/**
 * @param {number} n
 * @return {Function} counter
 */
var createCounter = function(n) {
    
    return function() {
        return n++;
    };
};

/** 
 * const counter = createCounter(10)
 * counter() // 10
 * counter() // 11
 * counter() // 12
 */
```

  
</details>

<details>
<summary>

#### 2621. Sleep
  
</summary>

```
// Example 1:

Input: millis = 100
Output: 100
Explanation: It should return a promise that resolves after 100ms.
let t = Date.now();
sleep(100).then(() => {
  console.log(Date.now() - t); // 100
});

// Example 2:

Input: millis = 200
Output: 200
Explanation: It should return a promise that resolves after 200ms.
```

```javascript
/**
 * @param {number} millis
 * @return {Promise}
 */
async function sleep(millis) {
    await new Promise(resolve => setTimeout(resolve, millis));
}

/** 
 * let t = Date.now()
 * sleep(100).then(() => console.log(Date.now() - t)) // 100
*/
```

  
</details>

<details>
<summary>

#### 2624. Snail Traversal
  
</summary>

```
Example 1:

Input: 
nums = [19, 10, 3, 7, 9, 8, 5, 2, 1, 17, 16, 14, 12, 18, 6, 13, 11, 20, 4, 15]
rowsCount = 5
colsCount = 4
Output: 
[
 [19,17,16,15],
 [10,1,14,4],
 [3,2,12,20],
 [7,5,18,11],
 [9,8,6,13]
]

Example 2:

Input: 
nums = [1,2,3,4]
rowsCount = 1
colsCount = 4
Output: [[1, 2, 3, 4]]

Example 3:

Input: 
nums = [1,3]
rowsCount = 2
colsCount = 2
Output: []
Explanation: 2 multiplied by 2 is 4, and the original array [1,3] has a length of 2; therefore, the input is invalid.
```

```javascript
/**
 * @param {number} rowsCount
 * @param {number} colsCount
 * @return {Array<Array<number>>}
 */
Array.prototype.snail = function(numRows, numCols) {
  if (numRows * numCols !== this.length) return [];
  let result = Array(numRows).fill().map(() => []);
  for (let row = 0; row < numCols; row++) {
    for (let col = 0; col < numRows; col++) {
      result[(row & 1) ? numRows - col - 1 : col].push(this[row * numRows + col]);
    }
  }
  return result;
}

/**
 * const arr = [1,2,3,4];
 * arr.snail(1,4); // [[1,2,3,4]]
 */
```

  
</details>

<details>
<summary>

#### 2631. Group By
  
</summary>

Example 1:

```
Input: 
array = [
  {"id":"1"},
  {"id":"1"},
  {"id":"2"}
], 
fn = function (item) { 
  return item.id; 
}

Output: 
{ 
  "1": [{"id": "1"}, {"id": "1"}],   
  "2": [{"id": "2"}] 
}

Explanation:
Output is from array.groupBy(fn).
The selector function gets the "id" out of each item in the array.
There are two objects with an "id" of 1. Both of those objects are put in the first array.
There is one object with an "id" of 2. That object is put in the second array.
```
Example 2:
```
Input: 
array = [
  [1, 2, 3],
  [1, 3, 5],
  [1, 5, 9]
]
fn = function (list) { 
  return String(list[0]); 
}

Output: 
{ 
  "1": [[1, 2, 3], [1, 3, 5], [1, 5, 9]] 
}

Explanation:
The array can be of any type. In this case, the selector function defines the key as being the first element in the array. 
All the arrays have 1 as their first element so they are grouped together.
{
  "1": [[1, 2, 3], [1, 3, 5], [1, 5, 9]]
}
```
Example 3:
```
Input: 
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
fn = function (n) { 
  return String(n > 5);
}

Output:
{
  "true": [6, 7, 8, 9, 10],
  "false": [1, 2, 3, 4, 5]
}

Explanation:
The selector function splits the array by whether each number is greater than 5.
```

```javascript
/**
 * @param {Function} fn
 * @return {Array}
*/
Array.prototype.groupBy = function(fn) {
  // Reduce the array into a single object
  return this.reduce((grouped, item) => {
    // Apply the provided callback function to get the key
    const key = fn(item);
    
    // If the key doesn't exist in the grouped object, create a new array for it
    if (!grouped[key]) {
      grouped[key] = [];
    }
    
    // Push the current item to the array associated with the key
    grouped[key].push(item);
    
    // Return the updated grouped object for the next iteration
    return grouped;
  }, {});
};


/**
 * [1,2,3].groupBy(String) // {"1":[1],"2":[2],"3":[3]}
*/
```

  
</details>

<details>
<summary>

#### 2634. Filter Elements from Array
  
</summary>

```javascript
/**
 * @param {number[]} arr
 * @param {Function} fn
 * @return {number[]}
 */
var filter = function(arr, fn) {
    var filteredArr = [];
    for (var i = 0; i < arr.length; i++) {
        if (fn(arr[i], i)) {
            filteredArr.push(arr[i]);
        }
    }
    return filteredArr;
};
```

  
</details>

<details>
<summary>

#### 2637. Promise Time Limit
  
</summary>

```javascript
/**
 * @param {Function} fn
 * @param {number} t
 * @return {Function}
 */
var timeLimit = function(fn, t) {
    return async function(...args) {
        const originalFnPromise = fn(...args);

        const timeoutPromise = new Promise((_, reject) => {
            setTimeout(() => {
                reject('Time Limit Exceeded')
            }, t);
        })

        return Promise.race([originalFnPromise, timeoutPromise]);
    }
};

/**
 * const limited = timeLimit((t) => new Promise(res => setTimeout(res, t)), 100);
 * limited(150).catch(console.log) // "Time Limit Exceeded" at t=100ms
 */
```
  
</details>

<details>
<summary>

#### 2665. Counter II
  
</summary>

```javascript
/**
 * @param {integer} init
 * @return { increment: Function, decrement: Function, reset: Function }
 */
var createCounter = function (init) {
    let presentCount = init;

    function increment() {
        return ++presentCount;
    }

    function decrement() {
        return --presentCount;
    }

    function reset() {
        return (presentCount = init);
    }

    return { increment, decrement, reset };
};

/**
 * const counter = createCounter(5)
 * counter.increment(); // 6
 * counter.reset(); // 5
 * counter.decrement(); // 4
*/
```
</details>

<details>
<summary>

#### 2722. Join Two Arrays by ID
  
</summary>

```
Example 1:

Input: 
arr1 = [
    {"id": 1, "x": 1},
    {"id": 2, "x": 9}
], 
arr2 = [
    {"id": 3, "x": 5}
]
Output: 
[
    {"id": 1, "x": 1},
    {"id": 2, "x": 9},
    {"id": 3, "x": 5}
]
Explanation: There are no duplicate ids so arr1 is simply concatenated with arr2.

Example 2:

Input: 
arr1 = [
    {"id": 1, "x": 2, "y": 3},
    {"id": 2, "x": 3, "y": 6}
], 
arr2 = [
    {"id": 2, "x": 10, "y": 20},
    {"id": 3, "x": 0, "y": 0}
]
Output: 
[
    {"id": 1, "x": 2, "y": 3},
    {"id": 2, "x": 10, "y": 20},
    {"id": 3, "x": 0, "y": 0}
]
Explanation: The two objects with id=1 and id=3 are included in the result array without modifiction. The two objects with id=2 are merged together. The keys from arr2 override the values in arr1.

Example 3:

Input: 
arr1 = [
    {"id": 1, "b": {"b": 94},"v": [4, 3], "y": 48}
]
arr2 = [
    {"id": 1, "b": {"c": 84}, "v": [1, 3]}
]
Output: [
    {"id": 1, "b": {"c": 84}, "v": [1, 3], "y": 48}
]
Explanation: The two objects with id=1 are merged together. For the keys "b" and "v" the values from arr2 are used. Since the key "y" only exists in arr1, that value is taken form arr1.
 
```

```javascript
/**
 * @param {Array} arr1
 * @param {Array} arr2
 * @return {Array}
 */
var join = function(arr1, arr2) {
    const result = {};

    // 1. initialization
    arr1.forEach(item => {
        result[item.id] = item;
    });
    // 2. joining
    arr2.forEach(item => {
        if (result[item.id]) {
            Object.keys(item).forEach(key => {
                result[item.id][key] = item[key];    
            });
        } else {
            result[item.id] = item;
        }
    });
    console.log(result)
    return Object.values(result);
};
```
</details>

<details>
<summary>

#### 2724. Sort By
  
</summary>

```
Example 1:

Input: arr = [5, 4, 1, 2, 3], fn = (x) => x
Output: [1, 2, 3, 4, 5]
Explanation: fn simply returns the number passed to it so the array is sorted in ascending order.

Example 2:

Input: arr = [{"x": 1}, {"x": 0}, {"x": -1}], fn = (d) => d.x
Output: [{"x": -1}, {"x": 0}, {"x": 1}]
Explanation: fn returns the value for the "x" key. So the array is sorted based on that value.

Example 3:

Input: arr = [[3, 4], [5, 2], [10, 1]], fn = (x) => x[1]
Output: [[10, 1], [5, 2], [3, 4]]
Explanation: arr is sorted in ascending order by number at index=1. 
```

```javascript
/**
 * @param {Array} arr
 * @param {Function} fn
 * @return {Array}
 */
var sortBy = function(arr, fn) {
    return arr.sort((a, b) => fn(a) - fn(b));
};
```
</details>

<details>
<summary>

#### 2727. Is Object Empty
  
</summary>

```javascript
/**
 * @param {Object|Array} obj
 * @return {boolean}
 */
var isEmpty = function(obj) {
    return Object.keys(obj).length === 0
};
```
</details>

<details>
<summary>

#### Spotify coding interview - power of 4
  
</summary>

```javascript
/**
 * @param {number} n
 * @return boolean
 */

const isPowerOfFour = function(n) {
  if(n === 1) return true;
  if(n <= 0) return false;
  if(n % 4 !== 0) return false;

  return isPowerOfFour(n/4);
}

const n1 = 16
console.log(isPowerOfFour(n1)) //true (16 = 2^4)
```
</details>

</details>

<details>
<summary>

### Dub thingy
  
</summary>

```javascript
const eliminateDuplicates = (arr) => {
        var i,
            len = arr.length,
            out = [],
            obj = {};
      
        for (i = 0; i < len; i++) {
          obj[arr[i]] = 0;
        }
        for (i in obj) {
            out.push(i);
        }
        console.log(out)
    }

===================================THIS IS FOR OBJECT

eliminateDuplicatesObject 
        
const uniqueObjects = [...new Map(arr.map(item => [item.vid, item])).values()] //it will leave the lasted dub and remove previous one in the array

console.log(uniqueObjects)
  
```
</details>

<details>
<summary>

### Unique Array
  
</summary>

```javascript

function onlyUnique(value, index, array) {
  return array.indexOf(value) === index;
}

// usage example:
var a = ['a', 1, 'a', 2, '1'];
var unique = a.every(onlyUnique);

console.log(unique); // false

// get all unique values in arr

function onlyUnique(value, index, array) {
  return array.indexOf(value) === index;
}

// usage example:
var a = ['a', 1, 'a', 2, '1'];
var unique = a.filter(onlyUnique);

console.log(unique); // ['a', 1, 2, '1']
  
```
</details>




