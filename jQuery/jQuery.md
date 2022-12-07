# 自定义名称

```js
// 使用自己的名称（比如 jq）来代替 $ 符号
const jq = jQuery.noConflict();
```

# jQuery事件

| **Event 函数**                  | **绑定函数至**                                 |
| ------------------------------- | ---------------------------------------------- |
| $(document).ready(function)     | 将函数绑定到文档的就绪事件（当文档完成加载时） |
| $(selector).click(function)     | 触发或将函数绑定到被选元素的点击事件           |
| $(selector).dblclick(function)  | 触发或将函数绑定到被选元素的双击事件           |
| $(selector).focus(function)     | 触发或将函数绑定到被选元素的获得焦点事件       |
| $(selector).mouseover(function) | 触发或将函数绑定到被选元素的鼠标悬停事件       |

***

# jQuery 效果

## 隐藏/显示

- **使用 hide() 和 show() 方法来隐藏和显示 HTML 元素**

  ```js
  // 隐藏元素 hide()
  $('.hide').click(function(){
      $('.content').hide(1000);
  });
  
  // 显示元素 show()
  $('.show').click(function () {
      $('.content').show(1000);
  })
  ```

  

- **使用 toggle() 方法来切换 hide() 和 show() 方法。**

  ```js
  // 显示被隐藏的元素，并隐藏已显示的元素
  $('.toggle').click(function () {
      $('.content').toggle(1000);
  })
  ```

  

- **语法：**

  ```js
  $('.hide').hide(speed, callback);
  $('.show').show(speed, callback);
  $('.toggle').toggle(speed, callback);
  ```

  可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

  可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

***

## 淡入淡出

- **四种 fade 方法：**

  - fadeIn()
  - fadeOut()
  - fadeToggle()
  - fadeTo()

- **fadeIn() 用于淡入已隐藏的元素。**

  ```js
  // 使三个矩形淡出
  $('.fade-in').click(function(){
      $('.div1').fadeIn();
      $('.div2').fadeIn('slow');
      $('.div3').fadeIn(3000);
  });
  ```

- **fadeOut() 方法用于淡出可见元素。**

  ```js
  // 使三个矩形淡入
  $('.fade-out').click(function(){
      $('.div1').fadeOut();
      $('.div2').fadeOut('slow');
      $('.div3').fadeOut(3000);
  });
  ```

- **fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。**

  ```js
  // 使三个矩形淡入淡出
  $('.fade-toggle').click(function(){
      $('.div1').fadeToggle();
      $('.div2').fadeToggle('slow');
      $('.div3').fadeToggle(3000);
  });
  ```

- **fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。**

  ```js
  // 使三个矩形淡出
  $('.fade-to').click(function(){
      $('.div1').fadeTo('slow',0.15);
      $('.div2').fadeTo('slow',0.4);
      $('.div3').fadeTo('slow',0.7);
  });
  ```

- **语法：**

  ```js
  $('.fade-in').fadeIn(speed,callback);
  $('.fade-out').fadeOut(speed,callback);
  $('.fade-toggle').fadeToggle(speed,callback);
  $('.fade-to').fadeTo(speed,opacity,callback);
  ```

  可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

  可选的 callback 参数是 fading 完成后所执行的函数名称。

  fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。

***

## 滑动

- **滑动方法：**
  - slideDown()
  - slideUp()
  - slideToggle()

- **slideDown() 方法用于向下滑动元素。**

  ```js
  // 向下滑动元素
  $('.slide-down').click(function () {
      $('.panel').slideDown('slow');
  })
  ```

- **slideUp() 方法用于向上滑动元素。**

  ```js
  // 向上滑动元素
  $('.slide-up').click(function () {
      $('.panel').slideUp('slow');
  })
  ```

- **slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。**

  ```js
  // 上下滑动元素
  $('.slide-toggle').click(function () {
      $('.panel').slideToggle('slow');
  })
  ```

- **语法：**

  ```js
  $('.slide-down').slideDown(speed,callback);
  $('.slide-up').slideUp(speed,callback);
  $('.slide-toggle').slideToggle(speed,callback);
  ```

  可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

  可选的 callback 参数是滑动完成后所执行的函数名称。

***

## 动画

- **animate() 方法用于创建自定义动画。**

  ```js
  $('.animate').animate({params},speed,callback);
  ```

- **语法**

  - 必需的 params 参数定义形成动画的 CSS 属性。
  - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
  - 可选的 callback 参数是动画完成后所执行的函数名称。

