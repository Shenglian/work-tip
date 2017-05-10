## Object

### toString 

```js

  let _toString = Object.prototype.toString;

  // The PlainObject type is a JavaScript object containing zero or more key-value pairs.‍
  // http://stackoverflow.com/questions/8892465/javascript-object-object-means
  // http://stackoverflow.com/questions/29795330/compare-tostring-call-against-tostring
  function isPlainObject (obj) {
    return _toString.call(obj) === '[object Object]';
  }

```

### assign 

```js
Object.assign(target, ...sources)
  // method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

  // 可以用來設定修改多值 (針對存在的)
  Object.assign(oneElement, {
    value: 'hello',
    id: 'world',
  });

  // 要刪除屬性，設定成 null 就好
  oneElement.value = null

```

### create

```js

// method creates a new object with the specified prototype object and properties.
Object.create(proto, [ propertiesObject ]);
  
```


### Keys 

```js 

Object.keys(Obj);

const obj = {
  a: 'a',
  b: 'b',
};

console.log(Object.keys(obj)); // ["a", "b"]

// Object.keys 可以用來取代原來的 for ... in 增加可讀性

```

### Values

```js

const obj = {
  a: 1,
  b: 2, 
  c: 3,
};

Object.values(Obj); // [1,2,3];

```

### getOwnPropertyNames

> Object.getOwnPropertyNames() 方法返回一個指定對象的所有自身屬性名稱（包含 non-enumeralbe properties）

```js

Object.getOwnPropertyNames(obj)

```

和 Object.keys 的區別在能夠獲得自身全部的屬性，包含 non-enumerabled

### hasOwnProperty

> hasOwnProperty() 方法是用來判斷某個對象是否含有指定的屬性。

```js

obj.hasOwnProperty(prop);

```

在沒有 Object.keys 之前，可以利用 hasOwnProperty，讓 for in 達到類似的效果。

```js

for (let key in obj) {
  // 濾掉原型上面的方法。
  if (obj.hasOwnProperty(key)) {

  }
}

```


### isPrototypeOf

> isPrototypeOf() 方法是測試一個對象是否存在在另一個對象的原型鏈上面。

```js

prototype.isPrototypeOf(object);

```

```js

function Rectangle() {};
const rec = new Rectangle();
Rectangle.prototype.isPrototypeOf(rec); // true

```

### propertyIsEnumerable 

> propertyIsEnumerable() 方法返回一個 boolen，指名說目前屬性名稱，是否當前物件可以 enumerable 的屬性。

```js

obj.propertyIsEnumerable(prop);

```

```js

const obj = {
  a: 1,
  b: 2,
};

obj.propertyIsEnumerable('a'); // true


```

1. 從原型鍊繼承上的屬性，會返回 false
2. 對象沒有指定的屬性，會返回 false

[資料來源：](http://yanhaijing.com/javascript/2015/05/08/member-of-object/)