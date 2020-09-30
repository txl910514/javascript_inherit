### 5全属性拷贝法（浅拷贝法）
单纯的属性拷贝是一种非常简单直接的模式，但适用范围很广
#### 所属模式
* 基于对象工作的模式
* 属性拷贝模式

#### 技术注解
* 非常简单
* 没有使用原型属性

示例

```` javascript
function extendCopy (p) {
    var c = {};
    for (var i in p) {
        c[i] = p[i];
    }
    c.uber = p;
    return c;
}

var shape = {
    name: 'Shape',
    toString: function () {
        return this.name
    }
}

var twoDee = extendCopy(shape);
twoDee.name = '2D shape';
twoDee.toString = function () {
    return this.user.toString() + ',' + this.name
}

twoDee.toString();
````