- **生成动画的过程中可同时使用多个属性**

  ```js
  // 使用多个属性
  $('.btn1').click(function () {
      $('.animate').animate({
          left: '250px',
          opacity: 0.5,
          width: '150px',
          height: '150px'
      })
  })
  ```

- **animate() 也可以定义相对值（该值相对于元素的当前值）。需要在值的前面加上 += 或 -=**

  ```js
  // 使用相对值
  $('.btn2').click(function () {
      $('.animate').animate({
          left: '250px',
          width: '+=150px',
          height: '+=150px'
      })
  })
  ```

- **使用队列功能，编写多个 animate() 调用，jQuery 会创建包含这些方法调用的“内部”队列。然后逐一运行这些 animate 调用。**

  ```js
  // 使用队列功能
  $('.btn4').click(function () {
      $('.animate').animate({height: '300px', opacity: '0.4'}, "slow");
      $('.animate').animate({width: '300px', opacity: '0.8'}, "slow");
      $('.animate').animate({height: '100px', opacity: '0.4'}, "slow");
      $('.animate').animate({width: '100px', opacity: '0.8'}, "slow");
  })
  $('.btn5').click(function () {
      $('.animate').animate({width: '150px'}, 'slow');
      $('.animate').animate({fontSize: '24px'}, 'slow');
  })
  ```

***

## stop() 停止动画

- **stop() 方法用于停止动画或效果，在它们完成之前。**

  - stop() 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画。

  ```js
  $('.flip').click(function () {
      $('.panel').slideToggle(5000);
  })
  // 停止动画
  $('.stop').click(function () {
      $('.panel').stop();
  })
  ```

- **语法：**

  ```js
  $('.stop').stop(stopAll,goToEnd);
  ```

  可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。

  可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。

***

## Callback 函数

- **Callback 函数在当前动画 100% 完成之后执行。**

  ```js
  $(document).ready(function () {
      $('.btn').click(function () {
          $('p').hide(1000, () => {
              alert('我被隐藏了');
          });
      });
  });
  ```

***

## Chaining

- **Chaining 允许我们在一条语句中允许多个 jQuery 方法（在相同的元素上）。**

  ```js
  $(document).ready(function () {
    $('.btn').click(function () {
      $('p').css('color', 'red').slideUp(1000).slideDown(1000);
    })
  })
  ```

***

# jQuery HTML

## 获取内容和属性

- **获得内容 - text()、html() 以及 val()**

  - text() - 设置或返回所选元素的文本内容
  - html() - 设置或返回所选元素的内容（包括 HTML 标记）
  - val() - 设置或返回表单字段的值

  ```js
  // text() 和 html() 方法来获得内容
  // 设置或返回所选元素的文本内容
  $('.get-text').click(() => {
      alert('text:' + $('.test').text());
  })
  // 设置或返回所选元素的内容（包括 HTML 标记）
  $('.get-html').click(() => {
      alert('html:' + $('.test').html());
  })
  // val() 方法获得输入字段的值
  $('.get-value').click(() => {
      alert('value:' + $('.test3').val());
  })
  ```

- **获取属性 - attr()**

  ```js
  // attr() 方法用于获取属性值
  $('.get-href').click(() => {
      alert('href:' + $('.test2').attr('href'));
  })
  ```

***

## 设置内容和属性

- **设置内容 - text()、html() 以及 val()**

  - text() - 设置或返回所选元素的文本内容
  - html() - 设置或返回所选元素的内容（包括 HTML 标记）
  - val() - 设置或返回表单字段的值

  ```js
  // 设置文本
  $('.set-text').click(() => {
      $('.test1').text('设置文本');
  })
  // 设置 HTML
  $('.set-html').click(() => {
      $('.test2').html('设置 HTML');
  })
  // 设置 value 值
  $('.set-val').click(() => {
      $('.test3').val('设置 value 值');
  })
  ```

- **text()、html() 以及 val() 的回调函数**

  text()、html() 以及 val()，同样拥有回调函数。回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

  ```js
   // text()的回调函数
      $('.callback-text').click(() => {
        $('.test1').text((index, oldVal) => {
          return '旧值：' + oldVal;
        })
      })
      // html()的回调函数
      $('.callback-html').click(() => {
        $('.test2').html((index, oldVal) => {
          return '旧值：' + oldVal;
        })
      })
  ```

