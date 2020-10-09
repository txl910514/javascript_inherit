### 7原型继承法
基于这种在对象之间直接构建继承关系的理念， Douglas Crockford 为我们提出了一个建议，即可以用object()函数来接收父对象，并返回一个以该对象为原型的新对象

#### 所属模式
* 基于对象工作的模式
* 使用原型链模式

#### 技术注解
* 丢开仿类机制，直接在对象之间构建继承关系
* 发挥原型固有优势

示例

```` javascript
function object (o) {
    var n;
    function F() {};
    F.prototype = o;
    n = new F();
    n.uber =o;
    return n;
}

var shape = {
    name: 'Shape',
    toString: function () {
        return this.name
    }
}

var twoDee = object(shape);
twoDee.name = '2D shape';
twoDee.toString = function () {
    return this.user.toString() + ',' + this.name
}

twoDee.toString();
````