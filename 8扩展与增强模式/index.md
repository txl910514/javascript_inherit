### 8扩展与增强模式
对于继承来说，主要目标就是将一些现有的功能归为己有。也就是说，我们在新建一个对象时，通常首先应该继承于现有对象，然后再为其添加额外的方法与属性。对此，我们可以通过一个函数调用来完成，并且在其中混合使用我们刚才所讨论的两种方式。

具体而言就是：
* 使用原型继承的方式，将一个已有对象设置为新对象的原型。
* 新建一个对象后，将另一个已有对象的所有属性拷贝过来。

#### 所属模式
* 基于对象工作的模式
* 使用原型链模式
* 属性拷贝模式

#### 技术注解
* 该方法实际上是原型继承和属性拷贝法的混合应用
* 它通过一个函数一次性完成对象的继承与扩展

示例

```` javascript
function objectPlus (o, stuff) {
    var n;
    function F() {};
    F.prototype = o;
    n = new F();
    n.uber =o;
    for (var i in stuff) {
        a[i] = stuff[i];
    }
    return n;
}

var shape = {
    name: 'Shape',
    toString: function () {
        return this.name
    }
}

var twoDee = object(shape, {
    name: "test1"
});
// twoDee.name = '2D shape';
twoDee.toString = function () {
    return this.user.toString() + ',' + this.name
}

twoDee.toString();
````