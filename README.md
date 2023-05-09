> ## 前端基础与技术交叉

### CSS 动画和 JS 动画的优缺点

- CSS 动画
  - 优点
    - CSS动画比较流畅：把所有 DOM 操作集中起来，只进行一次重排或重绘，渲染时不会触发主线程
  - 缺点
    - 无法绑定事件回调函数
    - 代码比较冗余
    - 兼容性较差
- JS 动画
  - 优点
    - 可以实现复杂效果
    - 兼容性较好
  - 缺点
    - 执行时在主线程中运行，主线程中同时还可能存在其它 JS 脚本，可能会导致线程堵塞等情况
    - 代码量较大

### 路由与单页面应用

- 路由：一个路由（route）就是一组映射关系（key - value），多个路由需要路由器（router）进行管理
  - key 是路径，value 是组件或者函数
  - 分类
    - 前端路由
      - value 是 component，用于展示页面内容
      - 当浏览器的路径改变时，对应的组件就会显示
    - 后端路由
      - value 是 function，用于处理客户端提交的请求
      - 服务器收到一个请求后，根据请求路径找到匹配的函数来处理请求，返回响应数据

- 单页面应用（SPA，Single Page Web Application）
  - 整个应用只有一个完整页面
  - 点击页面中的导航链接不会刷新页面，只会做页面的局部更新
  - 数据需要通过 ajax 请求获取

> ## HTML + CSS

### HTML5 与 CSS3 新特性

#### HTML5

- 新增语义化标签（页面布局与多媒体）
  - 语义化
    - 语义化标签更具有可读性，便于团队的开发和维护
    - 没有 CSS 的情况下，网页也能很好的呈现出内容结构和代码结构
    - 关于 SEO，搜索引擎更能理解到网页中各部分之间的关系，更准确更快速搜索信息
- 新增 input 类型与属性
- WebStorage 本地储存
- WebSocket
  - 参考网络与 http
- WebWorker 多线程（了解）
- canvas（了解）
- 地理定位（了解）
- ……

#### CSS3

- 高级选择器（属性选择器、伪元素选择器）
- 背景透明度（rgb(0,0,0,0.5)） / 缩放（background-size） / 颜色渐变（gradient）
- 盒子模型（box-sizing）
- 圆角边框（border-radius）
- 图片边框（border-image）
- 盒子倒影（box-reflect）
- 盒子阴影（box-shadow）
- 文字阴影（text-shadow）
- 倾斜（skew）
- 滤镜（filter）
- 计算（calc）
- 转换（transform）
  - translate、rotate、scale
  - 2D、3D
- 过渡（transition）
- 动画（animation）
- 媒体查询
- flex 布局
- ……

### SEO（Search Engine Optimization）

- 搜索引擎优化指在了解搜索引擎自然搜索机制的基础之上，对网站进行内部及外部的调整优化，改进网站在搜索引擎中关键字的自然排名，获得更多的展现量，吸引更多目标客户点击访问网站，从而达到互联网营销及品牌建设的目标
- SEO 优化
  - TDK 三大标签优化
  - Logo 优化
  - 提高网页打开速度
  - 合理的书写内链和外链
  - 标签语义化
  - 图片 alt 属性合理书写
  - a 标签内部的文本（锚文本）合理书写
  - 合理利用搜索引擎重视的标签（title，strong，h1-h3，a，em，img&alt）

### 谈一谈 BFC

#### 块级格式化上下文（Block Formatting Context）

- 一个 BFC 区域包含创建该上下文元素的所有子元素，但是不包括创建了新的 BFC 的子元素内部元素，BFC 是一块独立的渲染区域，可以将 BFC 看成是元素的一种属性，拥有了这种属性的元素就会使它的子元素与世隔绝，不会影响到外部其它元素

#### BFC 区域的创建

- 根元素（html 和 body）
- 浮动元素（float 不为 none）
- 定位元素（绝对定位和固定定位）
- 行内块元素（inline-block）
- 设置 overflow 的元素（hidden、scroll、auto）
- 弹性布局（flex）
- ……

#### BFC 的特性

- 创建一个隔离的空间，不同 BFC 区域之间是相互独立的，互不影响

#### BFC 的应用

- 解决外边距塌陷
- 清除浮动
- ……

### 外边距塌陷

- 两个兄弟关系的块元素垂直间距不是相邻外边距之和，而是取两个值中的较大者，被称为相邻块元素垂直外边距的合并，又称垂直塌陷
  - 方法 1：只给一个盒子添加 margin 值
  - 方法 2：给这两个盒子都加一个父元素，并且将父元素设置成 BFC 区域
- 两个父子关系的块元素，（父元素有上外边距同时）子元素也有上外边距，此时父元素会塌陷较大的外边距值，被称为嵌套块元素垂直外边距的塌陷，又称包含塌陷
  - 方法 1：为父元素定义上边框或上内边距
  - 方法 2：将父元素设置成 BFC 区域，如给父元素添加 overflow: hidden

### 浮动与清除浮动

- 浮动：最初是用来做文字环绕

- float 属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘
    - 浮动元素会脱离标准流（脱标）
    - 浮动元素会一行内显示并且元素顶部对齐
    - 浮动元素会具有行内块元素的特性
    
- 清除浮动
  - 由于浮动元素不再占用原文档流的位置，所以它会对后面的元素排版产生影响
  - 清除浮动后，父级就会根据浮动的子盒子自动检测高度
  
- 方法：闭合浮动策略

    - 额外标签法 / 隔墙法，W3C 推荐（不常用）

        - 在浮动元素末尾添加一个空标签，或其他标签（如 \<br />）
          - 优点：通俗易懂，书写方便
          - 缺点：添加许多无意义的标签，结构化较差
          - 注意：空标签必须是块级元素

    - 父级添加 overflow 属性（将父级设置成 BFC 区域）

        - 可以给父级添加 overflow 属性，将其属性值设置为 hidden、scroll 或 auto
        - 优点：代码简洁
        - 缺点：无法显示溢出部分

    - 父级添加 after 伪元素

        - 额外标签法的升级版

        - ```css
            .clearfix:after { /* 单个冒号考虑低版本浏览器兼容性 */
            	content: "";
            	display: block;
                height: 0;
            	visibility: hidden;
                clear: both;
            }
            .clearfix {
            	/* IE6、7 专有 */
            	*zoom: 1;
            }
            ```

        - 优点：没有增加标签，结构更简单，照顾低版本浏览器

    - 父级添加双伪元素

        - ```css
            .clearfix:before,
            .clearfix:after {
                content: "";
                display: table; /* 转换为块级元素，并且在一行显示 */
            }
            
            .clearfix:after {
                clear: both;
            }
            
            .clearfix {
                *zoom: 1;
            }
            ```


### CSS 如何实现盒子水平垂直居中（不定宽高的元素在其它元素的水平垂直居中）

#### flex 布局

- 给盒子的容器设置

  - ```css
    .container {
        display: flex;
        justify-content: center;
    	align-item: center;
    }
    ```

#### 绝对定位 + 转换

- 盒子设置绝对定位，相对于容器
- 盒子绝对定位边偏移：`left: 50%; top: 50%`
- 盒子设置转换：`transform: translate(50%,50%)`

#### 其它方式

- 盒子设置绝对定位，相对于容器
- 盒子绝对定位边偏移：`left: 0; top: 0; right: 0; bottom: 0`
- 盒子设置：`margin: auto`

### 其他参考精讲 / 面试题

> ## JavaScript

### ECMAScript

#### JS 基础
##### 语句和表达式

- 语句：做特定操作的一段可以独立存在的代码，它并不返回可用的数据
  - 每条语句最终都以分号结尾，但编码时可以省略
- 表达式：常量值 / 变量 / 常量值与变量运算 / 函数调用
  - 总是返回一个可以使用的数据值
  - 它不能独立存在
  - 没有分号

##### JS 数据类型

- 基本数据类型

  - number、string、boolean
  - undefined、null
  - Symbol（ES2015）、Bigint（ES2020）
    - Symbol 表示独一无二的值，主要用来定义对象的唯一属性名
    - Bigint 用于表示 number 类型超过最大值的超大数值，以 n 结尾，不能将 Bigint 与其它类型进行运算，只能与 Bigint 值进行算术运算
- 复杂数据类型（引用类型）
  - Object
  - Array
  - Function
  - 其它内置或自定义类型
  - 本质都是 Object
- 注意
  - number / string / boolean 有对应的包装类型 Number / String / Boolean，可以读取属性或调用方法
  - undefined / null 没有对应的包装类型
  - Symbol / Bigint 对应的包装类型不需要用 new 实例化

##### JS 如何判断数据类型

- 常见 6 种判断方式
  - `===`：全等判断，一般用于 undefined 和 null
  - `typeof`：关键字判断
    - number / string / boolean / undefined / null / symbol / bigint
    - function / object（null，所有非函数对象）

  - `instanceof`：关键字判断
    - `A instanceof B`： 判断 A 或者 A 原型链上的对象是否是 B 类型的实例
    - 可以用于判断某个对象是否是某个特定类型
      - 区别 Object 对象与数组对象

  - `obj.constructor`，特殊方法判断
    - 得到对象的构造函数
    - 得到 number / string / boolean 有对应的包装类型 Number / String / Boolean
    - undefined / null 没有 constructor

  - `Object.prototype.toString.call(obj)`
    - 得到类似字符串 `[object Object]`，`slice` 截取后面的类型即可

  - `Array.isArray()`
    - Array 构造函数的方法，专门判断数组

##### 常用的循环 / 遍历

- `for`
- `while`
- `do while`
- `for in`
- `for of`（结合 `ES6+`）
- `forEach`
- `map`
- ……

##### 常用数组和字符串方法

