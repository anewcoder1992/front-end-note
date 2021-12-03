<!--
 * @Author: your name
 * @Date: 2021-09-10 08:08:04
 * @LastEditTime: 2021-12-03 09:35:19
 * @LastEditors: your name
 * @Description: 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
 * @FilePath: \front-end-note\code snippet\自定义实现的常用hook.md
-->

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
2. 点击元素之外的 hook
 ```js
 export const useClickAway = (ref, onClickAway) => {
  const savedCallback = useRef(onClickAway)
  useEffect(() => {
    savedCallback.current = onClickAway
  }, [onClickAway])
  useEffect(() => {
    function handleClickOutside(event) {
      if (ref.current && !ref.current.contains(event.target)) {
        savedCallback.current()
      }
    }
    // Bind the event listener
    document.addEventListener('mousedown', handleClickOutside)
    return () => {
      // Unbind the event listener on clean up
      document.removeEventListener('mousedown', handleClickOutside)
    }
  }, [ref])
}
 ```
 3. 定时器hook 
 ```js
 export function useInterval(callback, delay) {
  const savedCallback = useRef()

  // 保存新回调
  useEffect(() => {
    savedCallback.current = callback
  })

  // 建立 interval
  useEffect(() => {
    function tick() {
      savedCallback.current()
    }
    if (delay !== null) {
      let id = setInterval(tick, delay)
      return () => {
        clearInterval(id)
      }
    }
  }, [delay])
}
 ```
