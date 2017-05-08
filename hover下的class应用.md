#hover下的class应用技巧#


##第一组##
`<a href="#"><span class="ico-manage">管理</span></a>`
###使用样式一：###
`a:hover{color:black}`
`a:hover.ico-manage{color:red;}`

此时鼠标经过”管理“2字，颜色为黑色
###使用样式二：###
`a:hover{color:black}`
`a:hover .ico-manage{color:red;} //注意空格`

此时鼠标经过”管理“2字，颜色为红色

##第二组##
`<a href="#" class="ico-manage">管理</a>`
###使用样式一：###
`a:hover{color:black}`
`a:hover.ico-manage{color:red;}`

此时鼠标经过”管理“2字，颜色为红色
###使用样式二：###
`a:hover{color:black}`
`a:hover .ico-manage{color:red;} //注意空格`

此时鼠标经过”管理“2字，颜色为黑色

**对于第一组的a与.ico-manage, .ico-manage属于span标签的，与a不同级；而对于第二组的a与.ico-manage, .ico-manage属于a标签的，即是与a同级，由此可得出一个结论：**

- **当class为当前标签中一个属性时，则样式写为：标签+class名**
- **当class为子标签的一个属性时，则样式写为：标签+空格+class名**