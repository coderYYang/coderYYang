# TypeScript

## 安装TypeScript

- npm install -g typescript
- cmd查看版本号
  - `tsc -v`

- 将 TypeScript 转换为 JavaScript 代码
  - `tsc xxx.ts`

***

## 基础类型

- number 数字类型

  ```typescript
  // 声明一个变量a，同时它的类型为number
  let a: number;
  // a的类型设置为number，a只能是数字
  a = 10;
  // a = 'hello'; 代码会报错，类型为number，不能赋值为字符串
  ```

- string 字符串类型

  ```typescript
  // 声明一个变量a，同时它的类型为number
  let b: string;
  b = 'Hello Ts';
  ```

- boolean 布尔类型

  ```typescript
  // let c : boolean = true;
  // 如果变量的声明和赋值同时进行，TS可以自动进行类型检测
  let c = true;
  
  c = false;
  // c = 123; 报错
  ```

- 函数类型

  ```typescript
  // 声明函数sum 同时传入a和b两个值，它们的值类型都为number，切函数返回值的类型也为number
  function sum(a : number, b : number): number { // 函数返回值为number
      return a + b;
  }
  sum(123, 456);
  ```

- 直接使用字面量进行类型声明

  ```typescript
  let a: 10;
  ```

- 使用 | 来连接多个类型（联合类型）

  ```typescript
  let b: 'male' | 'female';
  b = 'male';
  b = 'female';
  
  let c: boolean | string;
  c = true;
  c = 'hello';
  ```

- any 表示任意类型，类型设置为any，相当于关闭TS类型检测

  ```typescript
  // 使用TS时，不建议使用any
  // let d : any; （显示的any）
  
  // 声明变量不指定类型，TS解析器会自动判断类型为any（隐式的any）
  let d;
  d = 10;
  d = 'hello';
  d = true;
  ```

- unknown 位置类型

  ```typescript
  let e: unknown;
  e = 10;
  e = 'hello';
  e = true;
  
  let s: string;
  // d 的类型时any，它可以赋值给任意变量
  //s = d;
  
  e = 'hello';
  // unknown 实际上就是一个类型安全的any
  // unknown 类型的变量，不能直接赋值给其它变量
  if (typeof e === 'string') {
    s = e;
  }
  ```

- 断言类型，可以告诉解释器变量的实际类型

  ```typescript
  /**
   * 语法：
   *     变量 as 类型
   *     <类型> 变量
   */
  s = e as string;
  e = <string>e;
  ```

- void 用来标识为空，以函数为例，表示没有返回值(空值，undefined)

  ```typescript
  // 没有返回值
  function fu(num): void {
  }
  ```

- never 表示永远不会返回值结果

  ```typescript
  // 一般用于返回错误
  function fu1(): never {
    throw new Error('报错了')
  }
  ```

- object 表示js对象

  ```typescript
  let a: object;
  
  a = {};
  a = function () {
  };
  
  // {} 用来指定对象中可以包含那些属性
  // 语法：{属性名: 属性值}
  // 属性名后加上?，表示属性是可选的
  let b: { name: string, age?: number };
  b = {name: 'yy', age: 18};
  
  // [propName: string]: any 表示任意类型属性
  let c: { name: string, [propName: string]: any };
  c = {name: '猪八戒', age: 18, sex: '男'};
  ```

- 函数结构的类型声明

  ```typescript
  /**
   * 设置函数结构的类型声明
   * 语法：(形参: 类型, 形参: 类型 ...) => 返回值
   */
  let d: (a: number, b: number) => number;
  d = function (n1, n2): number {
    return n1 + n2;
  };
  ```

- 数组类型声明

  ```typescript
  /**
   * 数组的类型声明
   *    类型[]
   *    Array<类型>
   */
  // string[] 表示字符串数组
  let e: string[];
  e = ['a', 'b', 'c'];
  
  // number[] 表示数值数组
  let f: number[];
  
  let g: Array<number>;
  g = [1, 2, 3];
  ```

- tuple 元组

  ```typescript
  /**
   * tuple
   * 元组，元组就是固定长度的数组
   *    语法： [类型, 类型]
   */
  let h: [string, string];
  h = ['hello', 'abc'];
  ```

- enum

  ```typescript
  /**
   * enum
   * 枚举
   */
  enum Gender{
    Male, // 编辑器中Male会默认等于0
    Female // 编辑器中Female会默认等于1
  }
  let i: {name: string, gender: Gender};
  i = {
    name: 'yy',
    gender: Gender.Male
  }
  // console.log(i.gender === Gender.Male);
  ```

- & 表示同时 与

  ```typescript
  // & 表示同时 与
  let j: {name: string} & {age: number};
  // j = {name: 'yy', age: 18}
  ```

- 类型别名

  ```typescript
  // 类型别名
  type myType = 1 | 2 | 3 | 4 | 5;
  let k: myType;
  let l: myType;
  let m: myType;
  
  k = 2;
  ```

***

## tsconfig.js 配置

```typescript
{
  /*
    tsconfig.json 是ts编译器的配置文件，ts编译器可以根据他的信息来对代码进行编译
    "include" 用来指定那些ts文件需要被编译
        路径： ** 任意目录
              * 任意文件
    "exclude" 不需要被编译的文件目录(一般不设置)
        默认值：["node_modules", "bower_components", "jspm_packages"]
  */
  "include": [
    "./src/**/*"
  ],
  //  "exclude": [
  //    "./src/hello/**/*"
  //  ]
  /*
    "compilerOptions" 编译器选项
  */
  "compilerOptions": {
    // 设置ts编译的目标版本
    "target": "ES6",
    // 指定要使用的模块化的规范
    "module": "ES6",
    // "lib": [], // 用来指定项目中要使用的库

    // 指定编译后的文件所在目录
    "outDir": "./dist",
    // "outFile": "./dist/app.js", // 将代码合并为一个文件 设置outFile后，所有的全局作用域中的代码会合并到同一个文件中

    // 是否对js文件进行编译
    "allowJs": false,
    // 是否检查js代码是否符合语法规范
    "checkJs": false,
    // 是否移除注释
    "removeComments": false,
    // 不生成编译后的文件
    "noEmit": false,
    // 当有错误时，不生成编译后的文件
    "noEmitOnError": false,
    // 用来设置编译后有的文件是否使用严格模式
    "alwaysStrict": false,
    // 不允许隐式any类型
    "noImplicitAny": false,
    // 不允许不明确类型的this
    "noImplicitThis": false,
    // 严格检查空值
    "strictNullChecks": false,
    // 严格检查的总开关
    "strict": false
  }
}
```



