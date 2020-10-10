### 11 构造器借用法
这里需要再次从构造器函数入手，由于在这种继承模式中，子对象构造器可以通过call()或apply()方法来调用父对象的构造器，因而，它通常备车被称为构造器盗用法或者构造器借用法
#### 所属模式
* 基于构造器工作模式

#### 技术注解
* 该方法可以只继承父对象的自身属性
* 可以与方法1结合使用，以便从原型中继承相关内容
* 它便于我们的子对象继承某个对象的具体属性(并且还有可能是引用类属性)时,选择最简单的处理方式

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
var twoDShape = new TwoDShape();
````