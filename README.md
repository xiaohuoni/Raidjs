# Raid.js 设计文档


## 构想
1. 简单的样式覆盖
2. 简单的路由管理（约定式文件即路由）
3. 简单的组件使用（<oni-block></oni-block>）
4. 简单的组件重构（注解）
5. 标准化的web组件
6. 浏览器兼容
7. 简单的表单（双向绑定，表单验证，内置表单正则，支持自定义）
# 问题和需求
1. 自定义样式
现有的UI框架，要自定义样式需要写好几层的class，还需要做全局覆盖
2. 自定义组件
在现有组件的基础上面做扩展，能否有简单的方法实现
```html
<div >
    <!-- something -->
    <oni-block>
        <children></children>
    </oni-block>
</div>
```
3. 自定义Icon
现有的UI框架，多是采用字体图标，但是工作中，设计师提供的一般是img图片，
所以希望有能简单替换图片地址，和设置icon大小的组件
4. 自由组合组件
多个组件自由组合
```js
|───────────────────────|
|      |     title      |
| img  ├────────────────|
|      |    content     |
└──────|────────────────|
只要简单的更换层级关系就能实现下面的布局
|───────────────────────|
|        title          |
|──────├────────────────|
|  img |    content     |
└──────|────────────────|
```
5. 自动的正则判断和自定义判断
```js
<oni-input type="email" length="10" rule="自定义正则表达式" value={email} isTrue={canSubmit}/>
type:email,phone,pullname,password,idcard,number
优先判断自定义正则,再判断长度,最后判断内置的正则
```
6. 自定义提示框
7. 图片上传
自动压缩图片，支持设置压缩比
8. 上拉加载更多，下拉刷新
9. 简单的Tab页切换
10. 广告Banner
11. 高清方案
屏幕适配方案，在iphone6下，设计的尺寸，如定义宽度为100px，则设置width:1rem
12. 布局
Flex，Row，Col，Height(定义整个高度为100，用于需要全屏展示页面的情况，如登录页面和关于页面等)
## 组件

<div id="component"></div>

### 基础内容
现有组件||
-------- | ---|
 <a href="#icon">Icon</a>|
 <a href="#text">Text</a>|
 <a href="#progress ">Progress</a>|

### 表单
现有组件||
-------- | ---|
 <a href="#button">Button按钮</a>|
 <a href="#form">Form表单</a>|
 <a href="#input">Input输入框</a>|
 <a href="#checkbok">CheckBox多项选择器</a>|
 <a href="#radio">Radio单项选择器</a>|
 <a href="#picker">Picker滚动选择器</a>|
 <a href="#slider">Slider滑动选择器</a>|
 <a href="#laber">Laber标签</a>|
 <a href="#switch">Switch开关选择器</a>|

### 导航
现有组件||
-------- | ---|
 <a href="#router">Router</a>|
 <a href="#another">Another</a>|

### 多媒体
 <a href="#image">Image</a>

### 基础内容
<div id="icon"></div>

#### Iocn 图标
属性     | 类型|默认值|说明|
-------- | ---|---|------|
type | String||icon类型，取默认的，有效值暂未定义|
size | Number|23| Iphone6下的设计尺寸，会自动适配|
src    | String||正确的图片路径或者base64文件流，src有值，则废弃type|

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="text"></div>

#### Text 文本
属性     | 类型|默认值|说明|
-------- | ---|---|------|
decode | Boolean|false|是否解码|
预计用于原样输出html不转义
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="progress"></div>

#### Progress 进度条
属性     | 类型|默认值|说明|
-------- | ---|---|------|
percent | Float|0|0-1|
show-info|	Boolean|	false	|在进度条右侧显示百分比
activeColor|	Color	||	已选择的进度条的颜色	
backgroundColor	|Color||		未选择的进度条的颜色

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="progress"></div>

#### Progress 进度条
属性     | 类型|默认值|说明|
-------- | ---|---|------|
percent | Float|0|0-1|
show-info|	Boolean|	false	|在进度条右侧显示百分比
activeColor|	Color	||	已选择的进度条的颜色	
backgroundColor	|Color||		未选择的进度条的颜色

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

### 表单

<div id="button"></div>

#### Button 按钮
属性     | 类型|默认值|说明|
-------- | ---|---|------|
size	|String|	default	|按钮的大小		
type	|String	|default|	按钮的样式类型		
plain	|Boolean|	false|	按钮是否镂空，背景色透明		
disabled	|Boolean	|false	|是否禁用		
loading	|Boolean|	false|	名称前是否带 loading 图标
hover-class	|String|	button-hover|	指定按钮按下去的样式类。当 hover-class="none" 时，没有点击态效果
onClick |EventHandle||绑定点击事件
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="form"></div>

