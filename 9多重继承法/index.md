### 9多重继承法
所谓的多重继承，通常指的是一个子对象中有不止一个父对象的继承模式。

多重继承实现是极其简单的，我们只需要延续属性拷贝法的继承思路依次扩展对象即可，而对参数中所继承的对象的数量没有限制

#### 所属模式
* 基于对象工作的模式
* 属性拷贝模式

#### 技术注解
* 一种混合插入式(mixin-style)继承实现
* 它会按照父对象的出现顺序依次对他们的执行属性全拷贝

示例

```` javascript
function multi () {
    var n = {}, sutff, j= 0. len = arguments.length;
    for (j = 0; j < len; j++) {
        stuff = arguments[j];
        for (var i in stuff) {
            if (stuff.hasOwnProperty(i)) {
                n[i] = stuff[i];
            }
        }
    }
    return n;
}

var shape = {
    name: 'Shape',
    toString: function () {
        return this.name
    }
}

var twoDee = multi(shape, {
    name: "test1"
}, {
     name1: "test2"
});
// twoDee.name = '2D shape';
twoDee.toString = function () {
    return this.user.toString() + ',' + this.name
}

twoDee.toString();
````