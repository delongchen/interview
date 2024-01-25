# ts 堆实现

```typescript
// a < b -> result < 0
// a == b -> result == 0
// a > b -> result > 0
type CompareFn<T = number> = (a: T, b: T) => number

export interface Heap<T = number> {
  vec: T[]
  push: (value: T) => void
  pop: () => T | null
  iter: () => Generator<T>
  iterWithCopy: () => Generator<T>
}

export interface KHeap<T = number> extends Heap<T> {
  feed: (value: T) => void
}

const swap = (vec: Array<any>, i1: number, i2: number) => {
  const temp = vec[i1]
  vec[i1] = vec[i2]
  vec[i2] = temp
}

// sift up the last element
const heapSiftUp = <T = number>(vec: T[], compareFn: CompareFn<T>) => {
  let i = vec.length - 1

  // if length of vec is 0 or 1, it will not enter this loop
  while (i > 0) {
    const parent = (i - 1) >> 1
    if (compareFn(vec[i], vec[parent]) >= 0) {
      break
    }
    swap(vec, parent, i)
    i = parent
  }
}

const heapPush = <T = number>(value: T, vec: T[], compareFn: CompareFn<T>) => {
  vec.push(value)
  heapSiftUp(vec, compareFn)
}


const heapSiftDown = <T = number>(vec: T[], compareFn: CompareFn<T>) => {
  const halfOfVec = vec.length >> 1
  let i = 0

  while (i < halfOfVec) {
    const leftChildrenIndex = (i << 1) + 1
    const leftChildrenValue = vec[leftChildrenIndex]

    let childrenIndex = leftChildrenIndex
    let childrenValue = leftChildrenValue

    const rightChildrenIndex = leftChildrenIndex + 1

    if (
      rightChildrenIndex < vec.length &&
      compareFn(vec[rightChildrenIndex], leftChildrenValue) < 0
    ) {
      childrenIndex = rightChildrenIndex
      childrenValue = vec[rightChildrenIndex]
    }

    if (compareFn(vec[i], childrenValue) <= 0) {
      break
    }

    swap(vec, i, childrenIndex)
    i = childrenIndex
  }
}

const heapPop = <T = number>(vec: T[], compareFn: CompareFn<T>): T | null => {
  if (vec.length === 0) {
    return null
  }

  if (vec.length > 1) {
    swap(vec, 0, vec.length - 1)
  }

  const result = vec.pop()!
  heapSiftDown(vec, compareFn)
  return result
}

function* heapIter<T = number>(vec: T[], compareFn: CompareFn<T>) {
  while (vec.length > 0) {
    yield heapPop(vec, compareFn)!
  }
}

export const createHeap = <T = number>(compareFn: CompareFn<T>): Heap<T> => {
  const vec: T[] = []

  const push = (value: T) => heapPush(value, vec, compareFn)
  const pop = () => heapPop<T>(vec, compareFn)
  const iter = () => heapIter(vec, compareFn)
  const iterWithCopy = () => heapIter(Array.from(vec), compareFn)

  return {
    pop, push, vec, iter, iterWithCopy
  }
}

// k-heap is a heap that only keep k smallest elements
export const createKHeap = <T = number>(k: number, compareFn: CompareFn<T>): KHeap<T> => {
  const heap = createHeap(compareFn)

  const { pop, push, vec } = heap

  const feed = (value: T) => {
    if (vec.length < k) {
      push(value)
      return
    }

    if (compareFn(value, vec[0]) > 0) {
      pop()
      push(value)
    }
  }

  return {
    ...heap,
    feed
  }
}
```
