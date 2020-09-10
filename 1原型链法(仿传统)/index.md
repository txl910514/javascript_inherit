### 原型链法
当前类 的原型 为 另一个类的实例

原型链是javascript中实现继承的默认方式 javascript是一种完全依靠对象的语言，其中没有类（class）的概念。因此我们需要直接用new Shape（）构造
一个实体，然后才能通过该实体的属性完成相关的继承工作，而不能直接继承Shape()构造器。另外这也确保了在继承实现之后，我们对Shape()所进行的任何修改、
重写甚至删除，都不会对TwoDShape()产生影响，因为我们所继承的只是由该构造器所建的一个实体

我们对对象的prototype属性进行完全替换时,有可能会对对象constructor属性产生一定的副作用。所以完成相关的继承关系设定后，对这些对象的constructor属性
进行相应的重置

示例

```` javascript
function Shape() {
    this.name = 'Shape';
    this.toString = function () {
        return this.name;
    }
}

function TwoDShape () {
    this.name = '2D Shape';
}

function Triangle (side, height) {
    this.name = 'Triangle';
    this.side = side;
    this.height = height;
    this.getRrea = function () {
        return this.side * this.height / 2;
    }
}

TwoDShape.prototype = new Shape();
Triangle.prototype = new TwoDShape();
TwoDShape.prototype.constructor = TwoDShape;
Triangle.prototype.constructor = Triangle;
````