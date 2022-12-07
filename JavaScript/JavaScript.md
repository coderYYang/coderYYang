# JavaScript

# Array方法

## 不会改变原数组

1. **`concat()`**

   - 合并数组，可以合并一个或多个数组，会返回合并数组之后的数据，不会改变原来的数组

2. **`join()`**

   - 将数组转为字符串并返回转化的字符串数据，不会改变原来的数组

3. **`slice()`**

   - 截取指定位置的数组，并且返回截取的数组，不会改变原数组

4. **`toString()`**

   - 将数组转换成字符串，类似于没有参数的join()。该方法会在数据发生隐式类型转换时被自动调用，如果手动调用，就是直接转为字符串。不会改变原数组

5. **`valueOf()`**

   - 返回数组的原始值（一般情况下其实就是数组自身），一般由js在后台调用，并不显式的出现在代码中

6. **`indexOf()`**

   - 根据指定的数据，从左向右，查询在数组中出现的位置，如果不存在指定的数据，返回-1，找到了指定的数据返回该数据的索引

7. **`lastIndexOf()`**

   - 根据指定的数据，从左向右，查询在数组中出现的位置，如果不存在指定的数据，返回-1，找到了指定的数据返回该数据的索引

8. **`forEach()`**

   - 用来遍历数组，没有返回值
   - forEach方法中的function回调有三个参数：
     - 第一个参数是遍历的数组内容，
     - 第二个参数是对应的数组索引
     - 第三个参数是数组本身

9. **`map()`**

   - 同forEach功能；
   - map的回调函数会将执行结果返回，最后map将所有回调函数的返回值组成新数组返回。
     - 参数：map(callback);callback默认有三个参数，分别为value，index，self。跟上面的forEach()的参数一样

10. **`filter()`**

    - 同forEach功能；filter的回调函数需要返回布尔值，当为true时，将本次数组的数据返回给filter，最后filter将所有回调函数的返回值组成新数组返回（此功能可理解为“过滤”）
      - 参数：filter(callback);callback默认有三个参数，分别为value，index，self。

11. **`every()`**

    - 判断数组中每一项是否都满足条件，只有所有项都满足条件，才会返回true。
      - 参数：every()接收一个回调函数作为参数，这个回调函数需要有返回值，every(callback);callback默认有三个参数，分别为value，index，self。
        1. 当回调函数的返回值为true时，类似于forEach的功能，遍历所有；如果为false，那么停止执行，后面的数据不再遍历，停在第一个返回false的位置。
        2. 当每个回调函数的返回值都为true时，every的返回值为true，只要有一个回调函数的返回值为false，every的返回值都为false

12. **`some()`**

    - 判断数组中是否存在满足条件的项，只要有一项满足条件，就会返回true。
      - 参数：some()接收一个回调函数作为参数，这个回调函数需要有返回值，some(callback);callback默认有三个参数，分别为value，index，

    1. 因为要判断数组中的每一项，只要有一个回调函数返回true，some都会返回true，所以与every正好相反，当遇到一个回调函数的返回值为true时，可以确定结果，那么停止执行，后面都数据不再遍历，停在第一个返回true的位置；当回调函数的返回值为false时，需要继续向后执行，到最后才能确定结果，所以会遍历所有数据，实现类似于forEach的功能，遍历所有。
    2. 因为要判断数组中的每一项，只要有一个回调函数返回true，some都会返回true，所以与every正好相反，当遇到一个回调函数的返回值为true时，可以确定结果，那么停止执行，后面都数据不再遍历，停在第一个返回true的位置；当回调函数的返回值为false时，需要继续向后执行，到最后才能确定结果，所以会遍历所有数据，实现类似于forEach的功能，遍历所有。
    3. 与every相反，只要有一个回调函数的返回值都为true，some的返回值为true，所有回调函数的返回值为false，some的返回值才为false

13. **`reduce()`**

    - 从数组的第一项开始，逐个遍历到最后，迭代数组的所有项，然后构建一个最终返回的值。
      - 参数：reduce()接收一个或两个参数：第一个是回调函数，表示在数组的每一项上调用的函数；第二个参数（可选的）作为归并的初始值，被回调函数第一次执行时的第一个参数接收。 reduce(callback,initial);callback默认有四个参数，分别为prev，now，index，self。 callback返回的任何值都会作为下一次执行的第一个参数。 如果initial参数被省略，那么第一次迭代发生在数组的第二项上，因此callback的第一个参数是数组的第一项，第二个参数就是数组的第二项。

14. **`reduceRight()`**

    - （与reduce类似）从数组的最后一项开始，向前逐个遍历到第一位，迭代数组的所有项，然后构建一个最终返回的值。
      - 参数：同reduce。 demo：同reduce

## 会改表原数组

