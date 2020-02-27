# JavaScript Brushup

# Points to keep in mind

1. To make a copy of an array `copyArr = [...arr]`. The `...` is the spread operator.
2. To make a copy of an object `copyObj = {...obj}`. The `...` is the spread operator.
3. `arr.splice(index, number)` or `arr.splice(index)` changes the original array.
4. `arr.slice(index, number)` or `arr.slice(index)` doesn't changes the original array.
5. `arr.map((element) ⇒ {})` can also be used as `arr.map((element,index) ⇒ {})`. Here the index is unique for each element being mapped. *(Optional Note: try to use some other index while mapping lists in React as every time component is called to be re-rendered, new id's will be generated and hence the component will re-render even if the whole list is the same.)*
6.