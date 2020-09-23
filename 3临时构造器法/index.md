### 3临时构造器法
由于所有的prototype都指向了一个相同的对象，父对象就会受到子对象属性的影响，为了打破这种连锁关系，我们可以用一个临时构造器函数来充当中介。
即我们创建一个空函数F(),并将其原型设置为父级构造器。然后，我们既可以用new F() 来创建一些不包含父对象属性的对象，同时又可以从父对象prototype属性
中继承一切了


有时需要调用父类的同名方法，以便完成工作，javascript虽然没有这种特殊语法，但是要实现类似的的功能还是很简单的，咋构建继承关系的过程中引入一个uber属性，
并指向其父级原型对象

#### 所属模式
* 基于构造器工作的模式
* 使用原型链模式

#### 技术注解
* 此模式不同于1号方法，它只继承父对象的原型属性，而对于其自身属性（也就是被构造器添加到this值中的属性）则不予继承
* 另外，该模式还为我们访问父对象提供了便利的方式（即通过uber属性）

示例

```` javascript
function extend (Child, Parent) {
    var F = function ();
    F.prototype = Parent.prototype;
    Child.prototype = new F();
    Child.prototype.constructor = Child;
    Child.uber = Parent.prototype;
}
function Shape() {
}
Shape.prototype.name = "Shape";
Shape.prototypr.toString = function () {
    return this.constructor.uber ? this.constructor.uber.toString() +  ',' + this.name : this.name;
}


function TwoDShape () {
}

extend(TwoDShape, Shape);
TwoDShape.prototype.name = "2D shape";

function Triangle (side, height) {
    this.side = side;
    this.height = height;
}

extend(Triangle, TwoDShape);
Triangle.prototype.name = "Triangle";
Triangle.prototype.getArea = function () {
    return this.side * this.height / 2;
}
````