- **设置属性 - attr()**

  attr() 方法也用于设置/改变属性值。

  ```js
  //设置/改变属性值。
  $('.change-href').click(function () {
      $('.test4').attr('href', 'bilibili.com');
  });
  ```

  attr() 允许同时设置多个属性。

  ```js
  // 允许您同时设置多个属性
  $('.change-hrefs').click(function () {
      $('.test4').attr({
          'href': 'bilibili.com',
          'title': '666'
      });
  });
  ```

- **回调函数**

  ```js
  // 回调函数
  $('.change-callback-href').click(function(){
      $('.test4').attr('href', (index, oldVal) => {
          return oldVal + '/jQuery';
      });
  });
  ```

***

## 添加元素

- **添加新的 HTML 内容**
  - append() - 在被选元素的结尾插入内容
  - prepend() - 在被选元素的开头插入内容
  - after() - 在被选元素之后插入内容
  - before() - 在被选元素之前插入内容

- **append() 方法在被选元素的结尾插入内容。**

  ```js
  // 追加文本
  $('.btn1').click(() => {
      $("p").append(" <b>Appended text</b>.");
  });
  // 追加列表项
  $('.btn2').click(() => {
      $("ol").append("<li>Appended item</li>");
  });
  ```

- **prepend() 方法在被选元素的开头插入内容。**

  ```js
  // 开头追加文本
  $('.btn3').click(() => {
      $("p").prepend(" <b>开头追加文本</b>");
  });
  // 开头追加列表项
  $('.btn4').click(() => {
      $("ol").prepend("<li>开头追加列表项</li>");
  });
  ```

- **通过 append() 和 prepend() 方法添加若干新元素**

  ```js
  // 追加若干元素
  $('.btn5').click(() => {
      var txt1 = '<p>我是 HTML 创建的元素</p>'; // 以 HTML 创建新元素
      var txt2 = $('<p></p>').text('我是jQuery创建的元素'); // 以 jQuery 创建新元素
      var txt3 = document.createElement('p');
      txt3.innerHTML = '我是创建的 p 标签'; // 通过 DOM 来创建文本
      $('body').append(txt1, txt2, txt3); // 追加新元素
  });
  ```

- **after() 和 before() 方法**

  after() 方法在被选元素之后插入内容。

  ```js
  // before() 方法在被选元素之后插入内容。
  $('.before').click(() => {
      $('img').before('被选元素之后插前内容。')
  })
  ```

  before() 方法在被选元素之前插入内容。

  ```js
  // after() 方法在被选元素之后插入内容。
  $('.after').click(() => {
      $('img').after('被选元素之后插后内容。')
  })
  ```

- **通过 after() 和 before() 方法添加若干新元素**

  ```js
  // 追加若干元素
  $('.more').click(() => {
      var txt1 = "<b>I </b>"; // 以 HTML 创建元素
      var txt2 = $("<i></i>").text("love "); // 通过 jQuery 创建元素
      var txt3 = document.createElement("big"); // 通过 DOM 创建元素
      txt3.innerHTML = "jQuery!";
      $("img").after(txt1, txt2, txt3);
  });
  ```

***

- **删除元素/内容**

  - remove() - 删除被选元素（及其子元素）
  - empty() - 从被选元素中删除子元素

- **remove() 方法删除被选元素及其子元素。**

  ```js
  // remove() 方法删除被选元素及其子元素。
  $('.remove').click(() => {
      $('.div1').remove();
  })
  ```

- **empty() 方法删除被选元素的子元素。**

  ```js
  // empty() 方法删除被选元素的子元素。
  $('.empty').click(() => {
      $('.div1').empty();
  })
  ```

- **remove() 方法也可接受一个参数，允许您对被删元素进行过滤。**

  下面的例子删除 class="isP" 的所有 <p> 元素：

  ```js
  // remove() 方法也可接受一个参数，允许您对被删元素进行过滤。
    $('.btn').click(() => {
      $('p').remove('.isP');
    })
  ```

***

## 获取并设置 CSS 类

- **操作 CSS**

  - addClass() - 向被选元素添加一个或多个类
  - removeClass() - 从被选元素删除一个或多个类
  - toggleClass() - 对被选元素进行添加/删除类的切换操作
  - css() - 设置或返回样式属性

- **addClass() 方法**

  ```js
  // 向元素添加类
  $('.add-class').click(() => {
      $('h1, h2, p').addClass('blue');
      $('div').addClass('important');
  })
  ```

- **在 addClass() 方法中规定多个类**

  ```js
  // 添加多个类
  $('.add-classes').click(() => {
      $('div').addClass('important blue');
  })
  ```

