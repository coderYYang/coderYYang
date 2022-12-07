# JavaScript面向对象编程（一）：封装

## 1.实例对象的原始模式

把猫看成一个对象，它有名字和颜色

```javascript
let cat = {
    name: '',
    color: ''
}
```

根据这个原型对象的规格，生成两个实例对象

```javascript
let cat = {}; // 创建空对象
cat.name = '大黄'; // 按照原型对象属性赋值
cat.color = '蓝色';
let cat = {};
cat.name = '二哈';
cat.color = '黑色'
```

把两个属性封装在一个对象里面。但是，这样的写法有两个缺点，一是如果多生成几个实例，写起来就非常麻烦；二是实例与原型之间，没有任何办法，可以看出有什么联系

## 2.原始模式改进

```javascript
function Cat(name, color) {
    return {
        name: name,
        color: color
    }
}
```

生成实例对象，等于是在调用函数

```javascript
let cat1 = Cat('大黄', '黄色');
let cat2 = Cat('大毛', '橘色');
```

这种方法的问题依然是，`cat1`和`cat2`之间没有内在的联系，不能反映出它们是同一个原型对象的实例。

## 3.构造函数模式

- 为了解决从原型对象生成实例的问题，JavaScript提供了一个构造函数（Constructor）模式。
- 所谓"构造函数"，其实就是一个普通函数，但是内部使用了`this`变量。对构造函数使用`new`运算符，就能生成实例，并且`this`变量会绑定在实例对象上。

```javascript
function Cat(name, color) {
    this.name = name;
    this.color = color;
}
```

生成实例对象

```javascript
let cat1 = Cat('大黄', '黄色');
let cat2 = Cat('大毛', '橘色');
consloe.log(cat1.name); // 大黄
consloe.log(cat2.color); // 橘色
```

这时`cat1`和`cat2`会自动含有一个`constructor`属性，指向它们的构造函数。

```javascript
console.log(cat1.constructor == Cat); // true
console.log(cat2.constructor == Cat); // true
```

JavaScript还提供了一个`instanceof`运算符，验证原型对象与实例对象之间的关系。

```javascript
console.log(cat1 instanceof Cat); // true
console.log(cat2 instanceof Cat); // true
```

## 4.构造函数模式问题

构造函数方法很好用，但是存在一个浪费内存的问题。

```javascript
function Cat(name, color) {
    this.name = name;
    this.color = color;
    this.type = '猫科动物';
    this.eat = function () {
        console.log('吃老鼠');
    }
}
```

生成实例

```javascript
let cat1 = Cat('大黄', '黄色');
let cat2 = Cat('大毛', '橘色');
consloe.log(cat1.type); // 猫科动物
cat1.eat(); // 吃老鼠
```

表面上好像没什么问题，但是实际上这样做，有一个很大的弊端。那就是对于每一个实例对象，`type`属性和`eat()`方法都是一模一样的内容，每一次生成一个实例，都必须为重复的内容，多占用一些内存。这样既不环保，也缺乏效率。

```javascript
console.log(cat1.eat == cat2.eat); // false
```

让`type`属性和`eat()`方法在内存中只生成一次，然后所有实例都指向那个内存地址

## 5.Prototype模式

- JavaScript规定，每一个构造函数都有一个`prototype`属性，指向另一个对象。这个对象的所有属性和方法，都会被构造函数的实例继承。
- 我们可以把那些不变的属性和方法，直接定义在`prototype`对象上。

```javascript
function Cat(name, color) {
    this.name = name;
    this.color = color;
}
Cat.prototype.type = '猫科动物';
Cat.prototype.eat = function () {
    console.log('吃老鼠');
}
```

生成实例

```javascript
let cat1 = Cat('大黄', '黄色');
let cat2 = Cat('大毛', '橘色');
consloe.log(cat1.type); // 猫科动物
cat1.eat(); // 吃老鼠
```

这时所有实例的`type`属性和`eat()`方法，其实都是同一个内存地址，指向`prototype`对象

```javascript
console.log(cat1.eat == cat2.eat); // true
```

## 6.Prototype模式的验证方法

为了配合`prototype`属性，JavaScript定义了一些辅助方法，帮助我们使用它

1.  **`isPrototypeOf()`**

   这个方法用来判断，某个`proptotype`对象和某个实例之间的关系

   ```javascript
   console.log(Cat.prototype.isPrototypeOf(cat1)); // true
     console.log(Cat.prototype.isPrototypeOf(cat2)); // true
   ```

2. **`hasOwnProperty()`**

   每个实例对象都有一个`hasOwnProperty()`方法，用来判断某一个属性到底是本地属性，还是继承自`prototype`对象的属性。

   ```javascript
   console.log(cat1.hasOwnPrototype('name')); // true
   console.log(cat2.hasOwnPrototype('type')); // false
   ```

3. **`in`运算符**

   `in`运算符可以用来判断，某个实例是否含有某个属性，不管是不是本地属性。

   ```javascript
   console.log('name' in cat1); // true
   console.log('type' in cat1); // true
   ```

   `in`运算符还可以用来遍历某个对象的所有属性。

   ```javascript
   for (let item in cat1) {
       console.log("cat1["+item+"] = " + cat1[item]);
       // cat1[name] = 大黄
       // cat1[color] = 黄色
   }
   ```

   
