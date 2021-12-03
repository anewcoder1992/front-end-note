
react实现 敏感词汇或者需要高亮的词汇渲染

```js
const renderItem = (str: string, search: string) => {
    if (!search) return str;
      let  regString = str
    if(Array.isArray(search)){
      regString = search.join('|')
    }
    const reg = new RegExp(regString, 'ig');
    const splitedElements = str.split(reg);
    const matchedElements = str.match(reg) as Array<string>;
    return (
      <React.Fragment>
        {
          matchedElements.map((_, index) => {
            return (
              <React.Fragment key={ index }>
                <span>{ splitedElements[index] }</span>
                <span className="highlight">{ matchedElements[index] }</span>
              </React.Fragment>
            )
          })
        }
        <span>
          { splitedElements[splitedElements.length - 1] || '' }
        </span>
      </React.Fragment>
    )
  };
```