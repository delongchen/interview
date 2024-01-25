# quick sort
```typescript
const selectKey = (vec: number[], left: number, right: number) => {
  return right
}

const quickSortHelper = (vec: number[], left: number, right: number) => {
  if (left > right) return

  const _left = left
  const _right = right

  const keyIndex = selectKey(vec, left, right)
  const key = vec[keyIndex]

  while (left < right) {
    while (left < right && vec[right] > key) {
      right -= 1
    }
    if (left < right) {
      vec[left] = vec[right]
      left += 1
    }

    while (left < right && vec[left] < key) {
      left += 1
    }
    if (left < right) {
      vec[right] = vec[left]
      right -= 1
    }
  }

  vec[left] = key

  quickSortHelper(vec, _left, left - 1)
  quickSortHelper(vec, left + 1, _right)
}

const quickSort = (vec: number[]) => {
  quickSortHelper(vec, 0, vec.length - 1)
}
```