- 数组

  - | 方法                                                         | 描述                                                         | 说明                                                         | 是否改变原数组 |
    | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------- |
    | push(element0[, element1,...,elementN])                      | 数组添加元素（末尾添加）                                     | 返回该数组新长度                                             | 1              |
    | pop()                                                        | 数组删除最后一个元素（末尾删除）                             | 返回该元素的值                                               | 1              |
    | unshift(element0,[ element1,...,elementN])                   | 数组添加元素（开头添加）                                     | 返回该数组新长度                                             | 1              |
    | shift()                                                      | 数组删除第一个元素（开头删除）                               | 返回该元素的值                                               | 1              |
    | splice(start,deleteCount,item1[,item2,...,itemN])            | 该方法可以删除或替换现有元素或者原地添加新的元素             | ES6+，实例方法，返回由被删除的元素组成的一个数组，可以增删改 | 1              |
    | sort((a,b) => {<br/>    return a-b; // 升序排列<br/>    return b-a; // 降序排列<br/>}) | 数组排序                                                     | 返回排序后的数组，默认 ASSCI 码排序，需要传入参数配置        | 1              |
    | reverse()                                                    | 位置颠倒，翻转数组                                           | 返回翻转后的数组                                             | 1              |
    | slice(begin,end)                                             | 数组截取，由 begin 和 end 决定的原数组的浅拷贝               | ES6+，实例方法，返回截取后的新数组，包括 begin，不包括 end   | 0              |
    | arr1.concat(arr2[,...arrN])                                  | 该方法用于合并两个或多个数组                                 | 返回一个新数组                                               | 0              |
    | [...arr1,...arr2]                                            | 拓展运算符也可实现数组合并                                   | ES6+                                                         | 0              |
    | includes(element)                                            | 用于查找某个数组是否包含给定的值                             | ES6+，实例方法，返回值为布尔值                               | 0              |
    | indexOf(searchElement[,fromIndex])                           | 数组中，指定元素，找到索引（首个）                           | 返回在数组中可以找到给定元素的第一个索引，如果不存在，则返回 -1 | 0              |
    | lastIndexOf(searchElement[,fromIndex])                       | 数组中，指定元素，找到索引（最后一个）                       | 返回在数组中可以找到给定元素的最后一个索引，如果不存在，则返回 -1 | 0              |
    | toString()                                                   | 把数组转换为字符串，逗号分隔每一项                           | 返回一个字符串                                               | 0              |
    | join('分隔符')                                               | 把数组转换为字符串，默认逗号分隔每一项，可自定义分隔符       | 返回一个字符串                                               | 0              |
    | find((element,index) => {})                                  | 该方法返回数组中满足提供的测试函数的第一个元素的值；否则返回 undefined | ES6+，实例方法                                               | 0              |
    | findIndex((element,index) => {})                             | 该方法返回数组中满足提供的测试函数的第一个元素的索引；若没有找到对应元素则返回-1 | ES6+，实例方法                                               | 0              |
    | forEach((element,index,arr) => {})                           | 该方法对数组的每个元素执行一次给定的函数                     | ES6+，实例方法，返回 undefined                               | 0              |
    | map((element,index,arr) => {})                               | 该方法创建一个新数组，这个新数组由原数组中的每个元素都调用一次提供的函数后的返回值组成 | ES6+，实例方法，返回一个新数组，每个元素都是回调函数的返回值 | 0              |
    | filter((element,index,arr) => {})                            | 该方法创建给定数组一部分的浅拷贝，其包含通过所提供函数实现的测试的所有元素 | ES6+，实例方法，返回一个由通过测试的元素组成的新数组，如果没有任何数组元素通过测试，则返回空数组 | 0              |
    | reduce((p,c)=>{}[,initialValue])                             | 该方法对数组中的每个元素按序执行一个由您提供的 reducer 函数，每一次运行 reducer 会将先前元素的计算结果作为参数传入，最后将其结果汇总为单个返回值 | ES6+，实例方法，返回使用“reducer”回调函数遍历整个数组后的结果，即 'p' | 0              |
    | some((element,index,arr) => {})                              | 该方法测试数组中是不是至少有 1 个元素通过了被提供的函数测试；如果找到第一个满足条件的元素，返回 true，终止循环 | ES6+，实例方法，返回布尔值                                   | 0              |
    | every((element,index,arr) => {})                             | 该方法测试一个数组内的所有元素是否都能通过某个指定函数的测试，找到一个不符合条件的元素，返回 false，停止遍历 | ES6+，实例方法，返回布尔值                                   | 0              |
    | flat([depth])                                                | 该方法会按照一个可指定的深度递归遍历数组，并将所有元素与遍历到的子数组中的元素合并为一个新数组返回；参数 depth：指定要提取嵌套数组的结构深度，默认值为 1 | ES6+，实例方法，返回一个包含将数组与子数组中所有元素的新数组 | 0              |
    | Array.from(arg1[,arg2])                                      | 将类数组或可遍历对象转换为真正的数组                         | ES6+，构造函数方法，第一个参数是类数组或可遍历对象；第二个参数是一个方法，作用类似于 map，用来对每个元素进行处理，将处理后的值放入返回的数组 | --             |
    
  - 字符串
  
    - 字符串所有的方法，都不会修改字符串本身（字符串是不可变的），操作完成会返回一个新的字符串
  
    - | 方法                                            | 描述                                                         | 说明                                                         |
      | ----------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | indexOf(searchValue[,fromIndex])                | 通过字符查询索引                                             | 该方法返回调用它的 String 对象中第一次出现的指定值的索引，从 fromIndex 处进行搜索。如果未找到该值，则返回 -1 |
      | lastIndexOf(searchValue[,fromIndex])            | 通过字符查询索引                                             | 该方法返回调用 String 对象的指定值最后一次出现的索引，在一个字符串中的指定位置 fromIndex 处从后向前搜索。如果没找到这个特定值则返回 -1 |
      | chatAt(index)                                   | 通过索引检索字符                                             | 该方法从一个字符串中返回指定的字符                           |
      | chatCodeAt(index)                               | 通过索引检索字符 ASCII 码                                    | 该方法从一个字符串中返回指定的字符的 ASCII 码                |
      | str[index]                                      | 通过索引检索字符                                             | 返回指定位置处字符，实际上通过数组索引                       |
      | str.concat(str2,[,...strN])                     | 该方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回 | 返回一个拼接后的新字符串                                     |
      | slice(beginIndex[,endIndex])                    | 该方法提取某个字符串的一部分，并返回一个新的字符串           | 不包含 endIndex 索引字符                                     |
      | substr(start[,length])                          | 该方法返回一个字符串中从指定位置开始到指定字符数的字符       | 被认作是遗留的函数并且可以的话应该避免使用                   |
      | substring(indexStart[,indexEnd])                | 该方法返回一个字符串在开始索引到结束索引之间的一个子集，或从开始索引直到字符串的末尾的一个子集 | 不包含 indexEnd 索引字符                                     |
      | split(separator[,limit])                        | 该方法使用指定的分隔符字符串将一个字符串分割成子字符串数组   | 以一个指定的分割字串来决定每个拆分的位置；separator 可以是一个字符串或正则表达式；limit 是一个整数，限定返回的分割片段数量 |
      | replace(regexp \| substr,newSubstr \| function) | 参数1可以是一个字符串或者一个正则表达式，参数2可以是一个字符串或者一个每次匹配都要调用的回调函数；如果参数1是字符串，则仅替换第一个匹配项 | ES6+，实例方法，该方法返回一个由替换值替换部分或所有的模式匹配项后的新字符串 |
      | includes(searchString[, position])              | 方法用于判断一个字符串是否包含在另一个字符串中               | ES6+，实例方法，返回值为布尔值                               |
      | startsWith(str)                                 | 表示参数字符串是否在原字符串的头部                           | ES6+，实例方法，返回值为布尔值                               |
      | endsWith(str)                                   | 表示参数字符串是否在原字符串的尾部                           | ES6+，实例方法，返回值为布尔值                               |
      | trim()                                          | 该方法会从一个字符串的**两端**删除空白字符                   | ES6+，实例方法，返回新字符串                                 |
      | repeat(n)                                       | 将原字符串重复 n 次                                          | ES6+，实例方法，返回重复 n 次后的新字符串                    |
      | toUpperCase()                                   | 转大写                                                       | 无                                                           |
      | toLowerCase()                                   | 转小写                                                       | 无                                                           |

#### 作用域相关 

##### 作用域

- 理解：一个变量可以合法使用的范围 / 区域
- 目的：作用域起到了隔离变量的作用，避免了不同作用域下变量名冲突问题
- 分类：全局作用域，函数作用域，块级作用域
  - 注意：ES6+ 中的 let 和 const 定义的变量是具有块级作用域的
  - 如 if...else、while、do...while、for 等具有代码块的语句，在 ES6+ 中，表示块级作用域
- 补充：
  - JS 作用域是词法作用域
    - 也称为静态作用域
    - 作用域是在编写代码时就确定了（词法的嵌套结构），而不是在运行时动态确定的

##### 作用域链

- 理解：多个嵌套的作用域形成的由内向外的结构，用于查找变量
- 本质：包含由内向外的多个变量对象的数组
- 用途：保证对执行环境有权访问的所有变量和函数有序访问
- 补充：
  - 作用域链在内存中是真实存在的结构，是执行代码时动态确定的，而作用域不是

##### 变量提升与函数提升

- 变量提升（var）
  - 变量声明语句会提升到当前作用域的最前面执行
  - 在变量声明语句之前，就可以访问到这个变量（undefined）
- 函数提升（function）
  - 函数声明语句会提升到当前作用域的最前面执行
  - 在函数声明语句之前，就可以执行该函数
- 目的：在执行全局代码和函数前会进行预解析 / 处理
- 注意：
  - const / let / class 声明没有提升
  - var / function 声明才有提升

##### 区分函数声明与函数执行

- 函数声明：先创建函数对象，如果是命名函数，则定义一个变量并指向这个函数对象
- 函数执行：执行函数内部的语句
- 必须先声明函数，再执行函数（函数声明有可能会提升到函数执行之前）

##### JS 执行上下文

- JS 引擎并非一行行解析和执行代码，而是一段段解析和执行代码
- JS 可执行的代码分为 3 种类型
  - 全局代码、函数代码、eval 代码（忽略）
- 执行一段代码前，会进行准备工作，被称为 “执行上下文”
  
  1. 开辟一块内存空间
  
  2. 生成变量对象

  3. 确定作用域链
  
  4. 确定 this 指向
- 每执行一段代码，都会创建相对应的执行上下文；在脚本中可能存在多个执行上下文，因为有太多的执行上下文，JS 创建了一个执行上下文栈（stack），用来管理执行上下文（在非面向对象语言中，被称为函数调用栈）
- 过程
  1. 当 JS 开始解析程序时，最先遇到全局代码，此时向执行上下文栈中压入一个全局执行上下文，全局的一定是在整体运行结束以后才被清空
  2. 当执行一个函数时会创建一个函数的执行上下文，并压入到执行上下文栈中，函数执行完成，会将函数从栈里弹出
- 三个重要属性
  - 变量对象（VO）
    - 变量对象是 ECMAScript 规范术语，在一个执行上下文中，变量对象才被激活，只有激活的变量对象，其各种属性才能被读写
    - 变量对象是与执行上下文相关的数据作用域，储存了在执行上下文中定义的变量和函数声明
    - 全局执行上下文的变量对象其实就是全局对象 window
    - 调用函数，会生成函数的变量对象，函数的变量对象中也是有顺序的
      - 变量对象包括了函数所有的形参和实参
      - 检查所有声明的函数，如果变量对象已经有相同名字的属性，则完全替换
      - 检查所有声明的变量，转为变量对象的属性，如果变量名和已经声明的形参或实参相同，则变量声明不会干扰已经存在的这类属性
  - 作用域链
    - 作用域链的用途：保证对执行环境有权访问的所有变量和函数有序访问
    - 作用域链的前端始终都是当前执行的代码所在环境的变量对象
    - 全局执行环境的变量对象 window 始终都是作用域链中的最后一个对象
    - 标识符解析是沿着作用域链一级一级地搜索标识符的过程，搜索过程始终从作用域链的前端开始，然后逐级向后，直至找到标识符为止（如果找不到标识符，通常会导致错误发生）
  - this
    - 确定 this 指向

##### JS 中的 this 指向

- 一般情况下，函数中的 this 指向取决于函数调用的方式（四种绑定规则）
  - 默认绑定：直接调用函数
    - 非严格模式下，this 指向 window
    - 严格模式下，this 指向 undefined，但是最外层的 this 还是指向 window
  - 隐式绑定：通过对象调用（函数调用时存在上下文对象）
    - this 指向这个上下文对象
    - 注意隐式丢失（看函数调用的位置）：`var fn = o.abc; fn()`
  - 显示绑定：通过改变 this 指向的方法，`call / apply / bind`
    - this 指向相关方法的第一个参数
      - 如果是 null | undefined，则 this 指向 window
      - 如果是基本数据类型，this 指向这个值的包装对象
      - 如果是复杂数据类型，this 指向这个对象
  - 构造函数绑定：通过 new 实例化一个对象
    - this 指向这个实例化对象
- 特殊情况
  - 箭头函数没有自己的 this，沿着作用域链去外部作用域找 this
  - bind(obj) 返回的函数，this 指向 obj
  - 回调函数，它不是我们调用的
    - 定时器 / ajax / promise / 数组遍历相关方法回调
      - this 指向 window
    - DOM 事件监听回调
      - 绑定事件的 DOM 元素
    - React 控制的生命周期回调，事件监听回调
      - this 指向组件对象 / undefined
    - Vue 控制的回调函数（生命周期 / methods / watch / computed）
      - this 指向组件实例
- 改变 this 的指向
  - 情况一：将外部的 this 指定为当前函数中的 this
    - 将外部的 this 保存为其它名称变量，一般使用 _this / self
    - 使用箭头函数（ES6+）：this 是静态的！this 始终指向函数声明时所在作用域下的 this 的值
  - 情况二：将任意对象指定为当前函数中的 this
    - 函数立即调用：call / apply
    - 函数声明后，某个时候调用：bind

##### 闭包（closure）

- what
  - 指有权访问另一个函数作用域中变量的**函数对象**，即使这个函数已经执行完毕
- for
  - 闭包是一种保护私有变量的机制，在函数执行时形成私有的作用域，保护里面的私有变量不受外界干扰
  - 类似一个不销毁的栈环境，也延伸了变量的作用范围
- 如何产生
  - 嵌套的内部函数引用了外部函数的局部变量，当调用外部函数时就会产生闭包
- 具体流程
  - 产生闭包：内部函数对象创建时
  - 使用闭包：执行内部函数时
  - 释放闭包：让内部函数对象成为垃圾对象，断开指向它的所有引用
- 具体应用
  - IIEF（Immediately Invoked Function Expression）：立即执行函数
  - 函数柯里化：通过函数调用继续返回函数的方式（高阶函数），实现多次接收参数最后统一处理的函数编码形式
  - JS 模块编译后的运行代码
  - 节流 / 防抖 / 轮播图 都有用到闭包
- 注意
  - 闭包嵌套不要太深，否则占用空间越大
  - 闭包容易导致内存泄露，因为它会一直保存对外部函数作用域中变量的引用，直到内部函数被销毁


#### 原型相关

##### 原型与原型链

- 原型
  - 每个函数都有一个显示原型属性 prototype
  - 每个实例都有一个隐式原型属性 \__proto__
  - 实例的 \__proto__ 与对应函数的 prototype 都指向原型对象
  - 原型对象上有一个 constructor 属性指向对应的构造函数
- 原型链
  - 目的：实现资源的共享，节省空间
  - 理解：从对象的 \__proto__ 开始，连接所有对象，也称为 “隐式原型链”
  - 作用：在查找对象属性或调用对象方法时，会先在对象自身上查找，找不到就会沿着原型链查找，没有返回 undefined
  - 利用原型链可以实现继承
- 详图
  - ![](/images/原型链2.png)

##### new 操作符的原理

1. 创建一个对象空对象，作为 new 以后的实例化对象
2. 把实例化对象的隐式原型指向构造函数的原型对象
3. 调用构造函数并传参，把构造函数的 this 指向创建的实例化对象，收集构造函数的返回值
4. 根据构造函数调用后的返回值决定 new 的返回值

   - 如果构造函数调用返回一个基本类型数据，则 new 返回的是实例化对象
   
   - 如果构造函数调用返回一个复杂类型数据，则 new 返回的不再是实例化对象，而是这个复杂数据类型
   
##### instanceof

- 判断一个复杂数据类型（对象）的类型
- `A instanceof B`：A 是实例对象，B 是构造函数

##### 继承与继承的实现

- ```javascript
  function Person(name, age) {
    this.name = name;
    this.age = age;
  }
  Person.prototype.introduce = function () {
    console.log(`I am ${this.name},and ${this.age} now`);
  };
  const p = new Person('Chan', 25);
  p.introduce();
  ```

- 构造函数 + 原型链的组合式继承

  - 借用父构造函数：`Person.call(this,name,age)`

  - 子构造函数的原型指向父构造函数的实例：`Student.prototype = new Person()`

  - 子构造函数原型的构造器指回子构造函数：`Student.prototype.constructor = Student`

  - ```javascript
    function Student(name, age, price) {
      // 调用父构造函数
      Person.call(this, name, age);
      this.price = price;
    }
    // 1.将子构造函数的原型对象指向父实例对象
    Student.prototype = new Person();
    // 2.将子原型对象的构造函数修改回来
    Student.prototype.constructor = Student;
    const s = new Student('Tong', 33, 15000);
    s.introduce();
    // 子构造函数原型方法优先于父构造函数原型方法
    Student.prototype.introduce = function () {
      console.log(
        `I am ${this.name},and ${this.age} now,my salary is ${this.price}`
      );
    };
    s.introduce();
    ```

- 基于 ES6 类的继承

  - 子类 extends 父类

  - 子类构造器中调用父类的构造器：`super(name,age)`

  - ```javascript
    class Person2 {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }
      introduce() {
        console.log(`I am ${this.name},and ${this.age} now`);
      }
    }
    class Teacher extends Person2 {
      constructor(name, age, lesson) {
        // 子类构造器中调用父类的构造器
        super(name, age);
        this.lesson = lesson;
      }
      introduce() {
        console.log(
          `I am ${this.name},and ${this.age} now,major in ${this.lesson}`
        );
      }
    }
    const t = new Teacher('Hua', 29, 'front_end');
    t.introduce();
    ```

##### 面向对象的三大特性

- 封装
  - 理解：将可复用的代码用一个结构包装起来，便于反复使用
  - 表现：函数 => 对象 => 模块 => 组件 => 库
  - 特点：不需要外部看到的必须隐藏起来，只向外部暴露想让外部使用的功能或数据

- 继承
  - 目的：复用代码，提高效率
  - 实现：基于 构造函数+原型链 组合式实现继承；基于 ES6 类实现继承

- 多态
  - 理解
    - 声明时指定一个类型对象，并调用其方法
    - 实际使用时可以指定任意子类型对象，运行的方法就是当前子类型对象的方法

  - JS 中的多态
    - 由于 JS 是弱类型语言，在声明时都不用指定类型
    - 在使用时可以指定任意类型的数据


#### 异步编程

##### 同步与异步

- 同步
  - 从上到下按顺序依次执行
  - 只有将上一个任务完全执行完后，才执行下一个任务
  - 代码执行时易发送阻塞
- 异步
  - 启动任务后，立即向下继续执行，等同步代码执行完后，才执行回调函数
  - 异步回调函数执行的条件即使被触发，也是要先放入回调队列（callback queue）（task / event queue），只有当同步任务或前面的异步任务执行完毕后才执行

##### JS 事件轮询机制 / JS 执行机制 / JS 异步编程 / JS 单线程是怎么做到不阻塞

- JS 是通过事件轮询机制来实现单线程异步执行的

- JS 执行代码的先后顺序：先异步（注意是整个 script 是异步的），再执行同步代码（script 内部的代码），再执行异步代码（常见的异步回调）

- 浏览器事件模型的组成：主线程、回调队列、浏览器管理模块

  - 主线程：所有任务（同步 / 异步）都在主线程上执行，形成一个执行栈
  - 回调队列：主线程之外有用于储存待执行异步回调的回调队列
    - 回调队列有两个：宏任务队列和微任务队列
    - 整个 script 标签是异步的，属于宏任务，内部有同步代码与异步代码，script 不进入回调队列
  - 浏览器管理模块（WebAPI 管理模块）
    - 定时器管理模块
    - DOM 管理模块
    - AJAX 管理模块
    - MutationObserver 管理模块
    - ……

- 事件轮询（event loop）的过程

  1. 在执行主线程时，如果遇到了异步代码，则把异步代码的回调函数交给浏览器管理模块来管理
  2. 浏览器的管理模块对事件进行监听，当回调函数已经达到条件需要执行时，会把回调函数依次放入回调队列
  3. 当主线程的同步代码执行完毕，则会轮询回调队列，依次执行回调队列中的回调函数

  - 详图
    - ![](/images/事件轮询详图.png)

- 宏任务与微任务

  - 异步代码有优先级关系，分为宏任务和微任务
  - 宏任务（macrotask）和微任务（microtask）
    - 宏任务是宿主（浏览器）发起的：包括 script、setTimeout、setInterval、事件回调函数、ajax 请求回调函数等
      - 注意：script 是不进入宏任务队列的，是第一个执行的任务
    - 微任务是 JS 发起的：`Promise.then` `Promise.catch` `Promise.finally` `async/await` `MutationObserver` `Object.observe` 等
  - 执行过程
    1. 执行栈选择最先进入队列的宏任务（一般都是 script），执行其同步代码直至结束
    2. 检查是否存在微任务，有则执行至微任务队列为空
    3. 执行宏任务中的异步代码
    4. 执行过程中如果遇到微任务，就将它添加到微任务的任务队列中
    5. 每次执行完一个宏任务，都会检查是否存在微任务，有则执行至微任务队列为空
    6. 从宏任务队列中开始执行下一个宏任务……

##### JS 线程与 GUI 线程（绘制界面）

- JS 线程负责执行 JS 代码，GUI 线程负责渲染页面
- 2 个线程互斥，不会同时执行（了解原因：JS 可以修改 DOM 结构）
- 微任务的运行效率更高，因为微任务是在渲染页面之前执行
  - 页面第一次渲染：`script` 宏任务 => 所有微任务 => 渲染页面
  - 页面更新渲染：第一个宏任务 => 所有微任务 => 渲染页面

##### Promise

- 参考 ES6+

#### 内存管理

##### 内存的生命周期

- 分配所需的内存
  - 变量赋值
  - 创建对象
  - 调用函数
- 使用分配到的内存（读 / 写）
  - 读取当前值
  - 设置新的值
  - 新值覆盖旧值
- 不需要时将其释放
  - 函数执行完毕，为当次函数执行分配的内存自动释放
  - 没有引用指向的对象，会在某个时刻被垃圾回收器回收释放

##### JS 的垃圾回收机制

- 在 JS 中对象的释放（回收）是靠浏览器中的垃圾回收器来处理的
- 垃圾回收器：专门用来释放垃圾对象占用空间的一段程序代码，它单独运行在一个线程上，每隔一定时间就执行
  1. 判断对象是否为垃圾对象（较难）
     - 判断对象是否为垃圾对象
       1. 引用计数法（对象是否被引用）：每个对象内部都标记一下引用它的总个数，如果引用个数为 0 时，即为垃圾对象
       2. 标记清除法（对象是否能获取）：从根对象（也就是 window）开始查找（递归算法）所有引用的对象， 并标记为 “使用中”，没有标记为 ”使用中“ 的对象就是垃圾对象，循环引用的对象也可能是垃圾对象（引用计数法无法判断）
       3. V8 垃圾回收机制：分代回收（了解，参考面试题.pdf）
  2. 回收释放对象占用的内存空间（较易）

##### 内存泄漏与内存溢出

- 内存泄漏：当程序中的某个内存数据不再需要使用，而由于某种原因，没有被释放

  - 意外的局部变量

    - ```javascript
      function fn() {
          // 此处的 a 是全局变量
      	a = new Array(10);
      }
      fn();
      ```

  - 没有及时清除的定时器

    - ```javascript
      const intervalId = setInterval(()=>{},1000);
      // clearInterval(intervalId);
      ```

  - 没有及时解绑的监听

    - ```javascript
      this.$bus.$on('xxx', this.handle);
      // this.$bus.$off('xxx');
      ```

  - 没有及时释放的闭包

- 内存溢出：运行程序需要分配的内存超过了系统能给你分配的最大剩余内存

  - 抛出内存溢出的错误（Out of Memory），程序中断运行

  - 演示代码

    - ```javascript
      const arr = [];
      for (let i = 0; i < 100000000; i++) {
      	arr[i] = new Array(1000);
      }
      ```

- 内存泄漏容易导致内存溢出

#### ES6+

##### 整体列表

> const 和 let
>
> 变量解构赋值

> 数值扩展
>
> 字符串扩展
>
> 数组扩展
>
> 函数扩展
>
> 对象扩展

> 新数据类型
>
> 新容器语法
>
> 类语法
>
> 异步语法
>
> 模块化语法
>
> 代理（Proxy）与反射（Reflect）语法

##### const、let 与 var 的区别

- const 声明常量，let、var 声明变量
- const 和 let 有块级作用域、没有变量提升、不能重复声明、不会添加到 window 对象上

##### 变量解构赋值

- ES6 允许按照一定模式从数组和对象中提取值，对变量进行赋值，即变量的解构赋值
- 解构数组：如 `const [count,setCount] = useState();`
- 解构对象：如 `const {id,name} = this.product;`
- 解构形参：如 `add({id,title}){} add({id,title})`
- 解构引入模块：如 `import {getProductList} from '@/api'`

##### 数值扩展

- 二进制（0b）与八进制（0o）的表示规范
- Number 构造函数的方法
  - Number.EPSILON：JS 中表示最小的精度，属性值接近 2.220446049250313e-16，类比等价无穷小
  - Number.isFinite()：检测一个数值是否为有限数，返回值是布尔值，注：非数值类型返回`false`
  - Number.isNaN()：检测一个数值是否是NaN，返回值是布尔值
  - Number.parseInt()，Number.parseFloat()：字符串转整数，小数
  - Number.isInteger()：判断一个数值是否为整数，返回值是布尔值
- Math 内置对象方法
  - Math.trunc()：抹掉数值中的小数部分，返回抹掉后整数
  - Math.sign()：判断一个数值是正数、负数还是零，返回值是`1|-1|0`

##### 字符串扩展

- 模板字符串：\`我是 ${name}`
  - 内部允许空白字符
  - 变量拼接（解析变量）
  - 调用函数：\`${fn()}`
- 实例方法
  - `startsWith()`：表示参数字符串是否在原字符串的头部，返回值为布尔值
  - `endsWith()`：表示参数字符串是否在原字符串的尾部，返回值为布尔值
  - `repeat(n)`：将原字符串重复 n 次，返回值是重复后的新字符串

##### 数组扩展

- 扩展运算符
  - 数组降维
  - 浅拷贝数组：`const newArr = [...arr]`
  - 合并多个数组：`const newArr = [...arr1,...arr2]`
  - 将伪数组转换为真正数组
    - 将字符串转为数组
- 构造函数方法
  - `Array.from(arg1[,arg2])`：将**类数组或可遍历对象**转换为真正的数组
  - `Array.of(arg1,arg2,arg3)`：将一组值转换为数组
  - ……
- 实例方法
  - includes / find / findIndex / forEach / map / filter / some / every / reduce / splice / slice

##### 函数扩展

- 箭头函数
  - this 是静态的！this 始终指向函数声明时所在作用域下的 this 的值
  - 不能作为构造函数，实例化对象，本质还是 this 是静态的原因
  - 不能用作生成器函数
  - 不能使用 arguments 变量保存实参，使用 rest 参数代替

- 形参默认值
  - 形参初始值，具有默认值的参数，一般位置靠后

- 剩余参数（rest 参数）
  - 用来获取实参：`...args`
  - 如果参数存在多个，并且有 rest 参数，则 rest 参数一定要放到参数末尾
  - 剩余参数也是利用了扩展运算符

##### 对象扩展

- 扩展运算符
  - 浅拷贝对象：`const newObj = {...obj}`
  - 合并多个对象：`const newObj = {...obj1,...obj2}`

- 对象简写形式

  - ES6 允许在大括号内部，直接写入变量和函数，作为对象的属性和方法，更为简洁

- 属性表达式

  - 主要用于属性名是变量，属性名不规则，另外在 symbol 类型作为对象属性名中也常用

  - `obj['getter/add']` / `obj[a]`

- 构造函数方法

  - `Object.is(arg1,arg2)`：判断两个值是否完全相等
    - 注意：NaN 用此方法比较，是相等的（`===` 则不是）

  - `Object.assign(arg1,arg2)`对象的合并
    - 如果存在相同属性，arg2 覆盖 arg1
    - 可以用作对象的浅拷贝

  - `Object.setPrototypeof(arg1,arg2)`：设置原型对象
    - arg2 是 arg1 的原型对象
  - `Object.getPrototypeof(arg)`：返回指定对象的原型
    - arg 是要返回其原型的对象

##### 新数据类型（symbol）

- 表示独一无二的值，是 JS 语言的第七种数据类型，是一种类似于字符串的数据类型
- 特点
  - symbol 的值是唯一的，用来解决命名冲突的问题
  - symbol 值不能与其它数据类型进行运算（包括 symbol 类型）
  - symbol 定义的对象属性不能使用 for...in 循环遍历

- 迭代器（iterator）
  - Symbol 对象提供的属性（Symbol.iterator）
  - 是一种接口，为各种不同的数据结构提供统一的访问机制；任何数据结构只要部署 iterator 接口，就可以完成遍历操作
  - ES6 创造了一个新的遍历命令 for...of 循环，iterator 接口主要供 for...of 消费
  - 常用原生具备 iterator 接口的数据
    - Arguments
    - String
    - Array
    - Set
    - Map
    - ……

##### 新容器语法

- Set
  - 类似数组，但是成员值唯一
  - 集合实现了 iterator 接口，因此可以使用扩展运算符和 for...of
  - 属性和方法
    - size、add()、delete()、has()、clear()

  - 使用场景：历史搜索记录的存储，因为成员不重复

- Map
  - 类似对象，键值对的集合，但是 “键” 的范围不限于字符串或 symbol 类型，各种类型的值（包括对象）都可以当作键
  - 集合实现了 iterator 接口，因此可以使用扩展运算符和 for...of
  - 属性和方法
    - size、get()、set()、delete()、clear()

##### 类语法

- class
- constructor
- static
- extends
- super() / super.xxx()

##### 异步语法

- 生成器
  - 异步编程解决方案，是一种特殊函数，async...await 的语法糖
  - 内部通过 yield 语句分割，生成器函数返回值是生成器对象，符合迭代器协议和可迭代协议，调用依赖于迭代器的 next 方法

- promise
  - 参考末尾附加

- async...await
  - 参考末尾附加

##### 模块化语法（ESM）

- export / export default
  - 默认暴露 / 分别暴露 / 统一暴露

- import / import ... as /import()
  - 静态导入 / 导入起别名
  - 动态导入，拆分打包，主要用于懒加载

##### 代理（Proxy）与反射（Reflect）语法

##### 其它

- 可选链操作符 `?`

#### 其它

##### 节流 / 防抖

- 当一个事件触发很频繁时，会造成资源的浪费，这不是我们所需要的，此时就用到了节流和防抖；但是我们控制不了事件的触发与回调函数的执行，不过我们可以控制核心代码的执行
- 作用：节流和防抖作为页面性能优化的一种策略，可以降低回调函数核心代码的执行频率，节省计算资源，能有效减少浏览器引擎的损耗，防止出现页面堵塞卡顿现象
- 节流

  - 限制一个动作在一段时间内只能执行一次
  - 使用场景

    - 轮播图频繁点击
    - input 框实时搜索并发送请求展示下拉列表，每隔固定时间发送一次请求
    - resize、scroll 事件，每隔固定时间计算一次位置信息
    - DOM 元素的拖拽功能实现（mousemove）
    - 抢购疯狂点击（click）
    - ……
- 防抖

  - 当一个动作连续触发，只执行最后一次
  - 使用场景

    - 登录、发短信等按钮避免用户点击太快，以致于发送了多次请求
    - input 框输入，导致发请求次数过多，也可以用防抖
    - 调整浏览器窗口大小时，resize 次数过于频繁，造成计算过多，此时需要一次到位
    - ……

##### 深浅拷贝

- 浅拷贝：只是拷贝一层，更深层次对象级别的只拷贝引用
  - 常用方式
    - for...in 遍历并赋值
    - `Object.assign(target, ...sources)` 
    - 扩展运算符
- 深拷贝：拷贝多层，每一级别的数据都会拷贝

##### 图片懒加载与预加载

- 懒加载
  - what：也叫延迟加载，指的是在长网页中延迟加载图片的时机，当用户需要访问时，再去加载
  - why：可以提高网站的首屏加载速度，提升用户的体验，并且可以减少服务器的压力
  - how：将页面上图片的 src 属性设置为加载图片（尽量小），将图片的真实路径保存在一个自定义属性中，当页面滚动的时候，进行判断，如果图片进入页面可视区域内，则从自定义属性中取出真实路径赋值给图片的 src 属性，以此来实现图片的延迟加载
- 预加载
  - what：指的是将所需的资源提前请求加载到本地，这样后面在需要用到时就直接从缓存取资源
  - why：通过预加载能够减少用户的等待时间，提高用户的体验；一般预加载过程给用户提供载入界面，尽可能美观
  - how：最常用的方式是使用 js 中的 image 对象，通过为 image 对象来设置 src 属性，来实现图片的预加载

### 手写代码

#### new 和 instanceof

- ```javascript
  // 手写 new
  function myNew(con, ...args) {
    // 创建一个空对象作为实例对象
    const obj = {};
    // 将实例对象的隐式原型指向指定构造函数的显示原型
    obj.__proto__ = con.prototype;
    // 调用指定构造函数，将指定构造函数的 this 指向这个实例对象，并获取返回值
    const res = con.apply(obj, args);
    // 判断指定构造函数的返回值
    // 如果是引用数据类型，将其返回
    if (typeof res === 'object' || typeof res === 'function') {
      return res;
    }
    // 如果是基本数据类型，返回其实例对象 obj
    return obj;
  }
  // 使用 myNew
  function Person(name, age) {
    this.name = name;
    this.age = age;
    // return {};
  }
  console.log(myNew(Person, 'cc', 18));
  console.log(new Person('cc', 18));
  ```

- ```javascript
  // 手写 instanceof
  function myInstanceof(obj, Type) {
    // 获取对象的原型
    let protoObj = obj.__proto__;
    // 循环判断是否在原型链上有相应的类型与 Type 的原型相等
    while (protoObj) {
      // 存在返回 true
      if (protoObj === Type.prototype) return true;
      // 此处没有，继续更新条件，循环判断
      protoObj = protoObj.__proto__;
    }
    // 当达到原型链 null 处，跳出循环返回 false
    return false;
  }
  // 使用 myInstanceof
  console.log(myInstanceof(p, Course));
  console.log(myInstanceof(p, Object));
  console.log(myInstanceof(p, Function));
  ```

#### call、apply 与 bind

- ```javascript
  // 测试函数与对象
  function fn(a, b, c = 100) {
    console.log(this.m, a, b, c);
    return a + b;
  }
  var m = 'window-m';
  const obj = { m: 'obj-m' };
  ```

- ```javascript
  // 1. 重写 call：通过在目标对象上定义一个临时方法，使得 fn 函数在被调用时 this 指向这个目标对象
  Function.prototype.call = function (thisObj, ...args) {
    console.log('rewrite-call');
    // this 是调用者函数 fn
    // console.log(this, ...args);
    // 处理特殊情况
    if (thisObj === undefined || thisObj === null) {
      // 将 thisObj 指向 window
      thisObj = window;
    }
    // thisObj 上创建一个临时方法为 fn
    thisObj.tempFn = this;
    // 调用临时方法，传递参数，接受返回值
    const res = thisObj.tempFn(...args);
    // 删除临时方法
    delete thisObj.tempFn;
    // 返回临时方法返回值
    return res;
  };
  console.log(fn.call(obj, 4, 6));
  ```

- ```javascript
  // 2. 重写 apply：借用 call 即可，但是注意传递的参数是数组形式
  Function.prototype.apply = function (thisObj, args) {
    console.log('rewrite-apply');
    // call 传递的参数是序列
    return this.call(thisObj, ...args);
  };
  console.log(fn.apply(obj, [4, 6]));
  ```

- ```javascript
  // 3. 重写 bind：借用 call，但是注意 bind 的返回值是一个函数
  // bind 的本质：返回一个函数，这个函数内部会调用原函数，并且指定原函数的 this 为 bind 的第一个参数
  // 注意：原函数的实参，优先考虑 bind 的参数，其次考虑新函数调用指定的参数
  Function.prototype.bind = function (thisObj, ...args) {
    console.log('rewrite-bind');
    return (...args2) => {
      return this.call(thisObj, ...args, ...args2);
    };
  };
  console.log(fn.bind(obj, 4, 6)(200));
  ```

#### 节流 / 防抖

- ```html
  <button id="normal">normal</button>
  <button id="throttle">throttle</button>
  <button id="debounce">debounce</button>
  ```

- ```javascript
  // 处理点击事件的回调函数 callback
  function handleClick() {
    console.log('发送请求或更新 DOM', this);
  }
  ```

- ```javascript
  // 节流
  function throttle(callback, time) {
    // 定义上一次时间，初始化 0
    let pre = 0;
    // 返回的是真正的事件函数
    return function (event) {
      console.log('throttle');
      // 获取当前时间
      let current = Date.now();
      // 当前时间 - 上一次时间 > 给定的事件间隔时，才节流
      if (current - pre > time) {
        // 修改 this 指向，使得发生事件的目标元素调用 callback，这样 callback 内部 this 指向目标元素
        callback.call(this, event);
        pre = current;
      }
    };
  }
  ```

- ```javascript
  // 防抖
  function debounce(callback, time) {
    // 声明定时器 id
    let timeoutId = 0;
    // 事件回调函数
    return function (event) {
      // 在启动定时器之前，清除上一次还未处理的定时器
      if (timeoutId) clearTimeout(timeoutId);
      // 启动延迟定时器
      timeoutId = setTimeout(() => {
        callback.call(this, event);
      }, time);
    };
  }
  ```

- ```javascript
  // 获取 DOM 元素，绑定点击事件
  // normal
  document.getElementById('normal').onclick = handleClick;
  // throttle
  document.getElementById('throttle').onclick = throttle(handleClick, 2000);
  // debounce
  document.getElementById('debounce').onclick = debounce(handleClick, 2000);
  ```

#### 深浅拷贝（代码演示 - 深拷贝）

- ```javascript
  // 目标对象
  const obj = {
    a: {
      m: 1,
    },
    b: [3, 4],
    // 函数属性
    fn: function () {},
    d: 'abc',
  };
  // 循环引用
  obj.a.c = obj.b;
  obj.b[2] = obj.a;
  ```

- ```javascript
  // 1. 通过 JSON 与对象相互转换实现深拷贝
  // 使用场景：请求返回的数据对象的拷贝可以用这种方式
  function deepClone1(target) {
    return JSON.parse(JSON.stringify(target));
  }
  console.log(deepClone1(obj));
  // 问题：1. 目标对象不能有函数属性；2. 目标对象内部不能循环引用
  ```

- ```javascript
  // 2. 通过遍历目标对象，递归调用实现深拷贝
  // 解决问题1：目标对象可以存在函数属性
  // 首先定义一个获取类型函数
  function getType(target) {
    return Object.prototype.toString.call(target).slice(8, -1);
  }
  // console.log(getType(obj));
  function deepClone2(target) {
    // 获取目标对象类型
    const type = getType(target);
    // 判断是否再次遍历内部属性
    if (type === 'Object' || type === 'Array') {
      // 创建拷贝对象
      const cloneTarget = type === 'Object' ? {} : [];
      // 遍历目标对象
      for (const key in target) {
        // 防止在原型链上查找，影响性能，常与 for...in 搭配
        if (target.hasOwnProperty(key)) {
          // 递归调用赋值
          cloneTarget[key] = deepClone2(target[key]);
        }
      }
      return cloneTarget;
    } else {
      return target;
    }
  }
  console.log(deepClone2(obj));
  ```

- ```javascript
  // 3. 2方法优化，通过 Map 容器存储目标对象（key）与拷贝对象（value），对拷贝对象进行缓存，每次使用时从 Map 中获取即可
  // 解决问题2：目标对象内部可以循环引用
  function deepClone3(target, map = new Map()) {
    const type = getType(target);
    if (type === 'Object' || type === 'Array') {
      // 从 Map 中获取拷贝对象
      let cloneTarget = map.get(target);
      // 如果存在拷贝对象，返回后直接使用即可
      if (cloneTarget) return cloneTarget;
      // 不存在拷贝对象，创建拷贝对象
      cloneTarget = Array.isArray(target) ? [] : {};
      // 缓存到 Map 中
      map.set(target, cloneTarget);
      // 遍历目标对象
      for (const key in target) {
        if (target.hasOwnProperty(key)) {
          // 递归赋值
          cloneTarget[key] = deepClone3(target[key], map);
        }
      }
      return cloneTarget;
    } else {
      return target;
    }
  }
  console.log(deepClone3(obj));
  ```

- ```javascript
  // 4. 3方法性能优化
  // 数组：while / for / forEach 性能要高于 for...in / Object.keys&forEach
  // 对象：for...in / Object.keys&forEach 性能差不多
  function deepClone4(target, map = new Map()) {
    // 获取目标对象类型
    const type = getType(target);
    if (type === 'Object' || type === 'Array') {
      // 从 Map 中获取拷贝对象
      let cloneTarget = map.get(target);
      // 如果存在拷贝对象，返回
      if (cloneTarget) return cloneTarget;
      // 不存在则创建拷贝对象
      if (type === 'Object') {
        cloneTarget = {};
        // 将拷贝对象放入容器
        map.set(target, cloneTarget);
        // 遍历赋值
        for (const key in target) {
          if (Object.hasOwnProperty.call(target, key)) {
            cloneTarget[key] = deepClone4(target[key], map);
          }
        }
        return cloneTarget;
      } else {
        cloneTarget = [];
        // 将拷贝对象放入容器
        map.set(target, cloneTarget);
        // 遍历赋值
        target.forEach((item, index) => {
          cloneTarget[index] = deepClone4(item, map);
        });
        return cloneTarget;
      }
    } else {
      return target;
    }
  }
  console.log(deepClone4(obj));
  ```

#### 数组去重

- ```javascript
  const arr = [1, 2, 4, 5, 2, 4, 1, 5, 7];
  ```

- ```javascript
  // 1. ES6+ 语法
  // from / ... + Set
  function unique1(arr) {
    // return Array.from(new Set(arr));
    return [...new Set(arr)];
  }
  console.log(unique1(arr));
  ```

- ```javascript
  // 2. 双层遍历
  function unique2(arr) {
    const newArr = [];
    arr.forEach((item) => {
      // 判断新数组中有无重复元素
      if (!newArr.includes(item)) {
        // 没有则向新数组中添加
        newArr.push(item);
      }
    });
    return newArr;
  }
  console.log(unique2(arr));
  ```

- ```javascript
  // 3. 单层遍历 + 对象容器
  // 思路：以空间换时间，空间复杂度上升，时间复杂度下降
  // Vue 的 v-show 和 v-if 中 v-show 也是以空间换时间
  function unique3(arr) {
    const newArr = [];
    const container = {};
    arr.forEach((item) => {
      // 如果对象容器中没有 item 属性则把数组元素放入新数组
      if (!container.hasOwnProperty(item)) {
        // 将 item 放入对象容器
        container[item] = true;
        newArr.push(item);
      }
    });
    return newArr;
  }
  console.log(unique3(arr));
  ```

#### 数组扁平化

- ```javascript
  // 数组扁平化：取出嵌套数组（多维）中的所有元素放到一个新数组（一维）中
  const arr = [1, [2, [3]]];
  ```

- ```javascript
  // 1. 使用 ES6+ 提供的实例方法 flat
  const newArr = arr.flat(2);
  console.log(newArr);
  ```

- ```javascript
  // 2. 递归，使用 reduce concat some 方法
  function flatten(arr) {
    return arr.reduce((p, c) => {
      // 判断 当前元素c 是否是一个数组，并且 c 内部是否存在数组
      if (Array.isArray(c) && c.some((item) => Array.isArray(item))) {
        // 递归调用
        c = flatten(c);
      }
      // 连接起来
      return p.concat(c);
    }, []);
  }
  console.log(flatten([1, [2, [3]]]));
  ```

- ```javascript
  // 3. 使用扩展运算符（推荐）
  function flatten2(arr) {
    while (arr.some((item) => Array.isArray(item))) {
      // 扩展运算符可实现数组降维
      arr = [].concat(...arr);
    }
    return arr;
  }
  console.log(flatten2([1, [2, [3]]]));
  ```

#### 数组简单排序

- ```javascript
  const arr = [1, 5, 4, 2, 9, 7, 8, 0, 6, 3];
  ```

- ```javascript
  // 1. 冒泡排序
  function bubbleSort(arr) {
    // 外层循环的轮数
    for (let i = 0; i < arr.length - 1; i++) {
      // 内层对比的次数
      for (let j = 0; j < arr.length - i - 1; j++) {
        if (arr[j] > arr[j + 1]) {
          let temp = arr[j];
          arr[j] = arr[j + 1];
          arr[j + 1] = temp;
        }
      }
    }
    return arr;
  }
  console.log(bubbleSort(arr));
  ```

- ```javascript
  // 2. 项目中的排序
  // 前台排序：
  const products = [
    { id: 156, price: 50, sales: 100 },
    { id: 157, price: 89, sales: 40 },
    { id: 158, price: 22, sales: 250 },
  ];
  const reSortProducts = products.sort((a, b) => {
    return a.price - b.price;
  });
  console.log(reSortProducts);
  // 后台排序：返回数据本身就是有序，请求时就需要指定条件参数
  ```

#### 字符串处理

- ```javascript
  // 1. 字符串倒序：思路 => 字符串转为数组，数组倒序 reverse，再转为字符串 join
  function reverseString(str) {
    // return str.split('').reverse().join('');
    // return [...str].reverse().join('');
    return Array.from(str).reverse().join('');
  }
  console.log(reverseString('123456789'));
  ```

- ```javascript
  // 2. 判断字符串是否是回文（palindrome）
  function palindrome(str) {
    return str === reverseString(str);
  }
  console.log(palindrome('1234567'));
  console.log(palindrome('1234321'));
  ```

- ```javascript
  // 3. 截取字符串：如果字符串的长度超过了 num，截取前面 num 长度部分，并以 ... 结束
  function truncate(str, num) {
    return str.length > num ? str.slice(0, num) + '...' : str;
  }
  console.log(truncate('123456789', 6));
  ```

#### 千位分隔符

- ```javascript
  const reg = /(\d)(?=(\d{3})+$)/g;
  let num = 1234567890;
  let number = num.toString().replace(reg, '$1,');
  console.log(number);
  ```

### WebAPI

#### BOM：参考精讲 / 面试题

#### DOM：参考精讲 / 面试题

#### DOM 事件

##### DOM 事件流

- 基于 DOM 树形结构，事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 DOM 事件流
- 三个阶段：捕获阶段，当前目标阶段，冒泡阶段
  - 事件捕获：网景最早提出，由 DOM 最顶层节点开始，然后逐级向下传播到到最具体的元素接收的过程
  - 事件冒泡：IE 最早提出，事件开始时由最具体的元素接收，然后逐级向上传播到 DOM 最顶层节点的过程
    - 常用于事件代理 / 委派 / 委托

##### 事件代理（事件委派 | 事件委托）

- 不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点（利用 e.target 属性可以得到触发事件的子节点）
- 作用
  - 减少内存占用（事件监听回调从 n 变为 1）
  - 新增子元素也可以触发父节点的事件
- 使用场景：适用于多个元素发生相同的事件后，处理的工作基本一样

#### 前后台交互与 AJAX

##### 区别 AJAX 请求与一般 HTTP 请求

- AJAX 请求是一种特殊的 HTTP 请求
- 一般请求：浏览器一般会直接显示响应体数据，即刷新 / 跳转页面
- AJAX 请求：浏览器的 AJAX 引擎不会对界面进行任何更新操作，只是将数据保存到特定对象（xhr）上，并调用监视的回调函数（onReadyStateChange 监视回调）

##### AJAX 请求分为简单请求和复杂请求

- 简请求
  - get 和 post 默认都属于简单请求
  - 并且 http 的头部信息中不能超出以下字段
    - `Accept`
    - `Accept-language`
    - `Content-Type` 的值只能是 `application/x-www-form-urlencoded`

- 复杂请求
  - 不属于简单请求的，都被称为复杂请求
  - put 和 delete 都属于复杂请求
  - 只要添加额外请求头的也是属于复杂请求
  - 复杂请求在跨域的情况下，会先发送一个空的 body 的 options 预检请求，查看服务器的权限信息

##### 封装一个简易的 AJAX 异步请求函数

- ```javascript
  // 只有 get 请求，简易形式
  class ajax {
    constructor(url) {
      return new Promise((resolve, reject) => {
        // 创建一个 xhr 对象
        const xhr = new XMLHttpRequest();
        // 建立连接与配置（还未发送）
        xhr.open('get', url, true);
        // 发送请求
        xhr.send();
        // 监听状态值的改变
        xhr.onreadystatechange = function () {
  
          // ajax 引擎得到响应数据后：
          // - 将 xhr 的 readyState 属性指定为 4
          // - 将响应数据保存在 response / responseText 属性上
          // - 调用此回调函数
  
          // 当状态值为 4 时，请求已完成
          if (xhr.readyState === 4) {
            // 判断响应状态码，200 - 300 表示成功
            if (xhr.status > 200 && xhr.status < 300) {
              // 指定 promise 成功及结果值
              resolve(JSON.parse(xhr.responseText));
            } else {
              // 指定 promise 失败及结果值
              reject(new Error('request error status: ' + xhr.status));
            }
          }
        };
      });
    }
  }
  ```

##### 封装一个通用的 AJAX 异步请求函数（get / post）

```javascript
// 封装一个 ajax 类
class ajax {
  constructor(options) {
    return new Promise((resolve) => {
      // 解构传入的配置项，默认值
      let {
        url = '',
        method = 'get',
        data = {},
        dataType = 'json',
        success = function () {},
      } = options;
      // 处理 data 数据成 query string
      let str = this.$o2s(data);
      // 判断请求方式
      if (method === 'get') {
        // get 请求则 query string 拼接到 url 后面
        url = url + '?' + str;
      }
      // 创建 xhr 对象
      let xhr = new XMLHttpRequest();
      // 建立请求连接与配置
      xhr.open(method, url);
      // 判断请求方式
      if (method == 'get') {
        // 发送请求
        xhr.send();
      } else {
        // post 请求需要设置请求头
        xhr.setRequestHeader(
          'Content-Type',
          'application/x-www-form-urlencoded'
        );
        // 发送请求
        xhr.send(str);
      }
      xhr.onload = function () {
        if (xhr.status >= 200 && xhr.status < 300) {
          if (dataType == 'text') {
            // 处理返回的数据
            // 回调函数方式
            success(xhr.responseText);
            // promise 方式
            resolve(xhr.responseText);
          } else {
            // 回调函数方式
            success(JSON.parse(xhr.responseText));
            // promise 方式
            resolve(JSON.parse(xhr.responseText));
          }
        }
      };
    });
  }
  // 将对象转换成 query string
  $o2s(obj) {
    let keys = Object.keys(obj);
    let values = Object.values(obj);
    let arr = keys.map((key, k) => {
      return `${key}=${values[k]}`;
    });
    return arr.join('&');
  }
}
```

##### axios 封装 AJAX 请求

- axios 封装 AJAX 原理与使用：参考末尾附加
- axios 二次封装 AJAX 请求
  - 创建 axios 实例时传入配置
    - 通用基础路径和超时时间
  - 请求拦截器中配置
    - 显示进度条
    - 用户临时 ID（userTempId）的请求头（根据业务需求）
    - token
      - 有 token 携带 token 请求头（也有用 authorization 字段）
  - 响应拦截器中配置
    - 关闭进度条
    - 响应成功的结果数据 `response => response.data`
    - 统一处理请求失败（具体请求也可以选择处理或不处理）

> ## 网络基础 / 浏览器

### 网络与 http

#### CDN

- Content Delivery Network，即内容分发网络
- CDN 是构建在现有网络基础之上的智能虚拟网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率
- CDN 的关键技术主要有内容存储和分发技术

#### 区别 http 与 https

- http 协议的问题
  - http 通信使用明文，内容可能被窃听，不适合传输一些敏感信息，比如：信用卡号、密码等支付信息
  - http 不验证通信方的身份就可能遭遇伪装
  - http 无法确认报文的完整性，可能已经遭遇篡改
- https 是 http + 加密 + 认证 +完整性保护
  - https 通过和 SSL 和 TLS 组合使用进行加密 http 的内容，防止被窃听
  - https 中的 SSL 可以确认通信方，提供了一种证书，用于确认通信方
  - https 中的 SSL 可以提供完整性的保护

#### 响应状态码

- HTTP 响应状态码（status）指示特定 HTTP 请求的状态，响应分为五类
- `1xx`：请求已经被服务端接收，继续处理中
  - `100`：请求正常，可以继续请求
  - `101`：需要切换协议
- `2xx`：请求已经被服务器接收，并且处理完成
  - `200`：请求成功
  - `201`：请求处理成功，并创建了新资源，常见 POST 请求
- `3xx`：需要后续操作才能完成请求
  - `301`：永久重定向
  - `302`：临时重定向，让浏览器重定向到 location 响应头所指定的地址
  - `304`：读取缓存
- `4xx`：客户端错误（服务器无法执行）
  - `400`：请求中出现语法错误
  - `401`：需要重新认证，身份校验失败，一般是 token 过期或非法
  - `403`：拒绝访问
  - `404`：请求资源不存在
- `5xx`：服务端错误
  - `500`：服务器执行时出现错误
  - `503`：服务器因各种原因停止运行，无法处理请求

#### 常见的请求方式

- get（查）：主要向服务端查询数据使用，请求报文体没有内容，数据写在请求的 url 地址上
- post（增）：主要向服务端新增一些资源
- put（改）：主要是修改服务端的一些资源，也可以上传文件
- delete（删）：请求删除服务端的某些资源
- options：预检请求，查看服务端是否支持某些请求

#### 请求中 get 和 post 的区别

- 功能
  - get 常用于获取数据
  - post 常用于提交数据

- 读取缓存与否
  - get 默认读取缓存
    - 为了防止读取缓存，原生 ajax 请求中，会在查询字符串上添加一个时间戳

  - post 不会读取缓存

- 发送的数据类型
  - get 只能发送 ASCII 字符（query string）
  - post 能发送更多的数据类型

- 发送数据的位置
  - get 发送的数据在 url 地址上，get 有 url 长度限制
  - post 发送的数据在报文体中，发送的数据更大

#### Restless API 和 Restful API

- Restless API
  - 传统的 API，把每个 URL 当作一个功能操作，如 `/deleteUser`
  - 同一个 URL，后台只进行 CRUD（增删改查）的某一种操作
  - 请求方式不决定请求的 CRUD 操作
  - 一般只有 get / post
- Restful API
  - 新式的 API，把每个 URL 当作一个唯一资源，如 `/user`
  - 同一个 URL，可以通过不同类型的请求对后台资源数据进行 CRUD 四种操作
  - 由请求方式决定请求在后台进行 CRUD 的哪种操作
  - 请求方式
    - get：查询
    - post：添加
    - put：更新
    - delete：删除

#### WebSocket

- 是一种在单个 TCP 连接上进行全双工通信的协议。它使得客户端和服务器之间的数据交换变得更加实时、高效、可靠
- 与传统 HTTP 相比的优势
  - 支持实时数据传输，不需要等待 HTTP 请求和响应
  - 通过单个 TCP 连接进行全双工通信，减少了网络延迟
  - 原生支持跨域通信
- WebSocket 协议的使用需要客户端和服务器都支持
  - 客户端可以使用浏览器原生的 WebSocket API 进行开发
  - 服务器可以使用诸如 Node.js、Python、Java 等语言的库进行开发
- 在 WebSocket 连接建立后，客户端和服务器都可以向对方发送数据
  - 数据可以是文本、二进制数据等形式
  - 服务器可以随时向客户端发送数据，而客户端也可以随时向服务器发送数据
  - 这种实时的双向通信使得 WebSocket 在实时通信、在线游戏、股票行情等领域有着广泛的应用

### 浏览器相关

#### 从 URL 输入到渲染的过程

1. DNS 解析

   - 把域名解析成 IP 地址去访问

   - 浏览器缓存、计算机缓存、路由器缓存、运营商缓存

2. 建立连接：TCP 三次握手
3. 客户端发送请求，把请求报文发送给服务端
4. 客户端接收响应，把响应报文发送给客户端
5. 渲染页面
6. 断开连接：TCP 四次挥手

#### TCP 三次握手

- why：
  - TCP 协议，在发送数据前，通信双方必须在彼此间建立一条连接
  - 确保通信双方都能确定对方的接收和发送能力都正常

- what：三次握手就是在建立连接时发送的 3 次数据包
- how：
  1. 客户端向服务端发送一个 syn 字段（请求）数据包，请求连接
  2. 服务端接收到客户端的 syn 数据包（服务端确认客户端发送能力正常），服务端向客户端发送 syn + ack 字段（应答）数据包
  3. 客户端接收服务端的数据包（客户端确认服务端接收和发送能力都正常），客户端向服务端发送 ack 数据包
  4. 服务端接收 ack 数据包（服务端确认客户端接收能力正常） 

#### TCP 四次挥手

- what：TCP 连接拆除需要发送 4 个数据包，即四次挥手
- why：TCP 是双向的，所以需要在两个方向分别关闭，每个方向的关闭又需要请求和确认，所以一共需要发送 4 个数据包（在客户端请求断开时，服务端只能应答，并等到所有数据处理完毕，会再次发送断开请求）
- how：
  1. 客户端发送 fin（释放连接）字段请求断开连接
  2. 服务端发送 ack 字段（应答）断开连接
  3. 服务端等数据全部处理完毕，发送 fin 字段请求断开连接
  4. 客户端发送 ack 字段（应答）断开请求
- 补充为什么握手三次，挥手四次
  - 服务端数据处理可能还没有完成

#### 浏览器渲染页面的过程（客户端渲染）

1. 构建 DOM 树：解析 HTML 结构为浏览器可以识别的 DOM 树结构
2. 构建样式树（CSSOM 树）：解析 CSS 样式生成 CSSOM 树
3. 更新 DOM 树和 CSSOM 树：解析 JS
3. 构建渲染树（Render Tree）：合并 DOM 树和样式树
3. 布局（重排 / 回流）：计算各个节点显示的位置和样式
4. 分层：页面有很多复杂的效果，为了实现效果会进行分层绘制（例如，存在滚动条、3D、半透明等，都需要分层）
5. 生成图层绘制指令
6. 栅格化：不是一次性直接绘制图层，而是分多个图块
7. 合成与显示：把图块放在渲染线程上开始绘制，并显示在浏览器中

#### 重排与重绘

- 重排（回流）
  - 当渲染树（ Render Tree）中的一部分或全部，因元素的尺寸、布局、隐藏等改变引起页面的重新渲染，该过程被称为重排；完成重排后，浏览器会重新绘制受影响的部分，该过程被称为重绘
  - 引起重排
    - 更新 DOM 或 Style，可能会导致局部重排
    - 具体
      - 浏览器窗口尺寸改变
      - 元素位置和尺寸发生改变的时候
      - 新增和删除可见元素
      - 内容发生改变（文字数量或图片大小等）
      - 元素字体大小改变
      - 激活 CSS 伪类，如 `:hover`
      - 设置 style 属性
      - 查询某些属性
        - offsetTop、offsetLeft、offsetWidth、offsetHeight
        - scrollTop、scrollLeft、scrollWidth、scrollHeight
        - clientTop、clientLeft、clientWidth、clientHeight
- 重绘
  - 当渲染树（Render Tree）中更新的属性只会影响元素的外观、风格、不会影响元素的布局时，浏览器需要重新绘制当前元素的样式，该过程被称为重绘
  - 引起重绘
    - 更新 DOM 或 Style，可能会导致局部重绘
    - 具体
      - 更新元素的部分属性（影响元素外观、风格），如 visibility、outline、背景色等
- 注意
  - 重绘不会引起重排，但重排一定会引起重绘
  - 重排比重绘开销大，更消耗性能
- 减少重排次数
  - 更新节点样式，尽量通过类名，而不是通过 style 更新
  - 分离样式的读写功能，不要将读写操作混合调用
  - 将 DOM 操作离线处理，如 `DocumentFragment`

#### 浏览器缓存机制

-  缓存可以重用已获取的资源能够有效的提升网站与应用的性能
- 缓存分为强制缓存和协商缓存
- 强制缓存
  - 强制浏览器使用当前缓存（期间不发送请求）
  - 过程
    - 客户端请求时，需要携带 Cache-Control 请求头字段，值是 max-age = xxx（秒数）
    - 服务端响应时，也需要携带 Cache-Control 响应头字段，值是 max-age = xxx（秒数）
    - 当下次再次请求时，判断是否符合强制缓存条件，如果符合，则直接读取缓存；如果不符合，则会走协商缓存
-  协商缓存
  -  协商缓存就是强制缓存失效后，浏览器携带缓存标识向服务器发起请求，由服务器根据缓存标识决定是否使用缓存的过程

  -  客户端初次向服务端发起请求
    - 服务器通过响应头方式，返回 Etag（文件的唯一标识)）和 Last-modified（文件的最后一次修改时间）字段
    - 客户端收到 Etag 和 Last-modified 之后收集起来

  -  客户端第二次向服务器发送请求
    - 携带缓存字段，把 Etag 改名为 If-None-Match，把 Last-modified 改名为 If-Modified-Since，通过请求头的方式传递给服务端
    - 服务器先检查自己最新的 Etag 是否等于客户端传递过来的 If-None-Match，如果相等；则再次判断自己最新的 Last-modified 和客户端传递过来的 If-Modified-Since 是否相等
      - 如果以上两个比较都相等，则直接响应 304 状态码，要求客户端读取缓存
      - 如果以上两个比较有一个不相等，则服务端返回最新的数据和最新的 Etag 和 Last-modified

#### 浏览器同源策略（Same-Origin Policy）

- 最早由 Netscape 公司提出，是浏览器的一种安全策略
- 同源：协议、域名（主机名）、端口号 必须完全相同
- 目的：限制某些跨域请求
- 是否遵循同源策略
  - AJAX 请求，默认遵循同源策略
  - `image / link / script` 标签不受同源策略限制

#### 跨域与解决方案

- 跨域
  - 违背同源策略就是跨域，跨域只在服务器响应数据时出现差异（即服务器能够接收跨域请求）
- 解决方案
  - CORS
    - 即 Cross Origin Resouce Sharing，跨域资源共享，官方的跨域解决方案
    - 特点
      - 不需要在客户端做任何特殊操作
      - 完全在服务器中进行处理
      - 跨域资源共享标准新增了一组 http 首部字段（响应头），允许服务器声明哪些源站可以通过浏览器有权限访问哪些资源
        - `Access-Control-Allow-Origin`：允许任意跨域请求
        - `Access-Control-Allow-Headers`：允许客户端可以设置请求头
        - `Access-Control-Allow-Methods`：允许各种请求方式进行任意跨域请求
        - ……

    - 注意：会有数据安全的问题，所以一般只给自家网站配置
  - JSONP
    - 即 JSON with padding，非官方解决方案
    - 原理
      - JSONP 是利用 script 标签的跨域能力来发送请求的
      - script 标签请求
        - 客户端在 url 后拼接一个回调函数
        - 服务端返回结果形式是函数调用，函数的实参则是返回给客户端的结果数据
          - 服务端返回的结果形式是 JS 代码
  
    - 注意：需要前后端配合使用，而且只支持 get 请求，目前已不常用
  - 配置代理服务器
    - 原理：代理服务器端口号与客户端一致，客户端请求代理服务器即可，代理服务器再与跨域服务器交互
    - 前端配置代理：webpack 脚手架中开发服务器（webpack-dev-server）可以配置代理，利用 webpack-dev-server 中的 http-proxy-middleware 进行正向代理
    - 代理服务器
      - 代理服务器
        - 正向代理：代理的是客户端（客户端与代理服务器在一起）
          - 客户端和服务器之间的代理服务器，目的是客户端向目标服务器发送和接收数据
          - 客户端向代理服务器发送请求，并给代理服务器指定目标服务器的地址，代理服务器就会向目标服务器发送请求，得到响应并给客户端
          - 代理服务器代理的是客户端，主要是帮助客户端发送和接受数据（客户端和服务端相互之间不可见）
          - 场景
            - 在开发环境下，前端配置的都是正向代理（如在 webpack devServer 中配置）
            - 科学上网
        - 反向代理：代理的是服务器（服务端与代理服务器在一起）
          - 客户端和服务器之间的代理服务器，目的是代理服务器接收客户端请求，然后转发给服务器，并把得到的结果响应给客户端
          - 场景
            - 在项目上线时（生产配置中），配置的是反向代理，反向代理是在服务端配置的（如 nginx 服务器做反向代理，前端代码也是运行在 nginx 上），不需要客户端做任何操作
            - 百度用来做负载均衡的 nginx

### 前台存储数据

#### Cookie、sessionStorage、localStorage

- | 特性             | 会话cookie                                                   | 持久化cookie             | localStorage                       | sessionStorage                               |
  | ---------------- | ------------------------------------------------------------ | ------------------------ | ---------------------------------- | -------------------------------------------- |
  | 数据的声明周期   | 仅在当前会话有效，关闭页面或者浏览器后被清除                 | 除非被清除，否则永久保存 | 除非被清除，否则永久保存           | 仅在当前会话有效，关闭页面或者浏览器后被清除 |
  | 存放数据大小     | 4KB（小）                                                    | 同左                     | 一般5MB（大）                      | 同左                                         |
  | 请求是否自动携带 | 是                                                           | 是                       | 否                                 | 否                                           |
  | 与服务器通信     | 每次都会携带在HTTP头中，如果使用Cookie 保存过多数据会带来性能问题 | 同左                     | 仅在客户端保存，不参与和服务器通信 | 同左                                         |
  | 用途             | 一般由服务器端生成，用于标识用户身份                         | 同左                     | 用于浏览器端缓存数据               | 同左                                         |
  | 原生API易用性    | 差                                                           | 差                       | 好                                 | 好                                           |

#### 区别 cookie 和 session

- cookie 保存在浏览器端（前台可操作）
- session 保存在服务器端（前台不可操作）
- session 依赖 cookie
  - session 的 id 以 cookie 的形式保存在浏览器端
  - 后台将保存 session 的 id 的 cookie 指定为持久化 cookie

- 补充问题：如何实现关闭浏览再打开访问，还是同一个会话
  - 得到之前的 session 对象

#### WebSql 和 IndexDB（了解）

- 浏览器端的数据库，只有较新的浏览器支持
- WebSql：关系型数据库，通过 sql 语句进行数据的 CRUD 操作
- IndexDB：非关系型数据库，类似于 Mongodb

#### 免密登录流程（自动登录、token 校验）

- token 是什么
  - token 是服务端生成的一串字符串，以作为客户端进行请求的一个令牌，当第一次登录后，服务器生成一个 token 便将此 token 返回给客户端，以后客户端只需带上这个 token 前来请求数据即可，无需再次带上用户名和密码
  - 能够减轻服务器的压力，避免频繁查询数据库，使服务器更加健壮

- 一般来说 token 都是和用户信息在一起的，就算有 token，我们也要拿到用户信息，希望有 token 的情况下，也有用户信息；并且用户信息没有持久化存储，请求用户信息的同时也能检测 token 的可用性
- 需要在路由的全局前置守卫中进行 token 校验（**前端鉴权**）
  - 首先判断 token 是否存在
    - 如果存在
      - 判断当前去的路由导航是不是登录页
        - 如果是登录页，则直接导航到首页
        - 如果不是登录页，判断是否有用户信息
          - 如果有用户信息则直接放行
          - 如果没有用户信息，则请求用户信息，然后再放行
            - 如果请求用户信息失败，说明 token 过期了或者被篡改了，清空本地存储的 token，重新导航到登录页登录
    - 如果不存在
      - 判断要去的路由导航是否是白名单地址：如果是则直接放行，如果不是则直接去登录页登录
- 请求头携带 token 后端进行校验标识是否在登录状态（**后端鉴权**）


> ## 前端工程化

### webpack

- 本质上，webpack 是一个现代 JavaScript 应用程序的**静态模块打包器**（module bundler），当 webpack 处理应用程序时，它会**递归**地构建一个**依赖关系图**（dependency graph），其中包含应用程序需要的每个模块，然后将所有这些模块打包成**一个或多个 bundle**

- 构建打包工具（先构建再打包）
  - 构建：把浏览器不认识的文件（如 .vue、.less 等）转换为浏览器认识的文件（如 .html、.css、.js、.json），各种 loader 就是处理构建的工具
  - 打包：把多个文件打包成一个文件
- 功能
  - 转 ESM 语法（构建）
  - 转 CommonJS 语法（打包）
  - 自动压缩代码

- 最基础的五个部分
  - Entry：入口起点（entry point）。打包时第一个被访问的源码文件，指示 webpack 应该使用哪个模块来作为构建其内部依赖图的开始
  - Output：出口重点（output point）。打包后输出的文件名称
  - Loader：加载器。loader 让 webpack 能够去处理那些非 JavaScript 文件（常见 loader：eslint-loader、less-loader、css-loader）
  - Plugins：插件。实现 loader 之外的更加复杂的其它功能（打包优化和压缩等）
  - Mode：模式。生产模式 production；开发模式 development

### create-react-app

- 安装 create-react-app
  - `npm install -g create-react-app`
- 创建 react 应用程序
  - `create-react-app my-app`
- 进入 my-app 目录，启动应用程序
  - `cd my-app`
  - `npm start`
- 构建与打包
  - `npm run build`
  - 这将在 my-app/build 目录中生成一个优化过的、可部署的版本的应用程序

### vue-cli

- 安装 vue-cli
  - `npm install -g @vue/cli`
- 创建 vue2 应用程序
  - `vue create my-app`

- 进入 my-app 目录，启动应用程序
  - `cd my-app`
  - `npm run serve`

- 构建与打包
  - `npm run build`
  - 这将在 my-app/dist 目录中生成一个优化过的、可部署的版本的应用程序

### vite

- 安装 vite
  - `npm create vite@latest`
- 按提示创建 vue 应用程序
- 进入 my-app 目录，安装依赖，启动应用程序
  - `npm i`
  - `npm run dev`
- 构建与打包
  - `npm run build`
  - 这将在 my-app/dist 目录中生成一个优化过的、可部署的版本的应用程序


> ## NodeJS

### Node.js

- Node.js 是一个基于 Chrome V8 引擎的 JS 运行环境，包含一些内置 API

### 三大基本模块

#### fs 文件系统模块

- fs 模块是 Node.js 官方提供的，用来操作文件的模块。它提供了一系列的属性和方法，用来满足用户对文件的操作需求

- ```javascript
  // 引入 fs 模块
  const fs = require('fs');
  // 读取文件
  fs.readFile('./file/11.txt', function (err, result) {
    if (err) {
      return console.log(`文件读取错误，错误是${err.message}`);
    } else {
      console.log(`文件读取成功，结果是${result}`);
    }
  });
  // 写入文件
  fs.writeFile('./file/1.txt', 'abcd', function (err) {
    if (err) {
      console.log(`文件写入失败，失败原因是${err.message}`);
    } else {
      console.log('文件写入成功');
    }
  });
  ```

#### path 路径模块

- path 模块是 Node.js 官方提供的、用来处理路径的模块。它提供了一系列的属性和方法，用来满足用户对路径的处理需求
- 引入模块
  - `const path = require('path');`
- 路径拼接
  - `path.join([...paths])`
  - `path.resolve([...paths])`
- 获取路径中文件名
  - `path.basename(path[,ext])`
- 获取路径中文件扩展名
  - `path.extname(path)`

#### http 模块

- http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块，从而对外提供 web 资源服务

- 创建最基本的 web 服务器

  - ```javascript
    // 1. 导入 http 模块
    const http = require('http');
    
    // 2. 创建 web 服务器实例
    const server = http.createServer();
    
    // 3. 为服务器实例绑定 request 事件，监听客户端请求
    server.on('request', (req, res) => {
      console.log('Someone is visiting our web server');
    });
    
    // 4. 启动服务器
    server.listen(8080, () => {
      console.log('server is running at http://127.0.0.1:8080');
    });
    ```

  - req 请求对象

    - 服务器接收到客户端的请求，就会调用通过 `server.on()` 为服务器绑定的 request 事件处理函数；如果想在回调函数中，访问与客户端相关的数据和属性，则需要 req 请求对象

  - res 响应对象

    - 服务器接收到客户端的请求，就会调用通过 `server.on()` 为服务器绑定的 request 事件处理函数；如果想在回调函数中，访问与服务器相关的数据和属性，则需要 res 请求对象

> ## Vue2

### 常用 API

#### 全局配置

> Vue.config
>
> > Vue.config.productionTip = false

#### 全局 API

> Vue.component()
>
> Vue.use()
>
> Vue.directive()
>
> Vue.filter()
>
> Vue.nextTick()
>
> Vue.set()
>
> Vue.delete()

#### 配置选项

> 数据
>
> > data
> >
> > props
> >
> > computed
> >
> > methods
> >
> > watch

> DOM
>
> > el
> >
> > template
> >
> > render

> 生命周期
>
> > beforeCreate
> >
> > created
> >
> > beforeMount
> >
> > mounted
> >
> > beforeUpdate
> >
> > updated
> >
> > beforeDestroy
> >
> > destroyed
>
> > activated
> >
> > deactivated
>
> > errorCaptured

> 资源
>
> > components
> >
> > directives
> >
> > filters

> 杂项
>
> > mixins
> >
> > provide / inject

> 其它
>
> > name
> >
> > functional

#### 实例属性

> $el
>
> $refs
>
> $parent
>
> $children
>
> $attrs
>
> $listeners

#### 实例方法

> 数据
>
> > $watch()
> >
> > $nextTick()
> >
> > $set()
> >
> > $delete()

> 事件
>
> > $on()
> >
> > $once()
> >
> > $off()
> >
> > $emit()

> 生命周期
>
> > $mount()
> >
> > $nextTick()
> >
> > $destroy()

#### 指令

> v-text
>
> v-html
>
> v-show
>
> v-if
>
> v-else-if
>
> v-else
>
> v-for
>
> v-on
>
> v-once
>
> v-bind
>
> v-model
>
> v-slot
>
> v-cloak
>
> v-pre

#### 特殊属性

> key
>
> ref
>
> is

#### 内置组件

> component
>
> transition
>
> keep-alive
>
> slot

### API 常见问题

#### 为什么 data 配置项要写成函数

- 当一个组件被定义时，data 配置项必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例
- 如果 data 配置项是一个纯粹的对象，则所有实例将共享引用同一个数据对象
- 通过提供 data 函数，每次创建一个新实例后，能够调用 data 函数，从而返回初始数据对象的一个全新副本

#### 计算属性 computed 和侦听属性 watch 的对比

- watch 和 computed 都可以实现侦听功能；watch 直接侦听某个值，computed 是侦听内部计算需要的属性
- computed 优势在于基于响应式的数据进行缓存，初次计算好的结果会缓存起来，如果响应式依赖没有发生变化，则每次读取这个计算属性的值都会直接去拿缓存；而且计算属性和普通的 data 中数据是一样的也是直接放在 vm 身上，可以直接使用
- computed 能完成的 watch 都可以完成；但是 watch 完成的，computed 不一定可以完成，如监听之后，执行异步请求数据
- watch 擅长处理的场景：一个数据影响多个数据，侧重在监视，监视后想要做什么根据逻辑决定
- computed 擅长处理的场景：受一个或多个数据影响最后得到一个数据，重点是计算并得到一个数据

#### Vue.use() 做了什么

- `Vue.use()` 是用来安装插件的，该方法需要在调用 `new Vue()` 之前被调用
  - 对象插件：调用插件对象 install 方法（传入 Vue）来安装插件
  - 函数插件：直接将其作为 install 来调用（传入Vue）来安装插件

#### vue 的混入（mixin）技术

- 用来复用多个组件中相关的 JS 代码的技术
  - 将多个组件相同的 JS 代码提取出来，定义在一个 mixin 配置对象中
  - 在多个组件中通过 mixins 配置引入 mixin 中的代码，会自动合并到当前组件的配置中

#### $set 和 $nextTick 的使用场景

- $set：向响应式对象中添加一个 property，并确保这个新 property 同样是响应式的，且触发视图更新
- $nextTick：在下次 DOM 更新循环结束之后执行延迟回调
  - 使用场景：更新数据后，想操作更新后的 DOM
  - 深入分析：参考原理部分
- 场景一
  - 项目功能：点击列表项，动态显示输入框，并自动获取焦点（查看模式 => 编辑模式）
  - 编码实现
    - 动态给列表项对象添加 edit 属性（布尔值），用来标识显示输入框
    - 通过 ref 获取当前 input 对象，调用 `focus()`，自动获取焦点
  - 常见问题
    - 响应式数据对象直接添加属性不是响应式的，输入框不会显示
      - 原因：参考**数据监测**
      - 解决：使用 $set 添加 edit 属性
    - 得不到 input，调用 `focus()` 会报错
      - 原因：页面更新是异步的，此时还没有更新页面，还没有 input
      - 解决：使用 $nextTick 指定在 DOM 更新后才去执行回调，在回调中获取 input
- 场景二
  - 项目功能：使用 swiper 实现动态轮播
    - 参考项目，理解表述

#### v-model / vue 双向数据绑定

- 说明
  - 替代表单上的 value 属性，可以对表单的值进行双向数据绑定
  - 如果数据修改，表单的值就会发生改变；如果表单的值发生改变，数据也会随着改变
  - 一般用来收集表单数据
- 收集表单数据
  - 收集单选框数据：使用字符串收集
  - 收集复选框数据
    - 独立使用复选框：使用布尔值收集
    - 多个使用复选框：使用数组收集
  - 收集下拉列表
    - 单选：使用字符串收集
    - 多选：使用数组收集
  - 收集 text 文本和 textarea 等都是使用字符串收集
- 本质
  - 使用 `v-bind: value` 给表单强制单向绑定一个值
  - 使用 input 事件监听表单内容的改动，在事件中通过 `$event.target.value` 获取表单新输入的值，给 data 中的数据赋值

#### v-if 和 v-show 的区别

- v-if 是真正的条件渲染，因为它会确保在切换过程中元素或者子组件适当地被销毁和重建
  - v-if 是惰性的，如果在初始渲染时条件为假，则什么也不做；直到条件第一次变为真时，才会开始渲染条件块
- v-show 则不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换
- 一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销
  - 如果需要非常频繁地切换，则使用 v-show 较好（以空间换时间）
  - 如果在运行时条件很少改变，则使用 v-if 较好
- 补充：使用 v-if 解决模板中初始解析 undefined 的 bug，如 {{a.b.c}}，a 初始值是一个空对象

### 设计模式与原理

#### MVC 模式

- MVC 是一种软件架构模式
- MVC 分为三个部分
  - M（Model）：模型，是应用程序中用于处理应用程序数据逻辑的部分
    - 通常模型对象负责在数据库中存取数据
  - V（View）：视图，是应用程序中处理数据显示的部分
    - 通常视图是依据模型数据创建的
  - C（Controller）：控制器，是应用程序中处理用户交互的部分
    - 通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据

#### MVVM 模式

- MVVM 是一种软件架构模式
- MVVM 分为三个部分
  - M（Model）：模型层，指得是数据模型，主要负责业务数据相关，如 ajax 请求，数据处理等；在 Vue 中对应 data 配置项传入的数据
  - V（View）：视图层，负责视图相关，为了更方便的展示 M 层的数据；在 Vue 中对应视图模板
  - VM（ViewModel）：视图模型，V 与 M 沟通的桥梁，是实现 MVVM 双向绑定的要点，即当 M 层数据进行修改时，VM 层会监测到变化，并且通知 V 层进行相应的修改，反之修改 V 层则会通知 M 层数据进行修改；对应 Vue 的实例对象
- MVVM 优势：不用亲自操作 DOM，数据是响应式的；一旦数据变化，界面自动更新
- 总结
  - 传统开发模式（MVC），一般基于前后端项目在一起，前端只负责 View 层，完成的页面交由后端创建渲染模板并提供数据
  - MVVM 模式以及前后端分离的出现，前端已经可以自己写业务逻辑以及渲染模板，后端只负责提供数据即可


#### 观察者模式

- 当一个对象 A 中的数据被多个对象所依赖，并且当被依赖的对象发生改变的时候，会去通知所有的依赖项，这种模式被称为观察者模式
- 其中被依赖的对象被称为目标对象，依赖项被称为观察者

#### 订阅与发布者模式

- 订阅与发布者模式其实是属于观察者模式中的一种
- 观察者模式中的观察者被称为订阅者，观察者模式中的目标对象被称为发布者
- 每一个订阅者和发布者中间有一个调度中心（订阅中心），来实现数据的通信，并且订阅者和发布者都是不知道对方的存在
- 当订阅者订阅数据时，来订阅中心，订阅中心收集所有的订阅者
- 当发布者发布信息时，先传递给订阅中心，然后再由订阅中心传递给订阅者

#### vue 响应式（数据）原理

- 当 data 中的数据被修改的时候视图会随之发生更新
- 主要由三个方面构成
  - 数据代理、数据劫持、发布与订阅者模式
  - 数据代理
    - 通过一个对象代理，对另一个对象中属性的操作（读 / 写）
    - 在 Vue 中通过 vm 对象来代理 _data 对象中属性的操作（读 / 写），即把 _data 中的数据在 vm 上放了一份
    - 优势在于使操作 _data 中数据更加便捷，不需要通过对 _data 中数据成员访问时经过 _data
    - 基本原理
      - 在遍历 _data 数据时，通过 Object.defineProperty 方法给 vm 添加同名属性
      - 属性值使用 getter 和 setter 存取器属性
        - 当读取属性时，使用 getter 方法，返回 _data 的属性值
        - 当设置属性时，使用 setter 方法，设置 _data 的属性值
  - 数据劫持
    - 指的是在访问或者修改对象的某个属性时，通过一段代码拦截这个行为，进行额外的操作或者修改返回结果的过程
    - vue 中能监视到 data 中任意层级的属性值的更新
    - 实现
      - 通过 Object.defineProperty 来修改 data 中所有层级的属性，给属性添加 getter 和 setter
      - getter：用于收集依赖
      - setter：用于监视属性值的变化
    - 数据劫持是发布与订阅者模式中**发布者**实现响应式功能的原理，详见下方
  - 发布与订阅者模式（三种类）
    - Observer 类（发布者），主要是通过 Object.defineProperty 给 vm 的 _data 上的数据所有层级的属性都重写为 getter 和 setter 存取器属性；在 getter 中建立了 dep（订阅中心的实例化对象）和 watcher（订阅者的实例化对象）的关系，让 dep 收集访问当前数据的 watcher，在 setter 中通知所有的 watcher 进行重新获取数据
    - Dep 类（订阅中心），Dep 上有收集所有 watcher 的方法，和通知所有 watcher 重新获取数据的方法；数据中每一层需要劫持的属性在被劫持时，会创建一个 dep 对象（订阅中心的实例化对象），在劫持的 getter 中调用 dep 的收集依赖的 depend 方法，在 setter 中调用 dep 的通知更新的 notify 方法
    - Watcher 类（订阅者)，Watcher 上有获取数据的 get 方法和更新视图的 update 方法；每一个组件都对应一个 Watcher，Watcher 会在初次获取数据时被 dep 收集到数组中，当 dep 收到更新通知时，dep 就会通知所有的 watcher 实例调用 update 方法重新获取数据并更新视图
      - 三种 Watcher
        - render watcher（渲染 watcher）
          - 当组件中的响应式数据发生变化时（初始或更新），会触发重新渲染组件
        - user watcher（用户 watcher）
          - 每个组件中配置的 watch 和调用 $watch，都会创建一个 user 为 true 的 watcher
        - computed watcher（计算 watcher）
          - 每个计算属性，会通过 Object.defineProperty 给组件对象定义对应的属性
  - 图解
    - ![](/images/vue2响应式原理图.png)