1. **`unshift()`**
   - 在数组的首位新增一个或多数据，并且返回新数组的长度，会改变原来的数组
     - `unshift()`方法返回的数据是新数组的长度，它增加的数据可以是一个也可以是多个，可以理解为增加一连串的数据，
2. **`shift()`**
   - 删除数组的第一位数据，并且返回新数组的长度，会改变原来的数组
3. **`push()`**
   - 在数组的最后一位新增一个或多个数据，并且返回新数组的长度，会改变原来的数组
     - push()方法返回的是数据是新数组的长度，它增加的数据可以是一个也可以是多个，可以理解为增加一连串的数据
4. **`pop()`**
   - 删除数组的最后一位，并且返回删除的数据，会改变原来的数组
5. **`sort()`**
   - 对数组内的数据进行排序(默认为升序)，并且返回排过序的新数组，会改变原来的数组
6. **`reverse()`**
   - 将数组的数据进行反转，并且返回反转后的数组，会改变原数组
7. **`splice()`**
   - 向数组中添加，或从数组删除，或替换数组中的元素，然后返回被删除/替换的元素。
     - `splice(start,num,data1,data2,...);` 所有参数全部可选。　

# 箭头函数和普通函数区别

1. 箭头函数没有prototype属性

   ```javascript
   let fun = () => {};
   console.log(fun.prototype === undefined); // true
   ```

2. 写法不一样

   ```javascript
   // 普通函数
   function fun1() {
       console.log('Hello World');
   }
   // 箭头函数
   let fun2 = () => {
       console.log('Hello World');
   }
   ```

3. 普通函数存在变量提升的现象

   - 普通函数的this指向的是谁调用该函数就指向谁
   - 箭头函数的this指向的是在你书写代码时候的上下文环境对象的this，如果没有上下文环境对象，那么就指向最外层对象window。

   ```javascript
   // 普通函数
   fun1();
   function fun1() {
       console.log('Hello World');
   }
   // 箭头函数
   fun2(); // 或报错
   let fun2 = () => {
       console.log('Hello World');
   }
   ```

4. 箭头函数不能作为构造函数使用

   ```javascript
   // 普通函数
   function fun1(name, age) {
       this.name = name;
       this.age = age;
   }
   let obj1 = new fun1('YY', 18);
   console.log(obj1.name, obj1.age); // YY  18
   // 箭头函数
   let fun2 = (name) => {
       this.name = name;
   }
   let obj2 = new fun2('YY');
   console.log(obj2.name); // undefined
   ```

5. 两者的this指向不同

   ```javascript
   let num = 1;
   // 普通函数
   function fun1() {
       console.log(this); // Number{1}
   }
   fun1.call(num);
   // 箭头函数
   let fun2 = () => {
       console.log(this); // Window{...}
   }
   fun2.call(num);
   ```

6. 箭头函数没有new.target

   - 先说明下new.target是干嘛的，这家伙是用来检测函数是否被当做构造函数使用，他会返回一个指向构造函数的引用。
   - 因为箭头函数不能当做构造函数使用，自然是没有new.target的。

   ```javascript
   // 普通函数
   function fun1() {
       console.log(new.target); // 会打印fun1函数本身
   }
   new fun1(); // 会打印fun1函数本身
   // 箭头函数
   let fun2 = () => {
       console.log(new.target); // new.target 报错
   }
   ```

7. 箭头函数的arguments指向其父级函数作用域的arguments

   ```javascript
   // 普通函数
   function fun1() {
       console.log('Fun1', arguments); // Arguments['Hello World', callee: ƒ, Symbol(Symbol.iterator): ƒ]
       // 箭头函数
       let fun2 = () => {
       console.log('Fun2', arguments); // Arguments['Hello World', callee: ƒ, Symbol(Symbol.iterator): ƒ]
       }
       fun2('aaa');
     }
   fun1('Hello World');
   ```

# 闭包

1. 闭包的特性
   1. 函数嵌套函数
   2. 函数内部可以引用函数外部的参数和变量
   3. 参数和变量不会被垃圾回收机制回收
   4. 闭包就是能够读取其他函数内部变量的函数
2. 闭包的优缺点
   1. 优点
      - 可以读取函数内部的变量
      - 可以避免全局污染
   2. 缺点
      - 闭包会导致变量不会被垃圾回收机制所清除，会大量消耗内存；
      - 不恰当的使用闭包可能会造成内存泄漏的问题；

# DOM操作

```html
<div class="wrapper">
  <a href="#" id="a1">百度</a>
  <h3>我是h3</h3>
</div>
```

