### 4原型属性拷贝法
在构建可重用的继承代码时，我们也可以简单地将父对象的属性拷贝给子对象，我们可以创建一个extend2()函数，该函数也接受两个构造函数为参数，并将Parent的原型的所有属性全部拷贝给Child的原型， 其中包括方法， 因为方法本身也是一种函数类型的属性。

与之前的方法相比，这个方法在效率上略逊一筹，因为这里执行的是子对象原型的逐一拷贝，而非简单的原型链查询。这种方式仅适用于只包含基本数据类型的对象，所有的对象
类型（包括函数的数组）都是不可复制的， 因为他们只支持引用传递。
#### 所属模式
* 基于构造器工作的模式
* 拷贝属性模式
* 使用原型模式

#### 技术注解
* 将父对象原型中的内容全部转换成子对象原型属性
* 无须为继承单独创建对象实例
* 原型链本身也更短

示例

```` javascript
function extend2 (Child, Parent) {
    var p = Parent.prototype;
    var c = Child.prototype;
    for (var i in p) {
        c[i] = p[i];
    }
    c.uber = p;
}
function Shape() {
}
Shape.prototype.name = "Shape";
Shape.prototypr.toString = function () {
    return this.constructor.uber ? this.constructor.uber.toString() +  ',' + this.name : this.name;
}


function TwoDShape () {
}

extend2(TwoDShape, Shape);
TwoDShape.prototype.name = "2D shape";

function Triangle (side, height) {
    this.side = side;
    this.height = height;
}

extend2(Triangle, TwoDShape);
Triangle.prototype.name = "Triangle";
Triangle.prototype.getArea = function () {
    return this.side * this.height / 2;
}
````