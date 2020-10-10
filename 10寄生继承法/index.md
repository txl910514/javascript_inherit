### 10 寄生继承法
寄生式继承的基本思路是，我们可以在创建对象的函数中直接吸收其他对象的功能，然后在对其进行扩展并返回
#### 所属模式
* 基于对象工作的模式
* 使用原型链模式

#### 技术注解
* 该方法通过一个类似构造器的函数来创建对象
* 该函数会执行相应的对象拷贝，并对其进行扩展，然后返回该拷贝

示例

```` javascript
function parasite (victim) {
    var that = object(victim);
    that.more = 1;
    return that;
}

var shape = {
    name: 'Shape',
    toString: function () {
        return this.name
    }
}

var twoDee = parasite(shape);
// twoDee.name = '2D shape';
twoDee.toString = function () {
    return this.user.toString() + ',' + this.name
}

twoDee.toString();
````