```javascript
  let wrapper = document.querySelector('.wrapper');
  let a1 = document.querySelector('#a1');
  let h3 = document.querySelector('h3');

  // 获取/设置元素的属性值
  console.log(a1.getAttribute('href')); // 传入元素的属性名，如果有返回属性名的值，没有返回null
  a1.setAttribute('name', '123'); // 设置元素的属性名和属性名的值

  // 创建节点
  let div = document.createElement('div'); // 创建一个html元素
  let div1 = document.createTextNode('123456'); // 创建一个文本节点
  let div2 = document.createAttribute('class'); // 创建一个属性节点
  console.log(div1, div2)

  // 增添节点
  wrapper.appendChild(document.createElement('div')); // 往wrapper内部最后面添加一个节点，参数是节点类型
  wrapper.insertBefore(document.createElement('span'), a1); // 在wrapper内部的中在a1前面插入span

  // 删除节点
  wrapper.removeChild(a1); // 删除当前节点下指定的子节点，删除成功返回该被删除的节点，否则返回null

  // 获取当前元素的父节点
  console.log(h3.parentNode); // 返回当前元素的父节点对象

  // 获取当前元素的子节点
  console.log(wrapper.children); // 返回当前元素所有子元素节点对象，只返回HTML节点
  console.log(wrapper.childNodes); // 返回当前元素多有子节点，包括文本，HTML，属性节点。（回车也会当做一个节点）
  console.log(wrapper.firstChild); // 返回当前元素的第一个子节点对象
  console.log(wrapper.lastChild); // 返回当前元素的最后一个子节点对象

  // 获取当前元素的同级元素
  console.log(h3.nextSibling); // 返回当前元素的下一个同级元素 没有就返回null
  console.log(h3.previousSibling); // 返回当前元素上一个同级元素 没有就返回null

  // 获取当前元素的文本
  console.log(h3.innerHTML); // 返回元素的所有文本，包括html代码
  console.log(h3.innerText); // 返回当前元素的自身及子代所有文本值，只是文本内容，不包括html代码

  // 获取当前节点的节点类型
  console.log(div.nodeType); // 返回节点的类型,数字形式（1-12）常见几个1：元素节点，2：属性节点，3：文本节点

  //设置样式
  h3.style.color = '#eea'; // 设置元素的样式时使用style，这里以设置文字颜色为例
```

***

# HTML

## select 下拉菜单

1. ```html
   <select id="footSel">
   	<option value="1">黄金糕</option>
   	<option value="2">双皮奶</option>
   	<option value="3">盒子精</option>
   	<option value="4">面包</option>
   	<option value="5">奶茶</option>
   </select>
   ```

   

2. ```javascript
   //1：获取select对象： 
   var  sel = document.getElementById("citySel");
   // sel.value = '33'; //通过value添加默认选中
   
   sel.selectedIndex = 4;//通过索引添加默认选中
   //selectedIndex 属性可设置或返回下拉列表中被选选项的索引号。
   sel.onchange = function () {
   //onchange时间 当改变选择时调用的事件。
   //2：取到选中项的索引：
   var index=sel.selectedIndex;
   // selectedIndex是所选中的项的index
   
       	
   //3：获取选中项的value：  
   sel.options[index].value;
   console.log(sel.options[index].value);
   			 
   //4：取到选中项的文本内容：  
   sel[index].text;
   console.log(sel.options[index].text)
   }
   ```


***

## textarea 标签

`textarea` 标签定义多行的文本输入控件。

- 文本区中可容纳无限数量的文本，其中的文本的默认字体是等宽字体，可以通过 cols 和 rows 属性来规定 textarea 的尺寸，不过更好的办法是使用 CSS 的 height 和 width 属性。

***

## input 标签

`input` 标签用于搜集用户信息。

### text 属性(输入类型)

1. `text` 默认。定义单行输入字段，用户可在其中输入文本。默认是 20 个字符。
2. `radio` 定义单选框
3. `ckeckbox` 定义复选框
4. `button` 定义可点击的按钮
5. `passwprd` 定义密码字段。字段中的字符会被遮蔽
6. `color` 输入类型用于规定颜色
7. `email` 输入类型用于应该包含电邮地址的输入字段
8. `file` 输入类型用于文件上传
9. `number` 输入类型用于包含数字值的输入字段
10. `range` 
    - 输入类型用于应该包含指定范围值的输入字段
    - 类型显示为滑块

11. `reset` 输入类型定义重置按钮，重置按钮会把所有表单字段重置为初始值

12. `submit` 输入类型定义提交按钮
13. `tel` 输入类型用于应该包含电话号码的输入字段
14. `url` 输入类型用于应该包含 URL 地址的输入字段

### 日期和时间选择器

- date - 选择日、月、年
- month - 选择月、年
- week - 选择周、年
- time - 选择时间（时、分）
- datetime - 选择时间、日期、月、年（UTC 时间）
- datetime-local - 选择时间、日期、月、年（本地时间）

***
