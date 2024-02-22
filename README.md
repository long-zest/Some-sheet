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


</details>


