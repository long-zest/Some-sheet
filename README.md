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
```

// Desc

```javascript
var numArray = [104, 140000, 99];
numArray.sort(function(a, b) {
  return b - a;
});

console.log(numArray);
//result will be [140000, 104, 99]
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

</details>