#### $nextTick 的原理分析

- 作用
  - 指定回调函数，延迟到 DOM 更新后才执行，用于得到更新后的 DOM
- 原理
  - DOM 更新是异步执行的，且它的异步也是通过 nextTick 来实现的
    - 内部有一个队列数组（queue），用来保存待执行的 renderWatcher 和 userWatcher
    - 内部定义一个遍历队列的函数（flushSchedulerQueue），遍历每个 watcher，让 watcher 做对应的 DOM 更新
    - 当更新 data 数据时，会将对应的 renderWatcher 和 userWatcher 保存到队列数组（queue）中（通过 queueWatcher 函数添加 watcher）
    - 当更新第一个数据后，会调用 nextTick(flushSchedulerQueue)，保存到 callbacks 回调队列中
  - nextTick(callback) 的处理
    - 内部定义一个回调队列数组 callbacks，用来保存 nextTick 指定的回调（以及遍历 watcher 队列的函数 flushSchedulerQueue，在队头，因此才会更新 DOM 完成后，才执行回调函数，此时是最新的 DOM）
    - 定义一个遍历队列的函数 flushCallbacks，用来遍历执行 callbacks 中所有回调，此函数会进入异步队列执行
    - 每次调用 nextTick(callback) 时，都会将回调保存到 callbacks 中；第一次调用时，会将 flushCallbacks 指定为微任务或宏任务

