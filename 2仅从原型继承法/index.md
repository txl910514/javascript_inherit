### 原型链法
当前类 的原型 为 另一个类的原型

由于原型中的所有代码都是可重用的，这意味着继承自shape.prototype比继承自new Shape()所创建的实体要好得多。毕竟,new Shape()方式会将Shape的属性设定为对象自身属性，这样的代码是不可重用（因而要将其设置在原型中），但我们可采取以下方式对象效率做一些改善：
* 不要单独为继承关系创建新对象
* 尽量减少运行时方法搜索（例如toString()）

#### 所属模式
* 基于构造器工作的模式
* 原型拷贝模式（不存在原型链所有的对象共享一个原型对象）

#### 技术注解
* 由于该模式在构建继承关系时不需要新建对象实例，效率上会有较好的表现
* 提示: 原型链上的查询也会比较快，因为这里根本不存在链
* 缺点在于，对于子对象的修改会影响其父对象

示例

```` javascript
function Shape() {
    this.name = 'Shape';
    this.toString = function () {
        return this.name;
    }
}

function TwoDShape () {
}

TwoDShape.prototype = Shape.prototype;
TwoDShape.prototype.constructor = TwoDShape;
TwoDShape.prototype = Shape.prototype;
TwoDShape.prototype.name = "2D shape";

function Triangle (side, height) {
    this.name = 'Triangle';
    this.side = side;
    this.height = height;
    this.getRrea = function () {
        return this.side * this.height / 2;
    }
}

Triangle.prototype = TwoDShape.prototype;
Triangle.prototype.constructor = Triangle;
Triangle.prototype.name = "Triangle";
Triangle.prototype.getArea = function () {
    return this.side * this.height / 2;
}
````