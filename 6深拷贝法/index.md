### 6深拷贝法
深拷贝的实现方式与浅拷贝基本相同，也需要通过遍历对象的属性来进行拷贝操作。只是在遇到一个对象引用性的属性时,我们需要再次对其调用深拷贝函数

使用deepCopy() 函数要注意两点
* 在拷贝每个属性之前，建议使用hasOwnProperty()来确认不会误拷贝不需要的继承属性
* 由于区分Array对象和普通Object对象相当繁琐，所以ES5标准中实现了Array.isArray()函数。这个跨浏览器的最佳解决方案(换句话说，为仅支持ES3的环境提供isArray()函数)虽然看起来有点取巧，但却是有效的
```` javascript
if (typeof Array.isArray !== 'function') {
    Array.isArray = function (candidate) {
        return Object.prototype.toString.call(candidate) === '[object Array]';
    }
}
````
#### 所属模式
* 基于对象工作的模式
* 属性拷贝模式

#### 技术注解
* 非常简单
* 没有使用原型属性
* 对象执行的都是值传递

示例

```` javascript
function deepCopy (p, c) {
    c = c || {};
    for (var i in p) {
        if (p.hasOwnProperty(i)) {
            if (typeof p[i] === 'object') {
                c[i] = Array.isArray(p[i]) ? [] : {};
                deepCopy(p[i], c[i]);
            } else {
                c[i] = p[i];
            }
        }
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