#### 数据监测（响应式数据修改）

- 修改基本类型
  - 基本类型值是不可变的（可被替换），基本类型被替换时，是可以触发响应式的
- 修改对象类型
  - 对象类型包括内部的属性值一旦被修改，是具有响应式的
  - 对象属性的新增或者删除是没有响应式的
    - `vm.$set()` 或者 `Vue.set()` 可以用来做新增，并且内部帮我们完成响应式
    - `vm.$delete` 或者 `Vue.delete()` 可以用来做删除，并且内部帮我们完成响应式
- 修改数组类型
  - 数组中有 7 个变更方法（改变原始数组）：`push pop unshift shift splice sort reverse`，vue 重写以上 7 个方法，以上 7 个方法在完成修改数组的前提下，还会让视图重新渲染，所以我们使用以上 7 个方法修改数组，数组是具有响应式的
  - 相比之下，也有非变更方法，例如 `slice concat filter`，它们不会变更原始数组，而总是返回一个新数组，当使用非变更方法时，可以用新数组替换旧数组
  - 为什么 vue 在数组上使用重写方法的形式来实现响应式
    - 占用空间少，效率高：不用给每个元素都加 setter
    - 数组元素更新一般调用其方法；而对象的成员访问常用 `.xxx`
    - 存在限制：不能通过数组下标直接更新元素 / length
- 强制更新：`vm.$forceUpdate()` 迫使 vm 重新渲染

#### vue 的两个版本

- Runtime Only VS Runtime + Compiler

  - Runtime Only：不包含模板编译器
  - Runtime + Compiler：包含模板编译器

- vue-cli 创建的项目，默认使用 Runtime Only 版本

  - 运行时不支持模板编译
  - vue 组件文件中的 template 标签模板是 webpack 打包时，利用 vue-loader 对 vue 文件中的 template 编译，生成 render 函数

- 如果想要使用 Runtime + Compiler

  - `vue.config.js` 配置文件中指定引入 vue 带编辑器的库文件：`vue-esm.js`

  - ```javascript
    const { resolve } = require('path');
    module.exports = {
      configureWebpack: {
    	resolve: {
    	  extensions: ['js','vue','json'],
          modules: [resolve(__dirname,'src'), 'node_modules'],
          alias: {
    		'vue$': 'vue/dist/vue.esm.js' // 指定引入的 vue 库文件
            '@'： resolve('src'),
          }
        }
      }   
    }
    ```

#### 模板编译流程

- 目标：生成用于创建虚拟 DOM 的 render 函数

- 关键技术：正则 / ast / 优化算法

- 具体流程
  1. 解析模板生成抽象语法树（ast）对象
     - 抽象语法树（Abstract Syntax Tree）
       - 是源代码语法结构的一种抽象表示
       
       - 以树形结构表现编程语言的语法结构
       
       - 树上的每个节点都表示源代码中的一种结构
       
       - 常见属性
       
         - `tag`：标签名（字符串）
       
         - `attrs`：属性（数组）
       
         - `children`：子节点（数组）
       
         - ……
       
         - ```javascript
           {
               tag: '标签名',
               // 包含所有属性的数组
               attrs: [{name: '属性名',value: '属性值',……}],
               // 包含所有子节点的数组 
               children: [{type: 1,tag: '标签名',attrsList,children}]
           }
           ```
       
     - 利用正则解析模板，生成 ast 对象
     
  2. 对 ast 进行优化（添加静态标记）（vue3）
     
     - 目的：提高 Diff 算法的性能
     
     - 给不需要动态显示和更新的节点，添加静态标记：`static: true / false`
     - 标识有静态标记的 ast 节点对应的虚拟节点更新后，不需要重新生成，对应的真实 DOM 可以直接复用
     
  3. 根据 ast 生成用于生成虚拟 DOM 的 render 函数
  
     - render 函数，如
  
     - ```javascript
       function render() {
         with(this) {
           return _c('div', {
             attrs: {
               "id": "app"
             }
           }, [_c('h1', [_v("123")]), _c('span', [_v(_s(msg))])])
         }
       }
       ```

#### vue 中的虚拟 DOM

- 前提
  - vue / react 响应式库让我们只需要更新数据，而不需要直接更新 DOM，就可以更新界面，由库内部帮我们来操作 DOM
  - 为了实现最小化 DOM 更新，vue 内部设计了虚拟节点（VDOM）和虚拟节点算法（VDOM Diff）