#### Form 表单
属性     | 类型|说明|
-------- | ---|------|
bindsubmit|	EventHandle|	携带 form 中的数据触发 submit 事件，event.detail = {value : {'name': 'value'} , formId: ''}	
bindreset|	EventHandle	|表单重置时会触发 reset 事件
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="input"></div>

#### Input 输入框
属性     | 类型|默认值|说明|
-------- | ---|---|------|
value	|String	||	输入框的初始内容
type	|String|	"text"|	input 的类型
rule	|String|	|	正则表达式
isTrue|Boolean||表单验证通过，需要绑定一个属性
grounp|String||分组
placeholder	|String	||	输入框为空时占位符
placeholder-style	|String||		指定 placeholder 的样式
placeholder-class	|String	|"input-placeholder"|	指定 placeholder 的样式类
disabled	|Boolean|	false	|是否禁用
maxlength	|Number	|140|	最大输入长度，设置为 -1 的时候不限制最大长度
minlength	|Number	||	最小输入长度，最小值为1
adjust-position|	Boolean|	true|	键盘弹起时，是否自动上推页面
bindinput|	EventHandle	||	当键盘输入时，触发input事件，event.detail = {value, cursor}，处理函数可以直接 return 一个字符串，将替换输入框的内容。	
bindfocus|	EventHandle	||	输入框聚焦时触发，event.detail = { value, height }，height 参数在基础库 1.9.90 起支持	
bindblur	|EventHandle||		输入框失去焦点时触发，event.detail = {value: value}	
bindconfirm|	EventHandle	||	点击完成按钮时触发，event.detail = {value: value}
type的有效值：
值   |说明|
-------- |------|
email|邮箱
phone|手机号码
pullname|中文姓名
password|密码
idcard|身份证
number|数字
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="checkbok"></div>

#### CheckbokGroup 多项选择器
属性     | 类型|说明|
-------- | ---|------|
bindchange	|EventHandle|选中项发生改变时触发 change 事件，detail = {value:[选中的checkbox的value的数组]}		
##### Checkbox 多选项目
属性     | 类型|默认值|说明|
-------- | ---|---|------|
value	|String		||Checkbox标识，选中时触发CheckboxGroup的 change 事件，并携带 checkbox 的 value
disabled|	Boolean|	false|	是否禁用
checked	|Boolean|	false	|当前是否选中，可用来设置默认选中
color|	Color	|	|Checkbox的颜色，同css的color		
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>
<div id="radio"></div>

#### RadioGroup 单项选择器
属性     | 类型|说明|
-------- | ---|------|
bindchange|	EventHandle	|	RadioGroup 中的选中项发生变化时触发 change 事件，event.detail = {value: 选中项radio的value}
##### Radio 单选项目
属性     | 类型|默认值|说明|
-------- | ---|---|------|
value	|String	||	Radio 标识。当该Radio 选中时，RadioGroup 的 change 事件会携带Radio的value
checked	|Boolean|	false|	当前是否选中
disabled	|Boolean|	false|	是否禁用
color	|Color	|	|radio的颜色，同css的color

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="picker"></div>

####    Picker  滚动选择器
普通选择器：mode = selector
属性     | 类型|默认值|说明|
-------- | ---|---|------|
range|	Array / Object Array|	[]|	mode为 selector 或 multiSelector 时，range 有效	
range-key	|String	||	当 range 是一个 Object Array 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容	
value	|Number|	0	|value 的值表示选择了 range 中的第几个（下标从 0 开始）	
bindchange	|EventHandle||		value 改变时触发 change 事件，event.detail = {value: value}	
disabled|	Boolean|	false	|是否禁用	
bindcancel|	EventHandle	||	取消选择或点遮罩层收起 picker 时触发
多列选择器：mode = multiSelector
属性     | 类型|默认值|说明|
-------- | ---|---|------|
range	|二维Array / 二维Object Array|	[]|	mode为 selector 或 multiSelector 时，range 有效。二维数组，长度表示多少列，数组的每项表示每列的数据，如[["a","b"], ["c","d"]]	
range-key|	String||		当 range 是一个 二维Object Array 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容	
value	|Array|	[]	|value 每一项的值表示选择了 range 对应项中的第几个（下标从 0 开始）	
bindchange	|EventHandle||		value 改变时触发 change 事件，event.detail = {value: value}	
bindcolumnchange|	EventHandle	||	某一列的值改变时触发 columnchange 事件，event.detail = {column: column, value: value}，column 的值表示改变了第几列（下标从0开始），value 的值表示变更值的下标	
bindcancel|	EventHandle	||	取消选择时触发	
disabled|	Boolean	|false|	是否禁用
日期选择器：mode = date
属性     | 类型|默认值|说明|
-------- | ---|---|------|
value	|String	|0	|表示选中的日期，格式为"YYYY-MM-DD"	
start	|String	||	表示有效日期范围的开始，字符串格式为"YYYY-MM-DD"	
end	|String	||	表示有效日期范围的结束，字符串格式为"YYYY-MM-DD"	
fields|	String|	day|	有效值 year,month,day，表示选择器的粒度	
bindchange	|EventHandle||		value 改变时触发 change 事件，event.detail = {value: value}	
bindcancel	|EventHandle||		取消选择时触发	
disabled|	Boolean|	false|	是否禁用
fields 有效值：
值     | 说明|
-------- |------|
year|	选择器粒度为年
month	|选择器粒度为月份
day|	选择器粒度为天
省市区选择器：mode = region
属性     | 类型|默认值|说明|
-------- | ---|---|------|
value	|Array|	[]	|表示选中的省市区，默认选中每一列的第一个值	
custom-item	|String|		可为每一列的顶部添加一个自定义的项	1.5.0
bindchange|	EventHandle	|	|value 改变时触发 change 事件，event.detail = {value: value}	
bindcancel|	EventHandle	||	取消选择时触发	
disabled	|Boolean|	false|	是否禁用
type|String||province city
##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="slider"></div>

