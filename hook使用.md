1. props为数组或者对象时 变化 如何去判断 是否变化用去子组件的effect
```js
function usePrevious(value) {
  const ref = useRef();
  useEffect(() => {
    ref.current = value;
  });
  return ref.current;
}


const useCompare = val => {
  console.log(`val=${val}`);
  const prevVal = usePrevious(val);
  console.log(`prevVal=${prevVal}`);

  return prevVal !== val;
};
```
