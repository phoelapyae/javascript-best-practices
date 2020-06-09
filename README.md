# JavaScript Best Practices

### JavaScript Tricks

#### Number to string / String to number

Amateur:

```js
let num = 15;
let s = num.toString(); // number to string
let n = Number(s); // string to number
```

Pro:

```js
let num = 15;
let s = num + ''; // number to string
let n = + s; // string to number
```

#### The Ternary Operator

Amateur:

```js
let hungry = true;
let eat;
if (hungry) {
  eat = 'yes';
} else {
  eat = 'no';
}
```

Pro:

```js
let hungry = true;
let eat = hungry ? 'yes' : 'non';
```

#### Dynamic Properties in Objects

Amateur:

```js
let dynamic = 'value';
let user = {
  id: 1
};
user[dynamic] = 'other value';
```

Pro:

```js
let dynamic = 'value';
let user = {
  id: 1,
  [dynamic] = 'other value'
};
```

#### Array to Object

Amateur:

```js
let arr = ['value1', 'value2', 'value3'];
let arrObject = {};
for (let i = 0; i < arr.length; ++i) {
  if (arr[i] !== undefined) {
    arrObject[i] = arr[i];
  }
}
```

Pro:

```js
let arr = ['value1', 'value2', 'value3'];
let arrObject = {...arr};
```

#### Removing Duplicates

Amateur:

```js
let array = [100, 23, 23, 23, 23, 67, 45];
let outputArray = [];
let flag = false;
for (let j = 0; j < array.legth; j++) {
  for (let k = 0; k < outputArray.length; k++) {
    if (array[j] == outputArray[k]) {
      flag = true;
    }
  }
  if (flag == false) {
    outputArray.push(array[j]);
  }
  flag = false;
}
// outputArray = [100, 23, 67, 45]
```

Pro:

```js
let array = [100, 23, 23, 23, 23, 67, 45];
let outputArray = Array.from(new Set(array));
// outputArray = [100, 23, 67, 45]
```

#### Populating an Array

Amateur:

```js
for (let i = 0; i < arraysize; i++) {
  filledArray[i] = {'hello': 'goodbye'};
}
```

Pro:

```js
let filledArray = new Array(arraySize).fill(null).map(() => ({'hello': 'goodbye'}));
```

#### Object to Array

Amateur:

```js
let numbers = {
  one: 1,
  two: 2,
};
let keys = [];
for (let number in numbers) {
  if (numbers.hasOwnProperty(number)) {
    keys.push(number);
  }
}
// key = ['one', 'two']
```

Pro:

```js
let numbers = {
  one: 1,
  two: 2,
}
let key = Object.keys(numbers); // key = ['one', 'two']
let value = Object.values(numbers); // value = [1, 2]
let entry = Object.entries(numbers); // entry = [['one': 1], ['two': 2]]
```

#### Shuffle an Array

```js
function shuffle(array) {
  array.sort(() => Math.random() - 0.5);
}

let arr = [1, 2, 3, 4, 5];
shuffle(arr);

// [3, 1, 5, 4, 2]
```

