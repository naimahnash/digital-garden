# Binary Search

```typescript
/**
 *
 * @param arr a sorted array
 * @param search we are searching for this value in the array
 *
 * @returns the index of the searched for value, -1 if isn't in the array
 */
const binarySearchRecursive = (arr: number[], search: number) => {
  if (arr.length === 0) return -1;
  if (arr.length < 2) {
    return arr[0] === search ? 0 : -1;
  }
  let mid = Math.floor(arr.length / 2);

  if (arr[mid] === search) return mid;

  // if arr[mid] is greater than search
  // search lower half of array
  if (arr[mid] > search)
    return mid + binarySearchRecursive(arr.slice(0, mid - 1), search);

  // if arr[mid] is less than search
  // search upper half of array
  if (arr[mid] < search)
    return mid + binarySearchRecursive(arr.slice(mid + 1, arr.length), search);
};

/**
 *
 * @param arr a sorted array
 * @param search we are searching for this value in the array
 *
 * @returns the index of the searched for value, -1 if isn't in the array
 */
const binarySearchIterative = (arr: number[], search: number) => {
  if (arr.length === 0) return -1;
  let low = 0,
    high = arr.length - 1;
  while (high >= low) {
    let mid = Math.floor((high + low) / 2);
    if (arr[mid] === search) return mid;
    if (arr[mid] > search) {
      // if val at midpoint is greater than search,
      // search bottom half of array
      high = mid - 1;
    }
    if (arr[mid] < search) {
      // otherwise
      low = mid + 1;
    }
  }
  return -1;
};
```
