# js 深克隆对象
```javascript
const deepClone = (target: any, cache: WeakMap<any, any>) => {
  if (typeof target !== 'object' || target === null) {
    return target
  }

  const exist = cache.get(target)
  if (exist !== undefined) {
    return exist
  }

  const result = Array.isArray(target) ? [] : {}

  const keys = Reflect.ownKeys(target)
  if (keys.length === 0) {
    return target
  }

  cache.set(target, result)

  for (const key of keys) {
    const item = Reflect.get(target, key)
    if (typeof item === 'object' && item !== null) {
      Reflect.set(result, key, deepClone(item, cache))
    } else {
      Reflect.set(result, key, item)
    }
  }

  return result
}

const clone = (target: any) => deepClone(target, new WeakMap)
```