#### Slider 滑动选择器
属性     | 类型|默认值|说明|
-------- | ---|---|------|
未设计||||

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="laber"></div>

#### Laber 
用来改进表单组件的可用性，使用for属性找到对应的id，或者将控件放在该标签下，当点击时，就会触发对应的控件。

for优先级高于内部控件，内部有多个控件的时候默认触发第一个控件。

目前可以绑定的控件有：Button, Checkbox, Radio, Switch

属性     | 类型|说明|
-------- | ---|------|
for	|String	|绑定控件的 id

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="switch"></div>

#### Switch 开关选择器
属性     | 类型|默认值|说明|
-------- | ---| ---|------|
checked	|Boolean|	false|	是否选中
type	|String	|switch	|样式，有效值：switch, checkbox
bindchange|	EventHandle	|	|checked 改变时触发 change 事件，event.detail={ value:checked}
color	|Color	||	switch 的颜色，同 css 的 color

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

### 导航
<div id="roouter"></div>

#### Router 页面链接
属性     | 类型|默认值|说明|
-------- | ---|---|------|
url|	String	||	应用内的跳转链接
data|Object|{}|跳转携带参数

##### 实例：
```js
未实现
```
<img src="">
<a href="#component">返回导航</a>

<div id="another"></div>

#### Another 页面内定位
属性     | 类型|默认值|说明|
-------- | ---|---|------|
href|	String	||	当前页面定位，对应id


##### 实例：
```html
<div id="user1"></div>
<div id="user2"></div>
<div id="user3"></div>
<Another href="#user1"/>
<!-- 点击Another，页面会自动滚动到id="user1"的位置 -->
```
<img src="">
<a href="#component">返回导航</a>

### 多媒体
 
<div id="image"></div>

#### Image 图片
属性     | 类型|默认值|说明|
-------- | ---|---|------|
src	|String	|	|图片资源地址	
mode	|String||	'scaleToFill'	图片裁剪、缩放的模式	
lazy-load	|Boolean|	false	|图片懒加载。只针对page与scroll-view下的image有效
binderror	|HandleEvent|	|	当错误发生时，发布到 AppService 的事件名，事件对象event.detail = {errMsg: 'something wrong'}	
bindload	|HandleEvent||		当图片载入完毕时，发布到 AppService 的事件名，事件对象event.detail = {height:'图片高度px', width:'图片宽度px'}
mode 有效值：
mode 有 13 种模式，其中 4 种是缩放模式，9 种是裁剪模式。
模式     | 值|说明|
-------- | ---|------|
缩放|	scaleToFill	|不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素
缩放|	aspectFit	|保持纵横比缩放图片，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来。
缩放	|aspectFill|	保持纵横比缩放图片，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取。
缩放	|widthFix|	宽度不变，高度自动变化，保持原图宽高比不变
裁剪|	top	|不缩放图片，只显示图片的顶部区域
裁剪|	bottom|	不缩放图片，只显示图片的底部区域
裁剪	|center|	不缩放图片，只显示图片的中间区域
裁剪	|left	|不缩放图片，只显示图片的左边区域
裁剪	|right|	不缩放图片，只显示图片的右边区域
裁剪|	top left|	不缩放图片，只显示图片的左上边区域
裁剪|	top right|	不缩放图片，只显示图片的右上边区域
裁剪|	bottom left	|不缩放图片，只显示图片的左下边区域
裁剪	|bottom right|	不缩放图片，只显示图片的右下边区域
##### 实例：
```html
未实现
```
<img src="">
<a href="#component">返回导航</a>