- 借鉴
  - vue 虚拟 DOM 实现借鉴了开源的虚拟 DOM 库：[snabbdom](https://github.com/snabbdom/snabbdom)

- VDOM / VNode
  - 就是一个普通的 JS 对象，VNode 类型的实例
  - 包含了用于生成真实 DOM 的重要属性：标签名 / 标签属性 / 子节点 / 标识名
    - tag：标签名
    - data：{attrs：多个标签属性的对象}
    - children：包含 n 个虚拟子节点的数组
    - key：虚拟节点的标识名称，最好保证它的唯一性和稳定性，默认值：undefined

- 比较虚拟 DOM 和真实 DOM
  - 区别：虚拟 DOM 轻；真实 DOM 重
  - 关系
    - 初始化阶段会根据虚拟 DOM 生成真实 DOM
    - 更新阶段会进行新旧虚拟 DOM 的 Diff 比较，来进行真实 DOM 的更新

- 作用
  - 生成真实 DOM
  - 基于新旧虚拟 DOM 进行 DOM Diff，实现最小化 DOM 更新

- 图解
  - ![](/images/虚拟DOM.jpg)


#### vue 中 key 的作用以及 Diff 算法

- 虚拟 DOM 中 key 的作用：

  - key 是虚拟 DOM 对象的标识，在更新时 key 起到了极其重要的作用
  - 当数据发生变化时，vue 会根据新数据生成新虚拟 DOM
  - 随后 vue 进行新虚拟 DOM 和旧虚拟 DOM 的差异对比，比较规则如下

- 对比规则（Diff 算法）

  - 目标

    - 确定哪些真实 DOM 可以复用（内部可能要更新），要创建哪些真实 DOM
    - 提高效率：最少的查找比较，能复用的尽量复用

  - 对比思路

    - 只同层比较
      - 虚拟 DOM 是树形结构，只进行同层比较，次数少，效率高
      - ![](/images/Diff算法1.jpg)
    - 确定要比较的新旧虚拟节点
      - 旧虚拟 DOM 中找到了与新虚拟 DOM 相同的 key
        - 如果虚拟 DOM 中内容没变，直接使用之前的真实 DOM
        - 如果虚拟 DOM 中内容变了，则生成新的真实 DOM，随后替换掉页面中之前的真实 DOM
      - 旧虚拟 DOM 中未找到与新虚拟 DOM 相同的 key
        - 依次比较
        - 多出的虚拟 DOM，创建新的真实 DOM
        - 渲染到页面
    - 比较标签名
      - 如果不同，直接创建新的真实 DOM
      - 如果相同，复用原来对应的真实 DOM
        - 如果内部有变化，更新真实 DOM 内部内容

  - 算法细节（在虚拟 DOM 列表中，查找两个相同的虚拟 DOM 的算法）

    - > 新前 => 旧前
      >
      > 新后 => 旧后
      >
      > 新后 => 旧前
      >
      > 新前 => 旧后

      1. 每找到相同的新旧 DOM 或者一轮对比完成以后，指针指向下（上）一个虚拟 DOM
      2. 直到前后两个指针指向同一个虚拟 DOM
         - 如果是旧虚拟 DOM，表示旧虚拟 DOM 已经匹配完成，新虚拟 DOM 有剩余，则将剩余的新虚拟 DOM 转变为真实 DOM
         - 如果是新虚拟 DOM，表示新虚拟 DOM 已经匹配完成，旧虚拟 DOM 有剩余，则将剩余的旧虚拟 DOM 删除
      3. 如果经过上面步骤后还找不到匹配的
         - 创建一个剩余所有 key 与旧虚拟 DOM 的下标的映射对象（只创建一次）
         - 根据 newStartNode 的 key 去对象中匹配对应的虚拟 DOM（即从上到下依次匹配）

    - ![](/images/Diff算法2.png)

    - 数组元素更新，一般情况下整体顺序改变不会很大，当前这种算法的效率整体比较高

- 用 index 作为 key 可能会出现的问题

  - 若对数据进行逆序添加、逆序删除等破坏顺序操作
    - 会产生没必要的真实 DOM 更新 ==> 界面效果没问题，但是效率低
  - 如果结构中还包含输入类的 DOM
    - 会产生错误 DOM 更新 ==> 界面有问题

- 开发中如何选择 key

  - 最好使用每条数据的唯一标识作为 key 的值，如 id、身份证号、学号等唯一值
    - 通常后端数据库中都存在每条数据的唯一标识（id）
  - 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用 index 没有问题

#### new Vue() 做了什么

- > new Vue() 之前
  >
  > 1. xxxMixin：给 Vue 的原型对象添加相关方法
  >    - 如 _init / $set / $delete / $watch / $on / $once / $emit / $off / $nextTick
  >    - ![](/images/xxxMixin.png)
  > 2. initGlobalAPIs：给 Vue 添加静态方法
  >    - 如 set / delete / nextTick / use / extend / component / directive / filter

1. 合并传入的 options 到 $options

2. 初始化 1

   - `initLifecycle()`：给 vm 添加 $root / $refs / $parent / $children
   - `initEvents()`：给 vm 添加 _events 对象，用来存放事件
   - `initRender()`
     - 给 vm 添加 _c 方法，用于解析模板，渲染生成 VDOM 的 render 函数
     - 给 vm 添加 $createElement 方法，用于传递给 main.js 入口函数中的 render 配置中的 h 参数
     - 给 vm 添加 $listeners / $attrs 属性

3. 调用 beforeCreate 钩子（此时还没有初始化 data / props / methods / computed / watch 等）

4. 初始化 2

   - `initInjections()`：初始化 inject 配置，将 inject 声明的属性添加到 vm 上，但不是响应式的
   - `initState()`（重点）：初始化状态相关配置（data / props / methods / computed / watch）
     - `initProps`：通过 vm 代理对 props 属性的操作（数据代理）
     - `initMethod`：将 methods 中的方法添加到 vm 上，并绑定（bind）this 是 vm
     - `initData`
       - 将 data 添加到 vm 的 _data 上，并在 vm 上做数据代理
       - 对 data 中的数据进行深度数据劫持
     - `initComputed`：根据 computed 配置，创建 computedWatcher，并将计算属性定义为 vm 的属性
     - `initWatch`：根据 watch 配置，创建 userWatcher
   - `initProvide()`：初始化 provide 配置

5. 调用 created 钩子

6. 模板编译与挂载

   1. 是否有 el 配置
      - 如果有则调用 $mount 方法挂载到 el 对应的元素上
      - 没有则等待应用层调用 $mount 方法挂载到给定的元素上
   2. 是否有 template？（Runtime + Compiler）
      - 如果有则先编译 template 并生成 render 函数（常用 Runtime 版本不用，而是在打包时候依赖 webpack 的 vue-loader 对 .vue 文件进行 template 编译）
      - 没有 template，判断有无 render 配置项，没有就会报错
      - 注意：Runtime 版本有 template 或者没有 render 都会报错
   3. 定义挂载组件的函数 mountComponent
   4. 调用 beforeMount 钩子
   4. mountComponent 内部定义更新组件的函数 updateComponent
      1. 创建渲染 watcher（new renderWatcher）
      2. 内部调用 _render 生成虚拟 DOM
      3. 并调用 _update 生成真实 DOM 挂载到页面（\_update 内部调用的是 patch 函数）
   5. 调用 mounted 钩子
   
   - path 函数的作用
     - 初始化：根据传入的 vDOM 生成真实 DOM
     - 更新时：进行新旧 vDOM Diff 算法比较，进行最小化的 DOM 更新

- 详图
  - ![](/images/newVue.png)


### vue 组件生命周期

#### 生命周期

- 初始化阶段

  1. 实例化 Vue

  2. 初始化生命周期与事件
  3. 此时介入一个生命周期函数 `beforeCreate`
  4. 数据的注入与响应式（数据劫持与数据代理）
  5. 此时介入一个生命周期函数 `created`

  - `beforeCreate` 和 `created`
    - 表示的是数据注入与响应式（数据劫持与数据代理）之前与之后
    - `beforeCreate`：此时无法通过 vm 访问 data 中数据和 methods 中方法
    - `created`：此时可以通过 vm 访问 data 中数据和 methods 中方法

- 模板编译阶段

  1. 判断有无 el 配置项
     - 如果有，则继续向下
     - 如果没有，则等待 $mount 方法调用，调用以后继续向下
  2. 判断有无 template 配置项
     - 如果有，把 template 中书写的模板进行编译成虚拟 DOM
     - 如果没有，把根容器 el 的 outerHTML 作为模板进行编译成虚拟 DOM

  - 此阶段开始解析模板，在内存中生成虚拟 DOM，页面还不能显示解析好的内容

- 挂载阶段

  1. 此时先介入一个生命周期函数 `beforeMount`
  2. 把模板编译阶段的虚拟 DOM 转为真实 DOM，并替换 el 容器，我们可以通过 vm.$el 获取到真实 DOM 根元素
  3. 此时介入一个生命周期函数 `mounted`

  - `beforeMount` 和 `mounted`
    - `beforeMount`：此时页面呈现的是未经 Vue 解析的 DOM 结构，对 DOM 的所有操作无效
    - `mounted`：此时页面呈现的是经过 Vue 解析的 DOM 结构，对 DOM 的操作有效（尽量避免）；初始化过程已结束，一般在此处开启定时器，发送 AJAX 请求，绑定自定义事件，订阅消息等初始化操作

- 更新阶段

  1. 挂载之后，当模板中数据发生改变时
  2. 此时介入一个生命周期函数 `beforeUpdate`
  3. 根据新数据生成新的虚拟 DOM，新旧虚拟 DOM 进行 DIff 算法比较，最终完成页面的更新，即 Model => View
  4. 此时介入一个生命周期函数 `updated`

  - `beforeUpdate` 和 `updated`

    - `beforeUpdate`：此时数据是新的，但页面还未发生更新，即数据与页面尚未保持同步

    - `updated`：此时数据是新的，页面也是新的，即数据与页面保持同步

- 卸载阶段

  1. 当调用 vm.$destroy 方法的时候进入卸载阶段（其实当一个组件因为路由或者条件渲染情况下，也会进行卸载，Vue 中是不建议我们直接使用 $destroy 卸载的）
  2. 介入一个生命周期函数 `beforeDestroy`
  3. 进入 Vue 的卸载过程，完全销毁一个实例，清理与其它实例的连接，解绑它的全部指令及事件监听器
  4. 介入一个生命周期函数 `destroyed`

  - `beforeDestroy` 和 `destroyed`

    - `beforeDestroy`：此时 vm 中的所有 data、methods、指令等等都处于可用状态，马上要执行销毁过程；一般在此处进行关闭定时器、解绑自定义事件、取消订阅消息等收尾工作
  
- 补充

  - `destroyed`：组件实例已经被销毁，这个生命周期基本不用
  - 发送请求在哪里发？
    - `created / beforeMount / mounted` 都可以，`mounted` 更常用
    - 如果发送请求之前，需要读取页面内容，则只能在 `mounted` 发送

#### 父子组件的生命周期

- 初始化挂载阶段
  1. 父组件 beforeCreate
  2. 父组件 created
  3. 父组件 beforeMount
  4. 子组件 beforeCreate
  5. 子组件 created
  6. 子组件 beforeMount
  7. 子组件 mounted
  8. 父组件 mounted
- 更新阶段
  - 如果子组件没有使用父组件更新的数据，则子组件是不会发生更新或者重新渲染
    1. 父组件 beforeUpdate
    2. 子组件 beforeUpdate
    3. 子组件 updated
    4. 父组件 updated
- 销毁阶段
  1. 父组件 beforeDestroy
  2. 子组件 beforeDestroy
  3. 子组件 destroyed
  4. 父组件 destroyed

#### 带缓存的路由组件生命周期

- activated：组件激活，在初始化最后 / 再回到当前路由调用
  - 被 keep-alive 缓存的组件激活时调用

- deactivated：组件失活，离开当前路由调用
  - 被 keep-alive 缓存的组件失活时调用

- 具体
  - 初始化
    - ...
    - mounted
    - activated

  - 离开当前路由
    - beforeCreate
    - created
    - beforeMount
    - deactivated：在下一个路由组件挂载之前，上一个路由组件失活
    - mounted
    - activated

#### 捕获子组件错误的钩子

- 子组件执行抛出错误时调用
  - errorCaptured：return false 表示错误已经处理了，不需要再向外传递这个错误

#### 详图

- ![](/images/vue组件生命周期详图.png)

### 组件深入

#### 组件的本质

- 使用 Vue.extend 创建的组件其实是一个 VueComponent 构造函数
- 当组件被注册并使用的时候，会实例化这个 VueComponent 构造函数，得到一个组件实例对象
- 组件实例对象其实就是一个小型的 vm 对象
- 组件中所有的方法和数据其实都是放在这个组件实例上，组件中的方法的 this 也都是指向组件实例

#### 重要的内置关系

- VueComponent 类继承 Vue 类，因为 VueComponent 可能有多个，Vue 只有一个，我们把所有实例公共方法放在 Vue 的原型对象上，即可实现所有共享
- 组件实例 => 当前组件的 VueComponent.prototype => Vue.prototyoe => Object.prototype => null
- 如要让所有的组件都能访问一个属性或者方法，则把这个属性或者方法放在 Vue 的原型对象上即可

#### 动态组件

- Vue 提供了一个 component 组件，可以用来做动态组件
- component 组件是一个占位符，接受一个 is 属性，is 属性的值是一个字符串类型，并且已经被引入和注册的组件名称，并且 is 必须要求强制绑定
- 我们可以通过改变 is 强制绑定的值，来切换替换 component 组件

#### 缓存组件

- keep-alive：用于缓存组件，包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们
- 作用
  - 防止重复渲染 DOM，减少加载时间及性能消耗，提高用户体验性

- 注意
  - 默认缓存所有动态组件

- 属性
  - include 和 exclude 允许组件有条件地缓存
    - 形式：逗号分隔的字符串 | 数组 | 正则表达式
- keep-alive 的生命周期函数
  - activated：被 keep-alive 缓存的组件激活时调用
  - deactivated：被 keep-alive 缓存的组件失活时调用
- 简要原理
  - 利用了虚拟 DOM，在组件切换过程中，把被切换的组件保留在内存中

#### 异步组件

- 问题
  - 直接使用 import 模块化引入 vue 模块，则 webpack 在打包构建的过程中，会把所有的 js 都打包到了一起
  - 但是里边包含了很多暂时没有使用的模块，这样包的体积过大，就会造成进入首页时需要加载的内容过多，出现长时间的白屏现象
- 解决
  - 可以使用异步组件，让 webpack 打包的时候把异步组件进行分开打包，需要的时候再去加载这个组件
- 异步组件
  - vue 允许以一个函数的方式定义组件，函数内部使用 import 方法引入某个模块
  - import 方法返回 promise 实例，当 import 引入成功则 promise 变成成功状态，import 失败则返回失败的 promise 实例
  - 定义组件的函数需要把 import 的返回值进行返回，让组件在渲染的时候能够知道渲染状态，即获取引入的模块
  - vue 只有在这个组件需要被渲染的时候才会触发该函数，且会把结果缓存起来供未来重渲染
  - webpack 在打包的时候，遇到 import 动态引入，则会把 import 动态引入的资源进行单独打包

#### 递归组件

- 理解：组件内部有自己的子组件标签

- 使用场景：用于显示树形结构的界面

- 注意：递归组件必须有 name

- 实现：一个简单的可开关的树形结构界面的 Tree 组件

  - ```vue
    <template>
      <ul>
        <li
          v-for="(item, index) in data"
          :key="index"
          @click.stop="handleClick(item)"
        >
          {{ item.text }}
          <Tree v-if="item.expend" :data="item.children" />
        </li>
      </ul>
    </template>
    
    <script>
      export default {
        name: 'Tree', // 作为内部的标签名，必需
        props: ['data'],
        methods: {
          handleClick(item) {
            if (item.hasOwnProperty('expend')) {
              item.expend = !item.expend;
            } else {
              this.$set(item, 'expend', true);
            }
          },
        },
      };
    </script>
    ```

### 组件通信

#### 整体列表

> 父传子
>
> > props（非函数）
> >
> > v-model
> >
> > .sync
> >
> > $refs，$children
> >
> > 插槽

> 子传父
>
> > props（函数）
> >
> > 自定义事件
> >
> > v-model
> >
> > .sync
> >
> > $parent
> >
> > 作用域插槽

> 祖孙
>
> > $attrs，$listeners
> >
> > provide | inject

> 任意
>
> > 全局事件总线
> >
> > $root
> >
> > vuex

> 路由组件通信

以上只代表哪种情况下哪种方式常用，不代表某种方式只适用于某种情况

#### $refs

- ref 被用来给元素或子组件注册引用信息，引用信息将会注册在父组件的 $refs 对象上
  - 如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素
  - 如果用在子组件上，引用就指向组件实例
- 也是组件通信的一种方式，因为可以在父组件操作子组件的数据

#### props

- props 主要是用来做父组件向子组件传递数据的（通过给子组件元素添加属性的方式传递）
- 在子组件内部通过 props 配置项接收父组件传递的 props 值，并把值放在子组件的组件实例上
- props 也能用来子传父
  - vue 是单向数据流，数据只从高层的组件流向低层的组件，后代组件不能直接修改祖辈组件的数据
  - 可以给子组件传递一个 props 值为函数，子组件通知父组件修改父组件的值时，可以调用 props 接收的函数，父组件就会收到通知，修改自己的值
- 注意
  - props 是只读属性，如果子组件内要修改的话推荐使用 computed 把接收的 props 数据变为自己的数据
  - 在传递 props 时，如果值是需要计算得到的，请使用 v-bind 强制绑定；而且可以使用 v-bind 分别批量传递对象中的值
  - 子组件的 props 配置项，可以是一个数组或者一个对象

#### 自定义事件

- 如果想要进行子传父的组件通信，可以选用自定义事件
- 给子组件绑定自定义事件，事件函数在父组件中，v-on 可以分别批量绑定对象中的事件给子组件
- 在子组件内触发自己身上的自定义事件，处在父组件中的事件函数就会执行
- 可以在触发自定义事件时，传递参数，父组件的事件回调函数就能接到参数，实现子传父
- 注意
  - 在 HTML 标签上添加就是原生的 DOM 事件
  - 在组件标签上添加就是自定义事件，想成为原生的事件得添加修饰符 native，就是把原生 DOM 事件添加到子组件根元素上
  - 自定义事件在 HTML 标签和组件标签上的区别
    - 在 HTML 标签上添加自定义事件无意义
    - 添加给组件标签，事件名可以任意，也可以和原生的 DOM 事件名相同，但是在组件标签身上即使添加原生 DOM 事件也是自定义的

#### 全局事件总线

- 事件总线内部使用自定义事件来完成组件通信的，但是主要做的任意组件通信
- 找一个可以被绑定自定义事件的实例（vm），放在所有组件都能访问到的地方（Vue.prototype），命名为 $bus
- 在接收数据的组件中（一般在 mounted 钩子中），给 $bus 绑定自定义事件，事件函数在当前组件内部
- 在发送数据的组件中，给 $bus 调用自定义事件并传值，则绑定事件的组件就会调用函数，完成传值

#### 消息订阅与发布（PubSub）

- PubSub 是使用第三方包进行任意组件通信的
- PubSub 提供了一个对象作为中介，数据的传输方可以给这个中介发布某些固定名称的数据，数据的接收方可以在这个中介订阅某些固定名称的数据，一旦发布新的数据，则订阅方就会收到 PubSub 的通知，接收数据执行函数
- 发布：`PubSub.publish('name',data)`
- 订阅：`PubSub.subscribe('name',fn('name',data))`
  - 回调函数的第一个参数是消息名字，一般以 _ 代替，第二个参数即传递过来的数据


#### $root

- vue 所有组件实例身上都有一个 $root 属性，它们指向整个项目的根组件，一般也就是 App 组件
- 我们可以借助这个 $root 做事件总线类似的传值方式
- 理解为最牛的状态提升（实现状态的组件共享，将状态放在所有组件都能访问的位置，一般是父级组件或 vm）

#### v-model 父子组件数据双向绑定

- 通过 props + 自定义事件，类比 v-model 在表单元素的实现
- 结合 v-model 的本质：v-bind 强制绑定 + input 事件
  - 在父子组件数据双向绑定中，v-bind 强制绑定即 props 父向子传值，input 事件为自定义事件 input

- 注意（插值语法中）
  - 在原生事件中，$event 是事件对象
  - 在自定义事件中，$event 是传递过来的值（参数）

#### sync 修饰符实现多数据父子组件数据双向绑定

- sync：同步，原理类似 v-model，可以多数据的父子组件通信
- 在 props 强制绑定传值时，props 属性添加修饰符 sync 即可，自动实现通过自定义事件进行子传父的通信
- 与 v-model 的区别
  - 在标签上只能绑定 1 个，表单上只能使用v-model；而 sync 可以实现多个数据父子组件双向绑定
  - v-model 用的事件名 input，属性名是 value；sync 用的事件名 update:属性名，属性名自定义

#### $attrs 和 $listeners

- 多层嵌套组件传递数据时，如果只是传递数据，而不做中间处理的话就可以用 $attrs 和 $listeners，比如父组件向孙子组件传递数据时
- $attrs：包含父作用域里 class 和 style 除外的 props 属性集合；通过 this.$attrs 获取父作用域中所有符合条件的属性集合，然后还要继续传给子组件内部的其它组件，就可以通过 v-bind="$attrs"
- $listenners：包含父作用域里 .native 除外的监听事件集合；如果还要继续传给子组件内部的其它组件，就可以通过 v-on="$listeners"
- 可以通过这两个属性二次开发组件
- 注意
  - 如果在组件中接收 $attrs 对象中将不存在接收的属性和值
  - 监听事件集合中无论组件触发与否，不会改变

#### $children 和 $parent

- $children：获取到一个包含所有子组件（不包含孙组件）的 VueComponent 对象数组，可以直接拿到子组件中所有数据和方法等（不建议使用下标的形式控制某一个子组件，因为 $children 拿到的子组件顺序不确定）
- $parent：获取到一个父节点的 VueComponent 对象，同样包含父节点中所有数据和方法等，因为一个组件可能被使用多次，那就有多个父组件，无法判断用的是哪一个父组件（但是如果当前组件只使用一次，则可以使用这个 $parent 获取它的父组件）

#### provide 和 inject

- 这对选项需要一起使用，以允许一个祖先组件向其所有子孙后代注入一个依赖，不论组件层次有多深，并在其上下游关系成立的时间里始终生效
- 注意：provide 和 inject 绑定并不是可响应的，这是刻意为之的；然而，如果你传入了一个可监听的对象，那么其对象的 property 还是可响应的

#### 插槽（slot）

- 默认插槽（匿名插槽）
  - 在封装组件的时候,如果组件中某一块的结构,需要在组件使用的时候传递过来,我们就使用一个 slot 内置组件标签占位，这个 slot 就是插槽的位置
  - 在使用组件的时候，如果要传递一个插槽，则直接在组件的双标签内部书写结构即可，组件内部的 slot 就会展示我们传递的结构
- 具名插槽
  - 封装组件时，可能需要被传递多个插槽结构，为了区分则要给插槽命名，每一个 slot 标签上都可以书写一个 name 属性
  - 在使用组件传递插槽时，要使用 `v-slot:xxx` 形式来标明传递到哪一个插槽中
    - 注意
      - v-slot 只能写在组件或者 template 标签上
      - `v-slot:` 可以简写为 `#`
- 作用域插槽
  - 在向组件传递插槽结构时，想要拿到组件内部的一些数据，此时则需要作用域插槽
  - 在组件内部封装时，要使用 props 的形式向 slot 标签进行传递数据
  - 在向组件插入结构时，通过 `v-slot:xxx='obj'` 来接收组件内部传递回来的数据，其中 obj 是对象（包含所有传递过来的数据）
  - 接收作用域数据时，支持解构，如 `v-slot:xxx='{content}'`

#### vuex

- Vuex 是状态管理工具，集中式存储管理所有组件的状态，实现多组件共享数据

#### 路由组件通信

- 参考 **vue-router**
  - 动态路由（query、params / path）
  - 路由组件传参（props）
  - 路由元信息（meta）
- 参考 **vuex**

### vuex

#### 详图

- ![](/images/vuex完整版.png)

#### 从 store 中读取值

- 方法1：直接在插值中使用 `$store.state.xxx` 即可
- 方法2：我们在计算属性中获取到某个值，在插值语法中直接拿到计算属性即可（比方法1好维护）
- 方法3：使用 mapState 辅助函数
  - mapState 接收一个数组或者对象，返回一个对象
  - mapState 对象内部的方法其实就是我们去读取某个 store 数据的计算属性的方法
  - 我们只需要把 mapState 得到的对象在 computed 中展开，则默认写好所有的获取 store 数据的计算属性的方法

#### mutations 修改 state 数据

- 首先在 store 的 mutations 配置对象中封装函数，mutations 中的函数是修改 state 数据的唯一途径，所有修改 state 的操作都会在 mutations 中的方法内进行
- mutations 中的方法接受的第一个参数就是 state 对象，第二个参数是调用这个函数时传递的载荷（payload），建议传递载荷的时候使用对象形式
- 在组件内使用 $store 上的 commit 方法来调用 mutations 中的函数，commit 方法接收两个参数，参数 1 是事件类型（mutations 中的函数名），参数 2 是调用函数时传递的载荷（payload）
- 在组件内使用 commit 方法调用 mutations 函数
  - 方法1：直接在插值中使用 `$store.commit(type,payload) `
  - 方法2：在 methods 中封装函数，使用 commit 方法调用 mutations 函数
  - 方法3：直接使用 mapMutations 辅助函数（可以接受一个数组或者对象），其实就是帮我们得到一个包含调用 mutations 方法的一个对象，直接在 methods 中展开即可

#### actions 中处理复杂逻辑与异步操作

- 如果 mutations 中修改数据的逻辑较为复杂，那么推荐把更多的逻辑写在 actions 中，最终仍然在 mutations 中修改数据
- 异步操作
  - 在 mutations 中也可以异步修改 state，但是开发者工具不会监听到数据的变化，导致工具和视图不同步
  - 可以把异步操作放在 actions 中，然后异步操作结束之后，在 actions 内部提交给 mutations 对应的函数进行修改数据
  - actions 接受两个参数，第一个是 context（上下文，小型的 store 对象），内部有 commit 方法可以提交 mutations，另一个参数就是组件中分发 actions 时传递的参数 payload（载荷）
  - 组件中调用 actions 的方法
    - 直接在插值中使用 `$store.dispatch(actionsName,payload)`
    - 在 methods 中封装函数，使用 dispatch 方法调用 actions 函数
    - 直接使用 mapActions 辅助函数（可以接受一个数组或者对象），其实就是帮我们获得一个包含分发 actions 方法的一个对象，我们直接在 methods 中展开即可

#### getters 中书写 vuex 的计算属性

- 有些情况下，需要从 store 中的 state 中派生出一些状态，需要使用 getters
- vuex 的 getters 其实类似于 vue 组件的计算属性
- getters 内部的函数接受 state 作为参数，函数内部必须要返回一个值，作为计算属性的值
- 组件中使用 getters 计算属性
  - 直接在插值中使用 `$store.getters.xxx`
  - 在 computed 中封装函数，访问 getters 中的计算属性
  - 直接使用 mapGetters 辅助函数（可以接受一个数组或者对象），直接在组件计算属性中展开返回的对象，则获取了 getters 中所需的计算属性

#### 模块化与命名空间

- module | namespaced
  - 每一个模块都是一个对象，可以包含完整的 vuex 属性（除了 module）
  - 当 vuex 管理的数据过多的情况下，可以使用 vuex 模块化
  - vuex 模块化时，添加一个namespaced 的配置，这样能够处理各个模块相关配置中命名冲突的情况，更规范地获取和操作数据
  - 模块化后
    - 使用辅助函数，辅助函数的第一个参数是命名空间的模块名，第二个参数是获取的内容组成的数组或者对象
    - 不使用辅助函数，特别注意获取 getters、actions、mutations 相关方法名是 模块名/方法名

#### vuex 数据的持久化（页面一旦刷新数据会丢失怎么办？==> 数据持久化）

- 手动数据持久化
  - 定义一个初始的 state 值，给 state 赋值时，先去 localStorage 中读取值，如果没有则得到初始的 state 值
  - 在所有的 mutations 方法中，在改变 state 值后，重新保存 localStorage
- 自动数据持久化
  - 可以使用第三方包，如 `vuex-persistedstate`
  - 在 store 下的 Vue.Store({}) 中使用插件 plugins 配置
    - `plugins: [createPersistedState()]`

#### vuex 状态响应式原理

- 什么是响应式：更新 vuex 数据，视图会随之更新
- 其实 vuex 内部也会创建一个 Vue 的实例对象（vm）
- vuex 中的 state 数据其实都是在它内部的 vm 身上进行管理
- 也就是说 vuex 的响应式数据原理是借助于 vue 的响应式数据原理来实现的


### vue-router

#### hash 模式和 history 模式的对比

- hash 模式
  - hash 模式是一种把前端路由的路径用 # 拼接在真实 URL 后面的模式
  - 内部利用的是 location 对象的 hash 语法
    - 读：`location.hash`
    - 写：`location.hash = '#/xxx'`
    - 监视：\# 后面的路径发生变化时，浏览器并不会重新发起请求，而是会触发 hashchange 事件，在 hashchange 事件中可以切换组件
  - hash模式的浏览器兼容性较好，就是看起来不够优雅
  
- history 模式
  - history 模式用到了 HTML5 中的 history API，允许开发者直接更新浏览器 URL 地址而不重新发起请求
  
    - 用到了 history API：pushState、replaceState、back、forward 和 go 这 5 个方法
    - 如果使用 pushState 改变了地址，浏览器回退历史记录的时候，视图不会发生改变；我们可以使用 window.popState 事件监听浏览器历史记录的改变，从而改变视图
  
  - history 兼容性不如 hash 模式，而且浏览器在刷新时会按照路径发送真实的资源请求，如果没有额外的配置，则可能会返回 404
  
    - 解决方式：如果 URL 匹配不到任何静态资源（404），则应该返回同一个 index.html 页面，这个页面就是当前 app 依赖的页面
  
      - 开发环境下：脚手架项目配置
  
        - `devServer: {historyApiFallback: true}`
  
      - 生产环境下：配置 nginx
  
        - ``` nginx
          location / {
          	try_files $uri $uri/ /index.html; # 所有404的请求都返回index页面
          }
          ```
  
      - 因此在线上部署基于 history API 的单页面应用时，一定要后端配合支持才行

#### 编程式路由导航与声明式路由导航（跳转 / 导航路由的 2 种基本方式）

- 编程式路由导航
  - 可以借助 router 的实例方法 `$router.push()` 来进行定义导航链接
  
    - 参数
      - 一个字符串路径，如 `$router.push('/home/news')`
      - 一个描述地址的对象 location，对象内部有 name 和 path 属性，可以控制导航到哪一个路由，path 和 name 随意使用一种即可，path的值是完整地址，name的值是路由命名
  
  - 其它方法
    - `$router.replace()`：和 `$router.push()` 一致，但不会留下任何的历史记录
    - `$router.back()`：历史记录回退 1
    - `$router.forward()`：历史记录前进 1
    - `$router.go(n)`：历史记录前进或回退 n
  
  - 编程式路由导航重复点击控制台报错
    - 问题：编程式路由跳转到当前路由，参数不变，会报出错误
  
    - 原因：如果重复导航 push 或者 replace 则会返回一个失败的 promise 实例，但是 push 原本没有做任何处理，所以浏览器会报错，表示有失败的 promise 没有被处理
  
    - 原理：vue-router 版本变化
  
      - 3.1 版本（2019-08）没有这个问题，3.1.0 及之后才出现这个问题
  
        - 3.1.0 之前：返回值 undefined
  
          - ```javascript
            push(location)
            push(location,()=>{},()=>{}) // 带成功与失败的回调
            ```
  
        - 3.1.0 及之后：如果没有指定回调函数，则返回 promise 对象
  
          - `push(location) ==> 出现错误`
  
    - 解决方式
      - push 可以接收第二个和第三个参数，分别是导航成功和导航失败的回调函数，如果书写了第三个参数处理导航失败（函数体任意），则解决报错问题
      
      - 如果 push 没有书写第二个和第三个参数，则 push 会返回一个失败的 promise，可以使用 catch 方法处理捕捉错误即可（传入的参数回调函数体任意） 来处理这个错误即可解决
      
      - 推荐重写 `VueRouter.prototype.push` 方法
      
        - 如果没有指定回调函数，需要调用原本的 push 后 catch 来处理错误的 promise
      
        - 如果传入了回调函数，本身就没问题，直接调用原本的 push 即可
      
        - ```javascript
          // 保存一份原来的 push
          const originPush = VueRouter.prototype.push;
          // 重写 push
          VueRouter.prototype.push = function (location, onComplete, onAbort) {
          // 判断如果没有指定回调函数，通过 call 调用原函数并使用 catch 来处理错误
             if (onComplete === undefined && onAbort === undefined) {
                return originPush.call(this, location).catch(() => {});
             } else {
                // 如果有指定任意回调函数，通过 call 调用原函数处理
                return originPush.call(this, location, onComplete, onAbort);
             }
          };
          ```
      
      - 声明式路由跳转之所有没有问题，是因为默认传入了成功的空回调函数
  
- 声明式路由导航
  - 使用 router-link 组件
    - router-link 组件内部也是使用 $router.push 进行导航
    - 最终在页面上被渲染成 a 标签（默认）
  - 属性
    - to：接收的参数就是 push 方法接收的 location 参数，用来控制跳转
    - tag：如果想要 router-link 渲染成某种标签，则使用 tag 指定何种标签，默认为 a 标签
    - replace：设置 replace 属性，点击时会调用 $router.replace 而不是 $router.push，于是导航后不会留下历史记录
    - active-class：设置链接激活时使用的 CSS 类名

#### 动态路由传参

- 经常需要把某种模式匹配到的所有路由，全都映射到同个组件
- 因为组件相同，但是组件内部要区分对应的路由，所以可以在路由路径中使用动态路径参数来达到这个效果
- 动态路由的 query 参数
  - 可以在路由导航时传递查询字符串参数
    - 直接在路由字符串上拼接查询字符串即可
    - 可以在 to 为 location 对象写法时，添加 query 属性为一个对象，对象内部就是 query 参数
  - 在路由组件中通过 $route.query 来接收 query 参数
- 动态路由的 params 参数
  - 可以在路由导航时在路由后添加 params 参数
  - 必须要在路由配置的 path 中去书写接收 params 参数的属性名，格式是 `/:xxx/:xxx?`
  - 在路由组件中使用 $route.params 来接收 params 参数
  - 注意
    - 如果在路由导航时使用 location 对象形式和 params 配合使用，则不能使用 path 导航（用 name 配置）
    - 配置 params 参数可传可不传
      - 如 `path: '/search/:keyword?'`
      - 可选的参数不能是一个空字符串
    - 跳转携带的参数，刷新后丢失
      - 注册路由时需要特定的占位，如 `path: 'detail/:id'`

#### 路由组件传参

- 除了动态路由可以向组件内部传递 params 和 query 参数以外，也可以在路由表中使用 props 属性给某个特定的路由传递参数
- 三种形式
  - props 是一个对象：在组件内部就能通过 props 属性接收到 props 对象中传递的数据
  - props 是布尔值为 true：会把当前路由规则接受的 params 参数通过 props 的形式传递给组件内部
  - props 是一个函数：当前的路由规则被匹配的时候，props 函数就被调用，props 函数接收当前路由的 $route 作为参数，props 函数的返回值对象中的属性就是将来在组件内部能够通过 props 属性获取的值

#### 路由元信息

- 定义路由规则时可以配置 meta 字段
- meta 一般是一个对象，meta 的数据其实就是路由的元信息（描述当前路由的一个固定信息）
- 可以在组件内部通过 $route.meta 得到元信息的内容
- 可以在组件外部通过遍历 routes 路由表得到每一个组件的元信息

#### 缓存路由组件

```vue
<keep-alive>
    <router-view>
</keep-alive>
```

- 基于缓存组件，路由离开时不销毁，路由回来时不用重新创建
- 利用缓存，切换路由更快

#### 路由懒加载

- 问题：当打包构建应用时，JavaScript 包会变得非常大，影响页面加载

- 思路
  - 把不同路由对应的组件分割成不同的代码块（单独打包）
  - 当路由被访问的时候才加载对应组件（按需加载）
  - 加载更快，提升用户体验

- 解决：结合 vue 异步组件和 webpack 代码分割功能，实现路由组件的懒加载

- 路由懒加载
  - 路由组件的异步加载，即路由组件被单独打包，并且被需要的时候才去加载这个文件
- 补充
  - 除了组件，其它模块也可以异步懒加载

#### 路由导航守卫

- 路由导航守卫实现 vue-router 提供两个功能

  - 监视路由跳转 ==> 回调函数
  - 控制路由跳转 ==> 放行 / 不放行 / 强制跳转到指定位置 => `next(path)`

- 应用

  - 在跳转到页面前，进行用户权限检查限制（如，是否已经登录 / 是否有访问路由的权限）
  - 在跳转到登录页面前，判断用户没有登录，才显示登录页面

- 分类

  - 全局导航守卫：针对任意路由跳转
    - 全局前置守卫：`router.beforeEach()`，所有导航都会最先触发
    - 全局解析守卫：`router.beforeResolve()`，在导航被确认之前，同时在所有组件内守卫和异步路由组件被解析之后，解析守卫就被调用
    - 全局后置钩子：`router.afterEach()`，导航已经全部完成，没有 next 参数
  - 路由独享守卫
    - `beforeEnter()`，设置在路由规则中，针对某一个路由进行守卫
  - 组件内守卫
    - 组件内进入时守卫：`beforeRouteEnter()`，刚刚进入当前组件，但是在渲染当前组件前（new VueComponent 前）就调用（此时没有 this，组件实例还未创建）
    - 组件内更新时守卫：`beforeRouteUpdate()`，在当前路由改变，但是该组件被复用时调用
    - 组件内离开时守卫：`beforeRouteLeave()`，导航离开该组件的对应路由时调用
  - 路由导航守卫参数
    - to：即将要进入的目标路由对象
    - from：当前导航正要离开的路由
    - next：一定要调用该方法，来确认守卫后导航下一步的行为
      - 参数为空：放行
      - 参数为一个地址字符串：代表导航到该地址

  - 路由导航守卫执行顺序
    1. 某个导航被触发
    2. 先调用失活组件内部的**组件内离开时守卫**
    3. 调用**全局前置守卫**
    4. 调用某个路由的**路由独享守卫**
    5. 调用组件内的**组件内进入时守卫**
    6. 调用**全局解析守卫**
    7. 调用**全局后置钩子**


#### 其他

##### 如何让路由跳转后，滚动条自动停留到起始位置

- ```javascript
  new VueRouter({
      scrollBehavior(to,from,savedPosition) {
  		// 对于所有路由导航，让页面滚动到顶部
          return {x: 0,y: 0};
          // 在按下后退 / 前进按钮时，页面滚动停留在离开时的位置
          if(savedPosition) {
              // 返回前面离开时保存的位置坐标对象
              return savedPosition;
          } else {
              // 否则直接滚动到顶部
              return {x: 0,y: 0}
          }
      }
  })
  // 注意：vue3 改为 return {left: 0,top: 0};
  ```

##### 如何实现登录后，自动跳转到前面要访问的路由页面

- 在全局前置守卫中，强制跳转到登录页面时携带目标路径的 redirect 参数

  - ```javascript
    if(userInfo.name) {
    	next();
    } else {
        // 如果还没有登录，强制跳转到 login
        // 携带目标路径的参数数据
        next('/login?redirect=' + to.fullPath);
    }
    ```

- 在登录成功后，跳转到 redirect 参数的路由路径上

  - ```javascript
    await this.$store.dispatch('login', {mobile, password});
    // 成功则跳转到 redirect 路由或首页
    const redirect = this.$route.query.redirect; // 从 query 参数中取即可，因为是拼接到 url 后的 query string
    this.$router.replace(redirect || '/');
    ```

##### 如何监听动态路由变化

- 动态路由是组件已经被复用，但传递的动态参数可能会发生变化，因此需要监听动态路由的改变
- 使用**组件内更新时守卫（beforeRouteUpdate）**
  - 这个守卫有限制，需要组件复用的时候路由地址不变，只有动态参数发生变化，此时守卫才会触发
  - 守卫中直接获取的 $route 的值还是旧值，需要通过守卫钩子的参数 to，获取最新的 $route
- 使用 watch 监听 $route（推荐使用）
  - 不需要深度监听，因为每次得到的都是一个新的 $route 对象
  - 在 watch 的回调函数中获取的就是最新的 $route

##### 如何动态添加路由

- 方法

  - ```javascript
    router.addRoutes(routes);
    router.addRoute(route);
    ```

- 场景

  - 在异步确定用户的权限路由后，需要动态添加到路由器

- 说明

  - 动态添加的路由在当次路由跳转不可见，只有在添加后的路由跳转才可见（异步）
    - next(to)，重新跳转到指定路由

- 路由守卫和权限校验

  - router.beforeEach() 注册全局前置守卫
  - 统一对用户权限进行一系列的校验处理

### 其它

#### scoped 原理

- 给当前组件的所有元素上都添加一个 data-v-xxx 的自定义属性（当前组件内一致，组件之间唯一），如果有子组件，则给子组件的最外层容器也添加上一个自定义属性
- 给 style 中所有的选择器都添加一个属性选择器，要求除了满足选择器以外还要拥有刚才给自己组件的元素添加的自定义属性

#### 深度选择器

- 我们希望在当前组件中控制后代组件中某个元素的样式，我们不能直接书写后代选择器，因为 scoped 给所有的选择器都添加了自己的 data-v 标识
- 我们希望后代选择器后边的选择器不要再添加标识，这样就可以进入选择了，我们需要把后代选择器替换为深度选择器 `>>>` 即可
- scoped 不会给深度选择器 `>>>` 后边的选择器添加标识
- 使用场景
  - Carousel 轮播图分页器的样式
  - Drawer 自动滚动，并隐藏滚动条
  - ……


> ## Vue3

### vue3 与 vue2 的区别（vue3 比 vue2 有什么优势）

#### 体积更小

- 将多个功能以多个函数提供出来，会进行按需引入
- 引入 tree-shaking，可以在打包压缩时，将无用模块“摇掉”

#### 性能更好

- 使用 proxy 代替 Object.defineProperty 来实现数据劫持
- Diff 算法优化：静态虚拟节点添加静态标记，不进行 Diff 比较，直接复用对应的真实 DOM
- 静态提升：静态虚拟节点提升到 render 的外部，缓存起来，不创建新的

#### 启动更快

- 更好的脚手架工具 vite
  - 开发环境中，无需打包操作，可快速的冷启动
  - 轻量快速的热重载（HMR）
  - 真正的按需编译，不再等待整个应用编译完成

#### 更好地支持 TS | 组件通信的变化

##### 增加了向外暴露的方法

- 组件内部的方法默认在外部是不能调用的

- vue3 中可以通过 defineExpose 暴露

- ```typescript
  defineExpose({
  	changeValue,
      ……
  })
  ```

##### ref（父子通信）

- 获取子组件实例或 DOM 元素

- ```vue
  <Son ref="sonRef" />
  <script setup lang="ts">
      import { ref } from 'vue';
      // 变量名需要和标签中的 ref 名保持一致
  	const sonRef = ref<InstanceType<typeof Son>>(null);
      // 通过 ref 得到子组件对象，调用其暴露的方法
      sonRef.value?.changeValue(num);
  </script>
  ```

##### props（父子通信）

- ```typescript
  // 定义接口，props 类型约束
  interface Test {
  	count: number;
      updateCount(val: number): void;
  }
  // 传递数据的方式与 vue2 同
  // 子组件接收数据的方式需要使用 defineProps 方法，可以在模板直接使用 props 的数据，在 setup 中则需要使用 props.XXX
  const props = defineProps<Test>()
  ```

##### 自定义事件（子传父）

- 在 vue3 中，无论给组件还是 HTML 元素绑定的事件都是原生 DOM 事件（删了 native 修饰符）

- 如果想要给组件绑定自定义事件，则需要在子组件内接收这个自定义事件

- 父组件绑定自定义事件

  - ```vue
    <Son @click="test" />
    <script setup lang="ts">
    	const test = (val: number) => {
    		console.log('test', number)
        }
    </script>
    ```

- 子组件接受自定义事件

  - ```vue
    <button @click="emit('click', 100)">子组件按钮</button>
    <script setup lang="ts">
    	import { defineEmits } from 'vue';
        // 接受自定义事件
        const emit = defineEmits<{
            (event: 'click', val: number): void;
        }>();
    </script>
    ```

##### PubSub（任意组件通信）

- vue3 本身不再提供全局事件总线的 API：$on

- 使用第三方包 pubsub.js

- ```typescript
  onMounted(() => {
      // 订阅
      PubSub.subscribe('count', (_: any, msg: number) => {
          count.value = msg;
      })
  })
  // 发布
  PubSub.publish('count', ++count.value);
  ```

##### v-model（父子通信）

- 相比于 vue2，v-model 在**组件标签**的本质发生变化，不再是 value 和 input 的简写

- 组件标签中 v-model 的本质是 modelValue 和 update:modelValue 简写

  - 父组件给子组件绑定 v-model，简写

    - ```vue
      <Son v-model="count" />
      ```

  - 完整写法：为了实现绑定多个 v-model

    - ```vue
      <Son v-model:modelValue="count" />
      ```

  - 本质写法

    - ```vue
      <Son :modelValue="count" @update:modelValue="count=$event">
      ```

    - 子组件需要接收 props：modelValue 和自定义事件：update:modelValue

- 原生标签中：**并未改变**，动态 value 和原生的 input 监听，TS 写法

  - ```vue
    <input type="text" :value="msg" @input="msg=($event.target as HTMLInputElement).value" />
    ```

##### 删掉了 sync 修饰符

##### $attrs（祖孙通信）

- vue3 中删除了 $listener
- 把所有组件接受的 props 和自定义事件全部放在了 $attr 上（除了已经使用 defineProps 和 defineEmits 接受的）
- 组合式 API：useAttrs

##### $parent（父子通信）

- vue3 中删除了 $children，但是保留了 $parent
- 没有提供组合式 API 写法，还是需要 this.$parent

#### 组合式（composition）API 代替选项式（option）API

- 更好的代码组织和逻辑复用：逻辑更清晰，让特定功能的代码集中抽取到一个函数中进行逻辑复用
- 更好的类型推导

- 常用的组合式 API

  > 启动函数
  >
  > > setup()
  >
  > 响应式核心
  >
  > > ref()
  > >
  > > reactive()
  > >
  > > computed()
  > >
  > > watch()
  >
  > 响应式工具
  >
  > > toRefs()
  >
  > 生命周期钩子
  >
  > > onBeforeUnmount()
  > >
  > > onUnmounted

#### 生命周期

|              选项式 API              |           组合式 API            |
| :----------------------------------: | :-----------------------------: |
|             beforeCreate             | 不需要（直接写到 setup 函数中） |
|               created                | 不需要（直接写到 setup 函数中） |
|             beforeMount              |          onBeforeMount          |
|               mounted                |            onMounted            |
|             beforeUpdate             |         onBeforeUpdate          |
|               updated                |            onUpdated            |
| beforeDestory \| vue3：beforeUnmount |         onBeforeUnmount         |
|     destroyed \| vue3：unmounted     |           onUnmounted           |
|            errorCaptured             |         onErrorCaptured         |
|              activated               |           onActivated           |
|             deactivated              |          onDeactivated          |

- 如果书写选项式 API 的生命周期
  - setup 函数会在 beforeCreate 和 created 之前调用，在 beforeCreate 中可以拿到 setup 中定义的数据，但是还是拿不到 data 配置项中定义的数据
- 如果书写组合式 API 的生命周期
  - 没有 beforeCreate 和 created，setup 在组合式 API 中其实是取代了这两个生命周期函数的过程（数据的注入和劫持，watch 监听，computed、methods 的定义）
- 组合式 API 中，使用 Vue 暴露出来的 onxxx 方法来作为生命周期函数，并接受回调函数作为参数
- 组合式 API 中的生命周期函数可以多次调用

#### 配套库

##### pinia vs vuex

- pinia 没有 mutation，在 action 中可以直接同步更新 state 或异步更新 state
- pinia 中可以包含多个 store，相互独立，不进行合并，没有模块嵌套结构
- 无需手动注册 store，创建出 store 直接可以使用
- 更好地支持 TS

##### vue-router4

- 创建路由器
  - createRouter 代替 new Router
  - createWebHistory 与 createWebHashHistory 代替 history 和 hash
- 获取路由器对象使用 useRouter
- 动态添加路由
  - 4 以前，可以一次添加多个：router.addRoutes(routes)
  - 4 及以后，只能一次添加一个：router.addRoute(route)
- 通配路由的 path 改变
  - 由 path:* 变为 path:/:pathMatch(.*)

### vue3 响应式原理

- vue3 是通过 Proxy（代理）和 Reflect（反射）实现响应式的

  - 通过 Proxy 构造函数（ES6）创建代理对象，从而实现基本操作的拦截和自定义（如属性查找、赋值、枚举、函数调用等13种操作）

    - ```javascript
      const proxy = new Proxy(target, handler)
      // target：代理的目标对象
      // handler：是一个对象，包含了可以监听这个对象的行为函数，有 13 种 trap
      // handler.get
      // handler.set
      ……
      ```

  - Reflect 是 ES6 提供的内置对象，其内部的 13 种静态方法与 13 种 trap 一一对应；在修改 proxy 代理对象时，一般也需要同步到代理的目标对象上，这个同步就是用 Reflect 对应方法来完成的

- 与 vue2 响应式的对比

  - Object.defineProperty 
    - 优点：兼容性好，支持 IE9+（IE OUT）
    - 缺点
      - 无法监测对象属性的新增或删除：$set / $delete
      - 不能监测数组的变化：重写数组的 7 种方法
  - Proxy + Reflect
    - 优点
      - proxy 直接代理的是整个对象而不是代理对象属性
      - 可以监听同级结构下的所有属性变化，包括新增的属性和删除的属性；也可以监听数组的变化
    - 缺点（可忽略）
      - 兼容较差
      - 性能较差

### 几个重要的 API

#### ref

- 接受一个内部值，返回一个响应式的、可更改的 ref 对象，此对象只有一个指向其内部值的属性 value。
- 接收值类型
  - 接收值是非 ref 对象
    - 则实例化 RefImpl 类，得到一个实例化 ref 对象，该对象也是通过 RefImpl 类中 getter 和 setter 来进行数据劫持的（收集依赖和触发依赖更新）
  - 接受值是 ref 对象
    - 直接把这个 ref 对象返回
- ref 对象中的 dep 属性就是收集的依赖；ref 对象中的 value 属性就是 ref 保存的值
- ref 可以实现对象的响应式
  - ref 自身是使用 RefImpl 类的 getter 和 setter 实现数据劫持的，但是并没有遍历对象，所以无法完成对对象的劫持；如果 ref 接受一个对象，则会把这个对象通过 reactive 方法创建一个代理对象实现响应式

#### reactive

- 返回一个对象的响应式代理，实现对象类型的响应式
- 响应式转换是“深层”的：它会影响到所有嵌套的属性
- 响应式原理是：reactive 内部根据接收的对象通过 Proxy 创建了对应的代理对象，代理对象可以监听所有对象的操作（增删改查遍历等），替代并完善了 vue 的 defineProperty 数据劫持方式（所以 vue3 没有 Vue.set 和 Vue.delete 方法）

> ##### ref and reactive
>
> > 作用：ref 和 reactive 都是实现数据响应式的
>
> - ref 既能实现基本类型响应式，又能实现对象类型响应式
> - reactive 由于其内部泛型约束的限制，只能实现对象类型的响应式
>
> > 原理
>
> - reactive 内部根据接收的对象，通过 Proxy 创建对应的代理对象，代理对象可以监听所有对象的操作（增删改查遍历等）
> - ref 是基于 RefImpl 类的 getter 和 setter 实现数据劫持的，但是并没有遍历对象，所以无法完成对对象的劫持；如果 ref 接受一个对象，则会把这个对象借助 reactive 通过 Proxy 创建一个代理对象实现响应式
>
> - 对于对象类型替换值的情况
>
>   - 使用 reactive 创建代理对象需要注意的是
>
>     - 如果直接替换这个值，则不具备任何的响应式
>
>     - 解决方案：可以创建这个数据的时候多嵌套一层结构，不去替换值，而是修改这个对象中某个属性值（不推荐）
>
>   - 使用 ref 创建对象数据，可以直接被替换，并且具有响应式
>     - 因为 ref 对象的数据劫持就是监听 ref 对象的 value 变化，而替换的就是 value
>
> > 更推荐使用 ref 创建响应式数据

#### watch 监听

- 侦听一个或多个响应式数据源，并在数据源变化时调用所给的回调函数
- 参数
  1. 被监听的值，多个被监视对象可以写成数组形式
  2. 数据源变化时被调用的回调函数，参数是 value 的新值或替换的新值
  3. 配置对象（包括 deep、immediate……）
- 监听规律（一般只讲 ref，监听 reactive 和监听 ref 是对象类型的规则相同）
  - ref 实现基本类型值响应式，监听 ref 对象即可，一旦 value 值发生变化，即执行回调函数
  - ref 实现复杂类型值响应式
    - 直接监听 ref 对象：只能监听到这个对象的 value 被替换，对象内部的增删改无法监听到（即默认没有深度监听）
    - 监听 ref 对象的 value 属性（整个代理对象）：无法监听到对象被替换，但是可以监听到对象的增删改（默认深度监听）
    - 监听 ref 对象 value 属性中的某个对象类型属性（代理对象中的某个对象类型属性），无法监听到对象被替换，但是可以监听对象内部的增删改（默认深度监听）
      - 如果想要监听某个属性值是否被替换（无论值是基本类型还是对象类型），watch 的第一个参数需要写成函数写法返回被监听的值（`() => goodInfo.value.skuName`）
- 而 vue2 的 watch 监听
  - 只是监听这个数据是否被替换，如果监听内部数据的需要，直接开启深度监听即可（`deep: true`）

> ## Vue 项目优化

### 代码优化

#### v-for 遍历列表

- 指定非下标的唯一 key，尽量不用 index，如果只用于展示，可以使用
- vue2 中不推荐 v-for 和 v-if 一起使用（先循环遍历渲染，再条件判断，效率低）
  - 对遍历的 item 数据进行限制判断
    - 问题：如果使用 v-if，每个数组元素都会解析指令来判断，效率低
    - 解决：不适用 v-if，使用计算属性，过滤产生一个子数组，效率高
  - 根据外部的数据进行判断
    - 问题：如果在当前标签上用 v-if，执行 n 次，效率低
    - 解决：在父标签上用 v-if，执行 1 次，效率高
  - vue3 中，v-if 和 v-for 可以同时使用，但当在同一个元素上同时使用 v-if 和 v-for 时，v-for 的优先级更高，也就是说 v-for 会先被执行，然后才会根据循环的结果来决定是否渲染该元素。如果循环的结果为空，则该元素**不会被渲染**；否则，该元素会被循环渲染多次
    - 先循环遍历，再条件判断，再渲染，效率高

#### 图片懒加载

- 使用 vue-lazyload 插件

  - 在需要懒加载图片的组件中，将图片的 src 属性替换为 v-lazy 指令

  - 当图片进入可视区域时，vue-lazyload 会自动将 v-lazy 指令的值设置为图片的 src 属性，从而实现图片的懒加载

  - 也可以通过配置项来自定义懒加载的行为

    - ```javascript
      Vue.use(VueLazyload, {
        preLoad: 1.3, // 预加载高度比例
        error: 'dist/error.png', // 图片加载失败时显示的图片
        loading: 'dist/loading.gif', // 图片加载时显示的图片
        attempt: 1 // 图片加载失败时的最大尝试次数
      })
      ```

- UI 组件库，如 element-ui、vant-ui 中的 Image 组件本身就有懒加载的功能

- 原理参考 ECMAScript 其它

#### 路由懒加载

- `const Home = () => import('./pages/Home')`
- `prefetch / preload`
- 具体参考异步组件和路由懒加载

#### 第三方插件的按需引入打包（以 Element UI 为例）

- 需要按需引入的第三方库：element-ui、vant-ui、lodash.js……

- 默认情况下，我们在 Vue 项目中使用 Element UI 时，会将整个 Element UI 库打包到项目中，这样会导致项目打包后的体积变得非常大，影响页面加载速度。为了解决这个问题，我们可以使用按需加载的方式引入 Element UI，只引入项目中需要的组件，从而减小打包后的体积

- 具体实现

  - 需要借助 babel-plugin-component 插件

    - `npm install babel-plugin-component --save-dev`

  - 在 babel 配置文件 .babelrc 中添加该插件

    - ```json
      {
        "presets": [
          ["@babel/preset-env", { "modules": false }],
          "@vue/cli-plugin-babel/preset"
        ],
        "plugins": [
          [
            "component",
            {
              "libraryName": "element-ui",
              "styleLibraryName": "theme-chalk"
            }
          ]
        ]
      }
      ```

  - 在需要使用 Element UI 的组件中，按需引入需要的组件

    - ```javascript
      import { Button, Input } from 'element-ui'
      export default {
        components: {
          'el-button': Button,
          'el-input': Input
        }
      }
      ```

  - 在模板中使用按需引入的组件

    - ```vue
      <template>
        <div>
          <el-button>按钮</el-button>
          <el-input placeholder="请输入内容"></el-input>
        </div>
      </template>
      ```

#### 对高频事件进行节流或防抖处理

- 项目中一般使用第三方封装好的 JS 库即可，如 lodash.js
- 节流场景
  - 鼠标移动切换显示子分类列表
  - 参考节流 / 防抖
- 防抖场景
  - 输入关键词实现显示关键字列表
  - 浏览器窗口大小的频繁拖拽（resize）
  - 参考节流 / 防抖

#### 及时销毁事件监听

- vue 组件销毁时，实例的所有指令都被解绑，所有的事件监听器被移除，所有的子实例也都会被销毁；而单独添加的监听事件是不会移除的，需要手动移除事件的监听，以免造成内存泄漏

- ```javascript
  mounted() {
      // 原生事件监听
  	document.addEventListener('scroll', this.onScroll, false);
      // 全局事件总线
  	this.$bus.$on('xxx', this.fn);
  },
  beforeDestory() {
  	document.removeEventListener('scroll', this.onScroll, false);
  	this.$bus.$off('xxx');
  }
  ```

#### 大数据优化：冻结响应式数据

- 如果当前组件只是为了单纯展示时，拿到数据后使用 `Object.freeze()` 将数据冻结，这样数据就无法进行响应式变化 

- ```javascript
  export default {
  	data: () => ({
  		users: [] // {id, name, age,...}
  	}),
  	async created() {
  		const users = await axios.get('/api/users');
  		// this.users = users // 每个 user 对象中的属性都添加了 setter 监视
  		this.users = Object.freeze(users); // 这样数组内部就没有做数据劫持处理，效率更高
  	}
  }
  ```

- 问题：只适用于展示型组件，而且所有数据都会生成真实 DOM

#### 大数据优化：虚拟列表

- 问题：当组件处于非常长的列表时，数据过多导致 DOM 元素同样多，导致卡顿
- 解决：使用虚拟列表，只渲染窗口可视区的 DOM
- 实现思路
  - 虚拟列表可以分为两个部分：可视区域和数据源
    - 可视区域是指用户可以看到的部分，它通常是一个固定大小的容器，例如一个固定高度的 div 元素
    - 数据源是指整个列表的数据，它通常是一个数组，例如一个装有一千条数据的数组
  - 为了实现虚拟列表，我们需要根据可视区域的大小和位置，计算出当前可视区域内应该显示哪些数据
  - 最后通过监听可视区域的滚动事件，根据当前可视区域的滚动位置计算出当前可视区域内应该显示哪些数据，并将这些数据保存到 data 数组中
- 项目中一般使用第三方插件
  - 如 vue-virtual-scroll-list

### webpack 配置优化

#### 兼容性处理

- JavaScript

  - babel-loader

    - babel 插件包是能够编译某些 ES6 新语法的包

    - @babel/preset-env：babel 环境预设包，即包含多个 babel 插件包的集合包，只能编译简单语法

    - @babel/polyfill：可以做复杂语法的兼容，问题是体积偏大

    - @babel/core：babel 核心语法包，其中配置项 `"useBuiltIns": "usage"` 可以实现按需打包，解决 @babel/polyfill 包体积偏大问题

    - `.babelrc` 配置文件

      - ```javascript
        module.exports = {
            "presets": [
              [
                "@babel/preset-env",
                {
                  "targets": {
                    "edge": "17",
                    "firefox": "60",
                    "chrome": "67",
                    "safari": "11.1"
                  },
                  "useBuiltIns": "usage",  // 按需打包，根据以上浏览器设置兼容性
                  "corejs": "3.6.5"  // babel 核心库版本
                  ……
                }
                ……
              ]
            ]
        }
        ```

    - 注意

      - const / let / 对象简写 / 箭头函数等，有对应的 ES5 语法

      - Promise / Map / Set 等，没有对应的 ES5 语法，需要额外安装插件

        - 比如 `@babel/plugin-transform-classes` 用来处理类，`@babel/plugin-transform-regenerator` 用来处理生成器函数，`@babel/plugin-transform-arrow-functions` 用来处理箭头函数等

        - 对于 Promise / Map / Set 等语法，一般采用安装 `@babel/plugin-transform-runtime`，`@babel/runtime`，前一个把新语法转换成使用 `@babel/runtime` 的工具函数

          - ```javascript
            // 例如
            var _promise = require("@babel/runtime-corejs3/core-js-stable/promise");
            var _map = require("@babel/runtime-corejs3/core-js-stable/map");
            var _set = require("@babel/runtime-corejs3/core-js-stable/set");
            ```

- CSS

  - 使用 `postcss-loader` 可以对 CSS 文件进行预处理，例如自动添加浏览器前缀、压缩 CSS、转换 CSS 新特性等，其内部用到相关插件

    - 如 `autoprefixer` 插件用于自动添加浏览器前缀，`cssnano` 插件用于压缩 CSS

    - ```javascript
      module.exports = {
        module: {
          rules: [
            {
              test: /\.css$/,
              use: [
                'style-loader',
                'css-loader',
                {
                  loader: 'postcss-loader',
                  options: {
                    plugins: [
                      require('autoprefixer'),
                      require('cssnano')({
                        // 默认压缩方式
                        preset: 'default'
                      })
                    ]
                  }
                }
              ]
            }
          ]
        }
      }
      ```

    - 在 package.json 中可以使用 browserslist 字段来指示 postcss-loader 的兼容性

      - ```json
        {
          "browserslist": [
            "> 1%",
            "last 2 versions",
            "not ie <= 8"
          ]
        }
        ```

      - 全球使用率超过 1%，最近两个版本浏览器，但是不兼容 IE8 及以下版本

- 注意：在 Vue CLI 3.x 及以上版本中，默认会处理以上兼容性问题，因此只需要配置 browserslist 即可

#### 对第三方包的拆分打包与压缩

- 作用
  - 抽取公共代码
  - 拆分成多个文件，减少单个文件体积，避免单次请求时间过长
- 在 Vue CLI 3.x 及以上版本中，默认会对第三方模块进行拆分打包和压缩，应用层无需额外配置

#### 资源预加载

- 让资源提前加载
  - preload：与主打包文件并行加载（有一定竞争）
  - prefetch：在主打包文件加载完成后，空闲再去加载
  - webpack 实现预加载
    - `import(/* webpackPrefetch: true */ './myComponent.js');`
    - `import(/* webpackPreload: true */ './myComponent.js');`
    - 另外，也可以使用 link 标签实现 preload
      - `<link rel="preload" href="./myComponent.js" as="script">`
    - 兼容性较差，不推荐
  - vue 脚手架项目已经默认资源预加载，基于 preload-webpack-plugin 插件
    - preload：对同步模块包
    - prefetch：对异步模块包

#### vue3 中实现 Tree Shaking

- 效果：打包时 ”摇掉模块” 中没有被使用的代码
- 条件：必须是 ES6 模块化导出且进行代码压缩时

#### 文件名 Hash 化

- 打包后文件名 hash 化的主要原因是为了解决浏览器缓存问题
- 当我们使用Webpack等工具对项目进行打包时，生成的文件名通常都是固定的，如果我们修改了某个文件，重新打包后生成的文件名仍然是一样的，浏览器会认为这是同一个文件，从而使用缓存中的旧文件，导致页面出现问题
- 为了避免这个问题，我们可以使用文件名 hash 化的方式，每次修改文件后，生成的文件名都会发生变化，从而让浏览器重新请求最新文件
- vue 中，默认文件名 Hash 化

#### 生产环境下不生产 SourceMap

- SourceMap：一种用于调试 JavaScript、CSS 和其他前端资源的技术。当前端代码经过构建（如压缩、合并等）后，通常会难以调试，因为这样的代码与源代码之间的对应关系已经失去了。SourceMap 解决了这个问题，它提供了一种将构建后的代码与源代码之间建立映射的方式
- 为了减少打包文件，生产环境下不生产 SourceMap
  - `productionSourceMap: false`
  - vue 生产环境下，默认不会生成 SourceMap 文件

### web 技术层面优化

#### Gzip 压缩

- 对打包文件开启 gzip 压缩

  - a.min.js `==>` a.min.js.gzip
  - 浏览器得到后面的文件，会自动解压

- vue 默认不会开启 gzip 压缩

  - 安装 compression-webpack-plugin 插件

  - vue.config.js 中配置

    - ```javascript
      const CompressionWebpackPlugin = require('compression-webpack-plugin')
      
      module.exports = {
        // ...其他配置
        configureWebpack: {
          plugins: [
            new CompressionWebpackPlugin({
              // 算法指定为 gzip
              algorithm: 'gzip',
              // 指定压缩的文件格式
              test: /\.(js|css)$/,
              // 指定了文件大小大于等于 10KB 时才进行压缩
              threshold: 10240,
              // 指定压缩比例达到 0.8 时才进行压缩
              minRatio: 0.8,
              // 不删除原始文件
              deleteOriginalAssets: false
            })
          ]
        }
      }
      ```

- 启用 gzip 压缩会增加构建时间和 CPU 负载，但可以显著减小静态资源的文件大小，从而提高页面加载速度

#### 静态资源使用 CDN 引入

- 浏览器从服务器上下载 CSS、JS 和图片等文件时都要和服务器连接，而大部分服务器的带宽有限，如果超过限制，网页响应速度就很慢
- CDN 可以通过不同的域名来加载文件，从而使下载文件的并发连接数大大增加，且 CDN 具有更好的可用性,更低的网络延迟和丢包率

> ## 数据可视化

### 常见应用层数据可视化库

- D3.js，目前 web 端评价最高的 JS 可视化工具库，入手较难
- Highcharts.js，国外的前端数据可视化库，非商用免费，被许多国外大公司使用
- Echarts.js，百度的一个开源 JS 数据可视化库
- AntV，蚂蚁金服全新一代数据可视化解决方案
- ……

### 使用场景

- 通用图表
- 移动端图表
- 大屏可视化
- 图编辑 / 图分析
- 地理可视化
- ……

### Canvas

#### canvas

- canvas 是 HTML5 的新特性，它允许我们使用 canvas 元素在网页上通过 JavaScript 绘制图像

#### 基本使用

- canvas 标签

  - `<canvas>` 标签只是图形容器，相当于一个画布，canvas 元素本身是没有绘图能力的
  - 所有的绘制工作必须在 JavaScript 内部完成，相当于使用画笔在画布上画画
  - 必须指定宽高

- `getContext()`

  - 获取 canvas 上下文对象 context

  - context 是一个封装了很多绘图功能的对象，我们在页面中创建一个 canvas 标签之后，首先要使用 `getContext()` 获取 canvas 的上下文环境，目前 `getContext()` 的参数只有 2d，暂时还不支持 3d 

    `getContext("2d")` 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法

- 查询文档

  - 绘制线段 / 矩形 / 圆形 / 文字
  - 清除路径 / 矩形区域

### Svg

#### svg

- svg（scalable vector graphics），可缩放矢量图形，一种基于 XML 的图像文件格式

#### 基本使用

- > `<svg>`：最外层标签
  >
  > `<line>`：直线
  >
  > `<polyline>`：折线
  >
  > `<rect>`：矩形
  >
  > `<circle>`：圆形
  >
  > `<ellipse>`：椭圆
  >
  > `<polygon>`：多边形
  >
  > `<path>`：通过指定点以及点和点之间的线来创建任意形状

- 具体配置通过标签属性的形式

### Echarts

#### echarts

- 基于 HTML5 Canvas 技术实现数据可视化
- 基本的 3 种图表类型
  - 折线图（line）
  - 柱状图（bar）
  - 饼状图（pie）


#### 基本使用

  1. 下载并引入 echarts.js
  2. 准备一个具备大小的 DOM 容器
  3. 初始化 echarts 实例对象（init）
  4. 指定配置项和数据（option）
  5. 将配置项设置给 echarts 实例对象（setOption）

#### 常见配置项

> title：标题组件
>
> legend：图例组件
>
> tooltip：提示框组件
>
> toolbox：工具栏
>
> grid：直角坐标系内绘图网格
>
> color：调色盘颜色列表
>
> xAxis：直角坐标系 grid 中的 x 轴（必需）
>
> yAxis：直角坐标系 grid 中的 y 轴（必需）
>
> series：系列列表，每个系列通过 type 决定自己的图表类型，类型数组 / 对象（必需）

#### vue 项目中使用 echarts

##### 直接使用 echarts.js

- ```java
  // plugins/echarts.js
  import Vue from 'vue';
  import * as echarts from 'echarts';
  // 将 echarts 放在 vue 的原型对象上
  Vue.prototype.$echarts = echarts;
  ```

- ```javascript
  // stylus/echarts.css
  // 重置 echarts 宽高
  .echarts {
  	width: 100%;
      height: 100%;
  }
  ```

- ```javascript
  // main.js 中引入
  import '@/plugins/echarts';
  // 样式后引入
  import '@/stylus/echarts.css';
  ```

##### 使用 vue-echarts

- vue-echarts 最新版本中，是组合式 api，如果在 vue2 项目中使用，必须下载 @vue/composition-api

- ```javascript
  // plugins/echarts.js
  import Vue from 'vue';
  import Echarts from 'vue-echarts';
  // 全局注册 echarts 组件
  Vue.component('v-chart',Echarts);
  ```

- 使用时直接以标签形式，配置等通过属性控制

##### 常见问题

- 如何动态显示图表
  - echarts
    - 在 mounted 中设置配置项（option）
    - 监视数据改变（watch），数据改变时，重新设置配置项（option）

  - vue-echarts
    - 只需要给 v-chart 指定动态 option 属性，
    - 通过调用 getOption（自定义方法） 得到配置对象
- 动态显示图表不能正常显示
  - 原因：初始 data 数据是 undefined
  - 解决：给 data 对应的数据一个空数组作为默认值
- 图表显示后不能自适应大小
  - 原因：浏览器窗口大小发生改变时，且父元素大小改变时，图表没有重新绘制
  - 解决：
    - echarts：给 window 绑定 resize 监听，在回调中调用 chart 对象的 resize 方法
    - vue-charts：只需要指定 autoresize 属性即可（boolean）
- tooltip 提示框有时会自动隐藏超出容器区域的部分
  - 解决一：
    - `confine: true`：将提示框限制在容器区域内
    - 问题：遮挡比较明显，用户体验较差
  - 解决二：
    - `position(point,params,dom,rect,size)` 
    - 通过条件判断，返回位置坐标，如 [x,-40]

> ## 微信小程序
-  参考精讲 / 面试题
- 参考微信小程序面试题

> ## 移动端
- 参考面试题

> ## 附加

### Promise

#### promise

- Promise 是 ES6 引入的异步编程的新解决方案
- 语法上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果（状态和返回值）
- 目的是为了解决回调地狱问题，并且 promise 的微任务执行效率更高

#### promise 对象三种状态（PromiseState）与结果值（PromiseResult）

- `pending`，等待状态，默认状态，结果值：`undefined`

  - ```javascript
    let p = new Promise((resolve,reject)=>{
    });
    console.log(p);
    ```

- `fulfilled`，成功状态，也称 `resolved`，结果值：调用 `resolve` 时传递的参数

  - ```javascript
    let p = new Promise((resolve,reject)=>{
        resolve('success');
    });
    console.log(p);
    ```

- `rejected`，失败状态，结果值：调用 `reject` 时传递的参数

  - ```javascript
    let p = new Promise((resolve,reject)=>{
        reject('error');
    });
    console.log(p);
    ```

#### promise 里的 then 方法：两种回调

- `onResolved`：会在调用 `resolve` 的时候执行 `onResolved` 回调函数

  - ```javascript
    let onResolved = function (res) { // 在 promise 内部调用
        console.log(res);
    }
    p.then(onResolved);
    ```

- `onRejected`： 会在调用 `reject` 的时候执行 `onRejected` 回调函数

  - ```javascript
    let onResolved = function(res){  // 在 promise 内部调用
        console.log(res)
    }
    let onRejected = function(err){
        console.log(err)
    }
    p.then(onResolved,onRejected);
    ```

#### then 方法的返回值

- `onResolved` 返回值
  - 没有返回值：得到一个 `fulfilled` 状态的 `promise`，且 `promiseResult` 是 `undefined`
  - 返回普通值：得到一个 `fulfilled` 状态的 `promise`，且 `promiseResult` 是 返回值
  - 返回 `promise` 对象：得到这个返回 `promise` 对象（成功 | 失败 | pending）
  - 抛出错误（throw new Error('错误')）：得到一个失败状态的 `promise` 对象，且 `promiseResult` 是错误的内容
- `onRejected` 返回值
  - 同上
  - 注意
    - 如果在 `onRejected` 里返还，得到一个成功状态的 `promise` 对象，那么就会进入下一个 `then` 的成功回调
    - 如果需要把失败的状态传递下去，需要不停的返还失败的 `promise` 对象

#### promisify

- 把 `node.js` 中的异步操作变成 `promise` 调用形式

- ```javascript
  let p = promisify(fs.readFile)(path.join(__dirname, '/dataTest.txt'));
  p.then(
    (dataString) => {
      console.log(dataString.toString);
    },
    (err) => {
      console.log(err);
    }
  );
  ```

- ```javascript
  // 自己封装一个 promisify
  function myPromisify(func) {
    return function (...args) {
      return new Promise((resolve, reject) => {
        func(...args, (err, dataString) => {
          if (err) {
            reject(err);
            return console.log(err);
          }
          // 判断 dataString 有无，如果有返回去，没有即不跟参
          if (typeof dataString !== undefined) {
            resolve(dataString);
          } else {
            resolve();
          }
        });
      });
    };
  }
  ```

#### promise 相关方法

##### 实例方法

- `catch`
  - catch 会捕捉 promise 对象链式上的错误
  
  - 减少了没必要的失败回调
  
  - 本质：then
  
    - ```javascript
      catch(onRejected) {
      	return then(value => value, onRejected);
      }
      ```
  
    - catch 穿透，catch 接收到 promise 后，不做任何处理，再返回新的 promise
  
      - 调用 catch 的 promise 是一个成功的，即 catch 的参数没有处理 promise 的回调函数，那 catch 返回的 promise 也是成功的，且 value 是成功 promise 的 value
  
- `finally`
  
  - 表示 promise 执行完毕，无论 promise 执行成功了，还是执行失败了，只要 promise 执行完了就会调用 finally
  - pending 状态不会执行

##### 静态方法

- `resolve`：快速创建一个成功状态的 promise 对象
- `reject`：快速创建一个失败状态的 promise 对象

- `race`

  - `Promise.race([p1,p2,...])`：执行多个 promise 对象 ，获取执行最快的 promise 的结果

  - ```javascript
    // 自己封装一个 Promise.race p 是 promise对象
    class myPromise {
      static race(arr) {
        return new Promise((resolve, reject) => {
          arr.forEach((item) => {
            // item.then(
            //   (val) => {
            //     resolve(val);
            //   },
            //   (err) => {
            //     reject(err);
            //   }
            // );
            // 第二种简写
            item.then(resolve, reject);
          });
        });
      }
    }
    
    // 执行静态方法
    myPromise.race([p1, p2, p3]).then(
      (res) => {
        console.log(res);
      },
      (err) => {
        console.log(err);
      }
    );
    ```

- `all`

  - `Promise.all([p1,p2,...])`：可以执行多个 promise 对象，获取 promise 对象的结果

  - 注意

    - `all` 是同时执行 promise 对象
    - `all` 收集的结果
      - 只有当所有接收的 promise 都成功了，返回的 promise 才成功，且成功的 value 为所有成功 promise 的 value 组成的数组
      - 一旦有一个失败了，返回的 promise 就失败了，且失败的 reason 就是失败 promise 的 reason

  - ```javascript
    // 自己封装一个 Promise.all p 是 promise 对象
    class myPromise {
      static all(arr) {
        return new Promise((resolve, reject) => {
          let count = 0;
          let resArr = [];
          arr.forEach((item) => {
            item.then(
              (res) => {
                resArr.push(res);
                count++;
                if (count === arr.length) {
                  resolve(resArr);
                }
              },
              (err) => {
                reject(err);
              }
            );
          });
        });
      }
    }
    
    // 执行静态方法
    myPromise.all([p1, p2, p3]).then(
      (res) => {
        console.log(res);
      },
      (err) => {
        console.log(err);
      }
    );
    ```

- `allSettle`

  - `Promise.allSettle([p1,p2,...])`：ES2020 出现的方法，弥补了 `all` 对于错误处理的能力，同时执行多个对象

  - ```javascript
    // 自己封装一个 Promise.allSettled p 是 promise 对象
    class myPromise {
      static allSettled(arr) {
        return new Promise((resolve) => {
          // 设置计数器和固定长度的空数组
          let count = 0;
          let resArr = new Array(arr.length);
          arr.forEach((item, key) => {
            item.then(
              (res) => {
                // 成功
                // 创建带有状态和值的对象
                let obj = {
                  status: 'filfulled',
                  value: res,
                };
                // 通过 key 对应到空数组中
                resArr[key] = obj;
                // 计数器加一
                count++;
                // 抛出条件
                if (count === arr.length) {
                  resolve(resArr);
                }
              },
              (err) => {
                // 失败
                // 创建带有状态和值的对象
                let obj = {
                  status: 'rejected',
                  value: err,
                };
                // 通过 key 对应到空数组中
                resArr[key] = obj;
                // 计数器加一
                count++;
                // 抛出条件
                if (count === arr.length) {
                  resolve(resArr);
                }
              }
            );
          });
        });
      }
    }
    
    // 执行静态方法
    myPromise.allSettled([p1, p2, p3]).then((res) => {
      console.log(res);
    });
    ```

#### 同步与异步，宏任务与微任务

- 同步先执行，异步任务会进入任务队列
- 微任务：为了提高 js 的响应精度，提高了 js 执行的颗粒度
  - 微任务可以插队，微任务较少，如 `promise.then()`，`MutationObserser` 等
  - 宏任务需要排队，大部分 js 任务都是宏任务，如事件回调，定时器，AJAX 请求，资源加载，主线程（整体的 script）等
- 微任务和宏任务的执行顺序
  - 先执行宏任务，在执行微任务
  - 每个宏任务执行完毕会进入微任务检查点，检查该宏任务下的微任务队列，如果为空就继续执行下一个宏任务，如果不为空就执行完毕微任务队列：
    - 【宏 1[微任务 1,微任务 2..]】
    - 【宏 2[微任务 1,微任务 2..]】
    - 【宏 3[微任务 1,微任务 2..]】
    - 【宏 4[微任务 1,微任务 2..]】
    - 【宏 5[微任务 1,微任务 2..]】
  - 宏任务里有一个任务是 script 主线程任务 （会执行所有的同步代码）；广义上说，同步代码也是异步代码

#### Promise 终极解决方案

- `async await` 是 `generator` 的语法糖，专门用来解决异步编程问题，是终极解决方案，用同步表达异步操作；`async` 是用来声明某个函数是异步函数（认为是 `generator` 中的 \*），`await` 是等待一个异步的执行（相当于是 `yield`）

- 目的

  - 消灭回调函数，简化 promise 的使用，不用再使用 then / catch 来指定回调函数

- ```javascript
  // fn1 fn2 fn3 均返回一个 promise
  async function fn() {
      // 调用依次执行，写成同步的形式，实际是异步操作
      // try catch 用来捕捉错误，catch 区别于 promise 中的 catch，参数不同
      try {
          let res1 = await fn1();
          // 接收的值为 promise
          console.log(res1);
          let res2 = await fn2();
          console.log(res2);
          let res3 = await fn3();
          console.log(res3);
      }catch(err) {
  		console.log(err);
      }
  }
  // 可以通过立即执行函数，以免忘记调用
  (async function () {
    let res = await fn1();
    console.log(res);
  })();
  ```

- `async` 函数返回值

  - 返回值是 promise
  - 默认返回成功的 promise 对象，值为函数的返回值（函数没有 return 时，返回 undefined）
  - 当 async 函数内部出现错误的时候，则 async 函数返回失败的 promise 对象，值为错误信息
  - 当 async 函数内的 await 等到了一个失败的 promise 对象时，则 async 函数直接返回一个失败的 promise 对象，值为错误信息

- `await` 返回值

  - await 右侧的表达式一般为 promise 对象，但也可以是其它的值
  - 如果表达式是 promise 对象，await 返回的是 promise 成功的值
    - 如果表达式是其它值，直接将此值作为 await 的返回值，但是 async 函数会通过 Promise.resolve 把这个非 promise 对象包装成 promise 对象

  - 注意：如果 await 的 promise 失败了，就会抛出错误，需要通过 try...catch 捕获处理

- 注意事项

  - `await` 必须写在 `async` 函数中，`async` 函数中可以没有 `await`

  - `await` 会等待 `resolve` 和 `reject` 之后执行的代码

  - `await` 之后是异步代码，之前是同步代码；`await` 模拟 `then` 的执行，所以 `await` 之后是微任务

  - `async` 函数的返回值和 `then` 的返回值一致

  - `await` 不能出现普通函数中

  - `async` 和 `await` 不能出现在嵌套函数中

    - ```javascript
      (async function fn(){
        let arr=[1,2,3];
        arr.forEach(item=>{
          await item; // 错误的，不能出现在嵌套函数中
          // 如 await item; --> await Promise.resolve(1);
        })
      }())
      ```
    
  - `await` 只能等待一个 `async` 函数的内容

    - ```javascript
      // 此时的 arrFn 是返回值为 promise 的函数数组
      
      // 注意此处是同时执行，三个 async 和 await
      arrFn.forEach(async (item) => {
        let res = await item();
        console.log(res);
      });
      
      // 通过 for 循环，依次执行
      (async function fn() {
        for (let i = 0; i < arrFn.length; i++) {
          let res = await arrFn[i]();
          console.log(res);
        }
      })();
      
      // 正常不用循环
      (async function f() {
        let res1 = await arr[0]();
        console.log(res1);
        let res2 = await arr[1]();
        console.log(res2);
        let res3 = await arr[2]();
        console.log(res3);
      })();
      ```

#### Promise 源码解析*

#### 自行封装一个 Promise*

- 三种状态
- 模拟 then，catch 方法
- Promise 微任务和宏任务
- 相关 静态和实例 方法
- ……

#### 其他

- 异步方法一般参数不写回调函数，返回 promise；如果写回调函数，则一般不会返回 promise

### Axios

#### 总述

- Axios：[æk'siəʊ:s]
- Axios：最主流的 ajax 请求库，发送 ajax，底层也是 XMLHttpRequest 对象
  - 服务端 和 客户端 均支持，后端利用 http 模块
  - **基于 Promise**
  - vue / react 官方均推荐使用 Axios 发送 AJAX 请求
- 默认配置：统一配置各种参数
- 拦截器：拦截所有 ajax 请求和返还
  - 请求 —— 请求拦截器 —— ajax1，ajax2，ajax3 ——返还拦截器 —— 返还
- 创建多个 ajax 实例：
  - 分类多个 ajax
  - 如：100 个 ajax 分成不同类型设置共同配置
- 支持 取消请求 / 批量发送多个请求
- 支持 请求 / 响应的数据转换
- ……

#### 基本使用

- `get` 请求

  - ```javascript
    axios({
      url: '/getAxios',
      method: 'get',
      // get 请求使用 params 配置数据，地址栏带参，querystring
      params: {
        x: 1,
        y: 2,
      },
    }).then((res) => {
      // res 内部还有属性，需要解构一下
      let { data } = res;
      console.log(data);
    });
    ```

- `post` 请求

  - ```javascript
    axios({
      url: '/postAxios',
      method: 'post',
      // post 请求使用 data 配置数据，请求体带参
      // 头部 axios 会根据数据类型自动设置
      //  1. 给的是 对象，那么 axios 默认设置头部为 json
      //  2. 给的是 querystring，那么 axios 会自动设置成表单的头部
      //  3. 文本也可以，不常用
      data: {
        x: 1,
        y: 2,
      },
      // 或者 data 以 querystring 形式
      // data: x=1&y=2,
    }).then((res) => {
      let { data } = res;
      console.log(res);
      box.innerHTML = data.info;
    });
    ```

- 基于 Promise，所以可以使用 async await

  - ```javascript
    async function() {
      let { data } = await axios({
          url: '/getAxios',
          method: 'get',
          // get 请求使用 params 配置数据，地址栏带参
          params: {
            x: 1,
            y: 2,
          },
      });
      console.log(data);
    }
    ```

- 别名

  - ```html
    <button>get</button>
    <button>post</button>
    <button>delete</button>
    <button>put</button>
    <div class="box"></div>
    <script>
      let btns = document.querySelectorAll('button');
      let box = document.querySelector('.box');
    </script>
    ```

  - `get` 请求，获取

    - ```javascript
      // get，两个参数 url,配置项，传递的参数在 url 后添加，也可以 params 在配置项中的形式表示
      btns[0].onclick = async function () {
        let { data } = await axios.get('/getAxios?id=1', {
          params: { x: 33, y: 22 },
          timeout: 2000,
        });
        box.innerHTML = data.info;
        console.log(data.info);
      };
      ```

  - `post` 请求，添加

    - ```javascript
      // post，三个参数 url,data,配置项，传递的参数在请求体 data 中
      btns[1].onclick = async function () {
        let { data } = await axios.post(
          '/postAxios',
          { x: 10, y: 11 },
          { timeout: 2000 }
        );
        box.innerHTML = data.info;
        console.log(data.info);
      };
      ```

  - `delete` 请求，删除

    - ```javascript
      // delete，两个参数 url,配置项，传递的参数在 url 后添加
      // 传递的参数也可以通过请求体传递，不过需要在配置项中以 data 的形式表示
      btns[2].onclick = async function () {
        let { data } = await axios.delete('/deleteAxios?id=1', {
          data: {
            a: 2,
            b: 4,
          },
          timeout: 2000,
        });
        box.innerHTML = data.info;
        console.log(data.info);
      };
      ```
  
  - `put` 请求，全局更新
  
    - ```javascript
      // put，三个参数 url,data,配置项，请求路径需要找到对应的更新路径，一般以 id 形式
      // 传递的参数在请求体 data 中，一般为更新后的数据
      btns[3].onclick = async function () {
        let { data } = await axios.put(
          '/putAxios/id',
          {
            a: 40,
            b: 80,
          },
          {
            timeout: 2000,
          }
        );
        box.innerHTML = data.info;
        console.log(data.info);
      };
      ```
    
  - `patch` 请求，局部更新
  
    - ```javascript
      // put，三个参数 url,data,配置项，请求路径需要找到对应的更新路径，一般以 id 形式
      // 传递的参数在请求体 data 中，一般为更新后的数据
      btns[4].onclick = async function () {
        let { data } = await axios.patch(
          '/patchAxios/id',
          {
            a: 50,
            b: 100,
          },
          {
            timeout: 2000,
          }
        );
        box.innerHTML = data.info;
        console.log(data.info);
      };
      ```

#### 配置项

- 配置项形式
  - 通用形式：`axios({配置项})`
  - 别名形式：`axios.get('url',{配置项})`、`axios.post('url',{data},{配置项})`
  
- 配置项
  - 常用
  
    - ```javascript
      axios({
      	// 请求服务器的地址
      	url: '/getAxios',
      
          // 基础路径，baseURL 将自动加到 url 前面，除非 url 是一个绝对路径
      	baseURL: 'http://127.0.0.1:9090',
          
      	// 请求方法，默认 get
      	method: 'get',
          
          // 自定义请求头
      	headers: { 'X-Request-With': 'XMLHttpRequest' },
      
      	// URL 参数
      	// 必须是一个简单对象 或 URLSearchParams 对象
      	params: {
      	  id: 5096,
      	},
          
      	// 作为请求体被发送的数据
      	// 只能用于 post put patch 等含有 data 请求方法
      	// 在没有设置 transformRequest 时，则必须是以下类型之一：
      	// string，plain object，ArrayBuffer，ArrayBufferView，URLSearchParams
      	// 浏览器专属：FormData，File，Blob
      	// Node专属：Stream，Buffer
      	data: {
      	  test: 'test',
      	},
      	// data 其他形式，只有 value 会被发送，key 不会
      	data: 'name=Chan&age=18',
      
      	// 对发送的 data 进行任意转换处理，只能用于 post put patch 等含有 data 请求方法
          // 数组中最后一个函数必须返回字符串、Buffer 实例，ArrayBuffer，FormData，或 Stream
          // 也可以修改请求头
      	TransformRequest: [
      	  function (data, headers) {
      	    // 对发送的 data 进行任意转换处理
      	    console.log(data);
      	    // 返还出去
      	    return data;
      	  },
      	],
      	// 在传递给 then / catch 前，允许修改响应数据
      	TransformResponse: [
      	  function (data) {
      	    console.log('返还的数据', data);
      	    return JSON.parse(data);
      	  },
      	],
          
      	// 表示浏览器将要响应的数据类型，默认 json
      	// 包括：'arraybuffer','document','json','text','stream'
      	// 浏览器专属：'blob
      	responseType: 'json',
          
      	// 指定请求超时的毫秒数，超过时间则请求中断，默认 0
      	timeout: 2000,
          
      	// 取消请求
      	cancelToken: new CancelToken(function (cancel) {}),
          
      	// 代理服务器
      	proxy: {
      	  protocol: 'https',
      	  host: '127.0.0.1',
      	  port: 9000,
      	  auth: {
      	    username: 'Chan',
      	    password: '123cxp',
      	  },
      	},
      });
      ```
  
  - 参考
  
    - ```javascript
      axios({
      	// 可选方法，序列化 params，参考
      	paramsSerializer: function (params) {
      	  return Qs.stringify(params, { arrayFormat: 'brackets' });
      	},
          
      	// 跨域请求时，是否需要凭证，默认 false
      	// 需要后端 CORS 头部也要进行相应配置
      	withCredentials: false,
      
      	// 需要账号密码的 HTTP 请求进行相应配置
      	auth: {
      	  username: 'Chan',
      	  password: '123cxp',
      	},
          
      	// 允许为上传处理进度事件，浏览器专属
      	onUploadProgress: function (progressEvent) {
      	  // 处理原生进度事件
      	},
      	// 允许为下载处理进度事件，浏览器专属
      	onDownloadProgress: function (progressEvent) {
      	  // 处理原生进度事件
      	},
          
      	// 定义了对于给定的 HTTP 状态码是 resolve 还是 reject promise
      	// 如果返回 true（或 null / undefined）
      	// 则 promise 将会 resolved（或 rejected）
      	validateStatus: function (status) {
      	  return status >= 200 && status < 300; // 默认值
      	},
          
          // 表示用于解码响应的编码（node.js 专属），默认 utf8
          // 注意：忽略 responseType 的值为 stream，或者是客户端请求
          responseEncoding: 'utf8',
          
      	// 适配器，服务端 node.js 中使用的
      	// 允许自定义处理请求，这使测试更加容易
      	// 返回一个 promise 并提供一个有效的响应
      	adapter: function (config) {},
      
      	// 定义 node.js 中允许的 HTTP 响应内容的最大字节数
      	maxContentLength: 2000,
      
      	// 定义 node.js 中允许的 HTTP 请求内容的最大字节数
      	maxBodyLength: 2000,
      
      	// 定义 node.js 中要遵循的最大重定向数，默认 5
      	maxRedirects: 5,
      
      	// 定义 node.js 中使用的 UNIX 套接字
      	socketPath: null,
      
      	// 定义 node.js 中是否自动压缩（.zip），默认 true
      	decompress: true,
      
      	// 定义 node.js 中 http 和 https 的请求与响应代理，keepAlive 默认 false
      	httpAgent: new http.Agent({ keepAlive: true }),
      	httpsAgent: new https.Agent({ keepAlive: true }),
          
      	// 与网络安全相关
      	// xsrfCookieName 是 xsrf token 的值，被用作 cookie 的名称
      	xsrfCookieName: 'XSRF-TOKEN', // 默认值
      	// xsrfHeaderName 是带有 xsrf token 的值，被用作 http 请求头名称
      	xsrfHeaderName: 'X-XSRF-TOKEN', // 默认值
      });
      ```
  
- 默认配置与实例化

  - 默认配置

    - ```javascript
      axios.defaults.timeout = 2000;
      axios.defaults.baseURL = '/api';
      // 项目上线后，没有跨域问题，因为会把前端服务器数据，整合到后端中，所以 baseURL 拼接也不需要
      ……
      ```

  - 实例化

    - ```javascript
      // 创建实例对象，并统一配置
      let instance1 = axios.create({
          timeout: 2000;
      });
      let instance2 = axios.create({
          timeout: 1000;
          baseURL: '/api';
      })
      // 也可以默认配置
      instance1.defaults.timeout = 2000;
      instance2.defaults.timeout = 1000;
      instance2.defaults.baseURL = '/api';
      
      // 发送请求，以实例化形式分类发送
      btn[0].onclick = async function () {
        let { data } = await instance1({
          url: '/getAxios',
          method: 'get',
          params: {
            a: 100,
            b: 200,
          },
        });
        console.log(data);
      };
      
      btn[1].onclick = async function () {
        let { data } = await instance2({
          url: '/postAxios',
          method: 'post',
          data: {
            a: 300,
            b: 400,
          },
        });
      ```


#### 执行多个请求与取消请求

- 同时发送多个请求（并发）

  - ```javascript
    axios.all([axios.get('geturl'),axios.post('posturl')]).then(res=>{
        console.log(res);
        // 返回值也是数组形式，解构
        let [dataget,datapost] = res;
        console.log(dataget.data);
    })
    ```

- 取消请求

  - ```javascript
    // 定义一个变量，用来存储取消函数
    let cancel;
    
    // 点击按钮1，发送延迟请求（服务器发送数据加个定时器即可）
    btns[0].onclick = async function () {
      // 节流 throttle
      if (cancel) {
        cancel();
      }
      try {
        let { data } = await axios.get('/getTimeout', {
          // 取消请求配置项
          cancelToken: new axios.CancelToken(function (c) {
            // 把取消函数赋值给全局变量
            cancel = c;
          }),
      	});
        console.log(data);
        box1.innerHTML = data.info;
      } catch (err) {
        console.log('错误', err);
        console.log(axios.isCancel(err));
        if (axios.isCancel(err)) {
          console.log('手动取消了 axios_ajax 请求');
        }
      }
    };
    
    // 点击按钮2，取消延迟请求
    btns[1].onclick = function () {
      // 执行取消函数
      cancel();
    };
    ```

#### 拦截器与错误处理

- `axios`：默认返回成功状态的 `promise` 实例，具体最后的结果还是由拦截器中的回调函数决定

- 拦截器

  - ```javascript
    // 请求拦截器
    axios.interceptors.request.use(function (config) {
      console.log('执行了请求拦截器');
      // 统一配置
      config.headers.token = 'afeiwiwieiirp';
      // 需要返还出去
      return config;
    });
    
    // 响应拦截器
    axios.interceptors.response.use(function (response) {
      console.log('执行了响应拦截器', response);
      // 可以进行一些数据再加工
      // 返还出去
      return response;
    });
    
    // 发送请求
    axios.get('geturl').then(res=>{
        console.log(res);
    })
    ```
    
  - 其实，拦截器中的两个函数就是 `axios` 请求后得到的 `promise` 调用 `then`  方法中的两个回调（成功 | 失败）

    - 因为我们希望拦截器执行后，仍然返回 `promise` 实例，供 `await` 去处理

- 拦截器执行顺序与错误处理

  - `axios` 中拦截器是通过数组收集的，请求拦截器和响应拦截器都收集在这个数组中；但是先执行请求拦截器，再执行响应拦截器，所以遇到请求拦截器时会把回调函数（成功 | 失败）放在数组的前面，响应拦截器会把回调函数（成功 | 失败）放在数组的后面；最后按照数组中的顺序依次执行（遍历），不断地更新最终返回的 `promise` 的值，因此请求拦截器就是倒序，响应拦截器就是正序
  
  - ```javascript
    // 请求拦截器
    // 多个请求拦截器执行顺序：倒序
    // 请求拦截器进入失败回调的两种方式
    // 1. 有多个拦截器，第一个拦截器成功的回调结果状态为失败，则进入第二个拦截器失败回调
    // 2. 拦截器有第三个参数，表示是否同步，默认 false，当前成功回调中错误或者返回失败的 promise，会进入自己的失败回调（了解）
    axios.interceptors.request.use(
      function (config) {
        console.log('111request');
        return config;
      },
      function (err) {
        console.log(err); // 请求错误的回调函数
      }
    );
    
    axios.interceptors.request.use(
      function (config) {
        console.log('222request');
        return config;
      },
      function (err) {
        console.log(err); // 请求错误的回调函数
      }
    );
    
    axios.interceptors.request.use(
      function (config) {
        console.log('333request');
        return config;
      },
      function (err) {
        console.log(err); // 请求错误的回调函数
      }
    );
    
    // 发送请求
    axios.get('geturl').then(res=>{
        console.log(res);
    }).catch((err)=>{
        console.log('请求错误',err)
    })
    ```
  
  - ```javascript
    // 响应拦截器
    // 多个响应拦截器执行顺序，顺序
    // 错误处理，类似于 promise 的错误
    axios.interceptors.response.use(
      (response) => {
        console.log('111response');
        // 测试一下，抛出一个错误
        // throw new Error('第一个响应拦截器错误');
        return response;
      },
      (err) => {
        console.log('第一个错误回调：', err);
      }
    );
    
    axios.interceptors.response.use(
      (response) => {
        console.log('222response');
        return response;
      },
      (err) => {
        console.log('第二个错误回调：', err);
        // 基于 promise 实现
        // 没有返回值：得到一个成功状态的 undefined 结果对象，所以会直接进入下一个拦截器的成功回调
    	// 如果需要继续进入下一个拦截器错误回调，有两种方式
    	// 1. throw err;
    	// 2. 返回失败状态的 promise 对象
        return Promise.reject(err);
      }
    );
    
    axios.interceptors.response.use(
      (response) => {
        console.log('333response');
        return response;
      },
      (err) => {
        console.log('第三个错误回调：', err);
        return Promise.reject(err);
      }
    );
    ```
  

#### Node.js 中的 Axios

- 服务器1

  - ```javascript
    const express = require('express');
    const path = require('path');
    const axios = require('axios');
    let app = express();
    
    // 响应页面
    app.get('/', (req, res) => {
      res.sendFile(path.join(__dirname, './views/index.html'));
    });
    
    // 接收 get 请求
    app.get('/getData', async (req, res) => {
      // node.js 发送 axios，向 7070 端口请求数据
      let { data } = await axios({
        url: 'http://localhost:7070/getData',
      });
      console.log(data);
      res.send({
        info: '8080端口数据',
        status: 1,
        proxy: data.info,
      });
    });
    
    // 监听
    app.listen(8080, () => {
      console.log('8080端口监听中……');
    });
    ```

- 服务器2

  - ```javascript
    const express = require('express');
    const path = require('path');
    
    let app = express();
    
    // 响应页面
    app.get('/', (req, res) => {
      res.sendFile(path.join(__dirname, './views/index.html'));
    });
    
    // 接收 get 请求
    app.get('/getData', (req, res) => {
      res.send({
        info: '7070端口数据',
        status: 1,
      });
    });
    
    // 监听
    app.listen(7070, () => {
      console.log('7070端口监听中……');
    });
    ```

- 通过 `服务器1` 向 `服务器2` 发送请求，可以实现服务器代理，即与 `服务器1` 端口相同的 `客户端` 可以跨域访问 `服务器2`