- **removeClass() 方法**

  ```js
  // 从元素上删除类
  $('.remove-class').click(() => {
      $('h1, h2, p').removeClass('blue');
  })
  ```

- **toggleClass() 方法**

  toggleClass() 方法方法对被选元素进行添加/删除类的切换操作

  ```js
  // 切换css类
  $('.toggle').click(() => {
      $('h1, h2, p').toggleClass('blue');
  })
  ```

***

## css() 方法

- **css() 方法设置或返回被选元素的一个或多个样式属性。**

  - 返回 CSS 属性

    **语法：`css("propertyname");`**

    ```js
    // 返回指定的 CSS 属性的值
    $('.back').click(() => {
        alert('背景色为：' + $('p').css('background-color'));
    })
    ```

  - 设置 CSS 属性

    **语法：`css("propertyname","value");`**

    ```js
    // 设置指定的 CSS 属性
    $('.set').click(() => {
        $('p').css('background-color', '#666')
    })
    ```

  - 设置多个 CSS 属性

    **语法：`css({"propertyname":"value","propertyname":"value",...});`**

    ```js
    // 设置多个 CSS 属性
    $('.set-more').click(() => {
        $('p').css({'background-color': '#666', 'color': 'red'});
    })
    ```

## 尺寸

- **jQuery 尺寸 方法**
  - width()
  - height()
  - innerWidth()
  - innerHeight()
  - outerWidth()
  - outerHeight()

- **width() 和 height() 方法**

  width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）。

  height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）。

  ```js
  // width() 和 height() 方法
  $('.btn').click(() => {
      let txt = '';
      txt += '宽度为:' + $('.div1').width();
      txt += '高度为:' + $('.div1').height();
      $('.div1').text(txt);
  })
  ```

- **innerWidth() 和 innerHeight() 方法**

  innerWidth() 方法返回元素的宽度（包括内边距）。

  innerHeight() 方法返回元素的高度（包括内边距）。

  ```js
  // innerWidth() 和 innerHeight() 方法
  $('.btn2').click(() => {
      let txt = '';
      txt += "innerWidth()为: " + $("#div1").innerWidth();
      txt += "innerHeight()为: " + $("#div1").innerHeight();
      $("#div1").html(txt);
  })
  ```

- **outerWidth() 和 outerHeight() 方法**

  outerWidth() 方法返回元素的宽度（包括内边距和边框）。

  outerHeight() 方法返回元素的高度（包括内边距和边框）。

  ```js
  // outerWidth() 和 outerHeight() 方法
  $('.btn3').click(() => {
      let txt = '';
      txt += "outerWidth()为: " + $(".div1").outerWidth() + '<br>';
      txt += "outerHeight()为: " + $(".div1").outerHeight();
      $(".div1").html(txt);
  })
  ```

- **返回文档（HTML 文档）和窗口（浏览器视口）的宽度和高度**

  ```js
  $('.btn4').click(() => {
        let txt="";
        txt+="Document width/height: " + $(document).width();
        txt+="x" + $(document).height() + "\n";
        txt+="Window width/height: " + $(window).width();
        txt+="x" + $(window).height();
        alert(txt);
      });
  ```

- **设置指定的 <div> 元素的宽度和高度**

  ```js
  // 设置指定的 <div> 元素的宽度和高度
  $('.btn5').click(() => {
      $(".div1").width(500).height(500);
  });
  ```

***

# jQuery 遍历

## 遍历 - 祖先

- **向上遍历 DOM 树**

  - parent()
  - parents()
  - parentsUntil()

- **parent() 方法返回被选元素的直接父元素。**

  ```js
  // 向上一级对 DOM 树进行遍历
  $('.parent').click(() => {
      $('span').parent().css({'color': 'red', 'border': '2px solid red'});
  })
  ```

- **parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。**

  ```js
  // 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。
  $('.parents').click(() => {
      $('span').parents().css({'color': 'red', 'border': '2px solid red'});
  })
  ```

  使用可选参数来过滤对祖先元素的搜索。

  下面的例子返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：

  ```js
  // 使用可选参数来过滤对祖先元素的搜索。
  $('.filter').click(() => {
      // 返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：
      $('span').parents('ul').css({'color': 'red', 'border': '2px solid red'});
  })
  ```

- **parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。**

  下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：

  ```js
  // 返回介于两个给定元素之间的所有祖先元素。
  $('.parentsUntil').click(() => {
      // 返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：
      $('span').parentsUntil('div').css({'color': 'red', 'border': '2px solid red'});
  })
  ```

  