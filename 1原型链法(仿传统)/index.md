### 原型链法
当前类 的原型 为 另一个类的示例

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
````