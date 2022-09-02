#### DOM查询节点的方法
document.getElementById() // 按照 **id** 查询一个元素节点对象
document.getElementsByName()  //通过**name属性**获取一组元素节点对象
document.getElementsByTagName() // 按照**标签名**查询一组元素节点对象
document.getElementsByClassName() // 按照**类名**查询一组元素节点对象

document.all() //代表页面中所有的元素
document.querySelector() //需要一个选择器的字符串作为参数，
                          可以根据一个CSS选择器来查询一个元素节点对象
document.querySelectorAll() //将符合条件的元素封装到一个数组中返回

如果需要读取元素节点属性，直接使用`元素.属性名`
        // 例子：`元素.id`  `元素.name`  `元素.value`
注意：class属性不能采用这种方式，读取class属性时需要使用`元素.className`

#### DOM删除节点的方法
父节点.removeChild(子节点)
子节点.parentNode.removeChild(子节点)


#### DOM创建节点的方法
document.createElement() //创建一个元素节点对象，它需要一个标签名作为参数
document.createTextNode() //创建一个文本节点对象，它需要一个文本内容作为参数

appendChild() //向一个父节点中添加一个新的子节点

#### DOM修改节点的方法
insertBefore()
replaceChild()

