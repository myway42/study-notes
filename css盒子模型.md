# css盒子模型

给元素设置宽度,width不包括padding border margin值, 使用padding border margin值会扩大元素的范围空间,相当于box-sizing:content-box;

不设宽度,元素会占满父容器,width包括padding border margin值,使用padding border margin值挤占width.

设置宽度后,使用box-sizing:padding-box|border-box可以分别将padding值或padding border值计入width中,达到不设宽度时的元素行为.

另外:content-box加不加意义不大，padding-box存在浏览器差异不好用，border-box safari/chrome/firefox均是一样的效果,ie8+支持.