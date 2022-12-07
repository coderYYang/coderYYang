# AngularJS

### 指令

##### ng-app 指令

- **ng-app** 指令定义了 AngularJS 应用程序的 **根元素**。
- **ng-app** 指令在网页加载完毕时会**自动引导**（自动初始化）应用程序。

##### ng-init 指令

- **ng-init** 指令为 AngularJS 应用程序定义了 **初始值**。

##### ng-model 指令

- **ng-model** 指令 **绑定 HTML 元素** 到应用程序数据。
- **ng-model** 指令也可以：
  - 为应用程序数据提供类型验证（number、email、required）。
  - 为应用程序数据提供状态（invalid、dirty、touched、error）。
  - 为 HTML 元素提供 CSS 类。
  - 绑定 HTML 元素到 HTML 表单。

##### ng-repeat 指令

- **ng-repeat** 指令对于集合中（数组中）的每个项会 **克隆一次 HTML 元素**。

##### 创建自定义的指令

- 你可以通过以下方式来调用指令：
  - 元素名
    - `<runoob-directive></runoob-directive>`
  - 属性
    - `<div runoob-directive></div>`
  - 类名
    - `<div class="runoob-directive"></div>`
  - 注释
    - `<!-- directive: runoob-directive -->`

- 通过添加 **restrict** 属性

  ```javascript
  var app = angular.module("myApp", []);
  app.directive("helloAngular", function() {
      return {
          restrict : "A",
          template : "<h1>自定义指令!</h1>"
      };
  });
  // restrict 值可以是以下几种:
  // E 作为元素名使用
  // A 作为属性使用
  // C 作为类名使用
  // M 作为注释使用
  ```

  