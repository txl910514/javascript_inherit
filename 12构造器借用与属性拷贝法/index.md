### 12 构造器借用与属性拷贝法
对于这种由于构造器的双重调用而带来的重复执行问题, 我们可以在父对象构造器上调用apply()方法，以获得其全部的自身属性， 然后再用一个简单的迭代器对其原型属性执行逐项拷贝
#### 所属模式
* 使用构造器工作模式
* 使用原型链模式
* 属性拷贝模式

#### 技术注解
* 该方法是方法11与方法4的结合体
* 它允许我们在不重复调用父对象构造器的情况下同时继承其自身属性和原型属性

示例

```` javascript
function Shape() {
    this.name = 'Shape';
    this.toString = function () {
        return this.name;
    }
}

function TwoDShape () {
    Shape.apply(this, arguments);
}
extend2(TwoDShape, Shape);
var twoDShape = new TwoDShape();
````