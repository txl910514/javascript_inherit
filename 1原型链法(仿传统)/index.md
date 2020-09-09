### 原型链法
* 子类 的原型 为 父类的原型

* 示例
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
````