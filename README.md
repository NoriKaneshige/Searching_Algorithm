# Searching_Algorithm

![Searching](https://github.com/NoriKaneshige/Searching_Algorithm/blob/master/Searching.png)
> ## 1) Linear Search Exercise: :cry: 
> Write a function called linearSearch which accepts an array and a value, 
> and returns the index at which the value exists. If the value does not exist in the array, return -1.

> Don't use indexOf to implement this function!

``` js
function linearSearch(arr, val){
    for(var i = 0; i < arr.length; i++){
        if(arr[i] === val) return i;
    }
    return -1;
}

console.log(linearSearch([34,51,1,2,3,45,56,687], 100)) // -1
console.log(linearSearch([10, 15, 20, 25, 30], 15)) // 1
console.log(linearSearch([9, 8, 7, 6, 5, 4, 3, 2, 1, 0], 4)) // 5
console.log(linearSearch([100], 100)) // 0
console.log(linearSearch([1,2,3,4,5], 6)) // -1
console.log(linearSearch([9, 8, 7, 6, 5, 4, 3, 2, 1, 0], 10)) // -1
console.log(linearSearch([100], 200)) // -1
```


> ## 2) Binary Search Exercise: :wink: 
> Write a function called binarySearch which accepts a sorted array and a value and returns the index at which the value exists. Otherwise, return -1.
> This algorithm should be more efficient than linearSearch - you can read how to implement it here 
> - https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search and here 
> - https://www.topcoder.com/community/data-science/data-science-tutorials/binary-search/


![Binary_Search](https://github.com/NoriKaneshige/Searching_Algorithm/blob/master/Binary_Search.png)

> Original Solution
``` js
function binarySearch(arr, elem) {
    var start = 0;
    var end = arr.length - 1;
    var middle = Math.floor((start + end) / 2);
    while(arr[middle] !== elem && start <= end) {
        if(elem < arr[middle]){
            end = middle - 1;
        } else {
            start = middle + 1;
        }
        middle = Math.floor((start + end) / 2);
    }
    if(arr[middle] === elem){
        return middle;
    }
    return -1;
}
```
> Refactored Version
``` js
function binarySearch(arr, elem) {
    var start = 0;
    var end = arr.length - 1;
    var middle = Math.floor((start + end) / 2);
    while(arr[middle] !== elem && start <= end) {
        if(elem < arr[middle]) end = middle - 1;
        else start = middle + 1;
        middle = Math.floor((start + end) / 2);
    }
    return arr[middle] === elem ? middle : -1;
}

console.log(binarySearch([2,5,6,9,13,15,28,30], 103)) // -1
console.log(binarySearch([1,2,3,4,5],2)) // 1
console.log(binarySearch([1,2,3,4,5],3)) // 2
console.log(binarySearch([1,2,3,4,5],5)) // 4
console.log(binarySearch([1,2,3,4,5],6)) // -1
console.log(binarySearch([
  5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 
  40, 44, 64, 79, 84, 86, 95, 96, 98, 99
], 10)) // 2
console.log(binarySearch([
  5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 
  40, 44, 64, 79, 84, 86, 95, 96, 98, 99
], 95)) // 16
console.log(binarySearch([
  5, 6, 10, 13, 14, 18, 30, 34, 35, 37, 
  40, 44, 64, 79, 84, 86, 95, 96, 98, 99
], 100)) // -1
```

> ## 3) Naive_String_Search: :cry: 
> Count the number of times a smaller string appears in a longer string

![Naive_String_Search](https://github.com/NoriKaneshige/Searching_Algorithm/blob/master/Naive_String_Search.png)
``` js
function naiveSearch(long, short){
    var count = 0;
    for(var i = 0; i < long.length; i++){
        for(var j = 0; j < short.length; j++){
           if(short[j] !== long[i+j]) break;
           if(j === short.length - 1) count++;
        }
    }
    return count;
}


console.log(naiveSearch("lorie loled", "lol")) // 1
```
