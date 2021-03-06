## jquery 
在Jquery中 最重要的是Jquery方法。它的功能很强大，有4种用法
   1   最常用的方法就是传递css选择器给$( )方法，当通过这种方式调用时，$( )方法会返回当前文档中匹配该选择器的元素集。
   2   第二种调用方式是传递一个Element Document 或Window 对象给 $( )方法。在这种情况下 ，$( )方法只需简单地将 Element Document 或Window 对象封装成JQuery 对象并返回。这样可以是得能用JQuery 方法来操作这些元素而不是使用原生DOM方法。例如 在Jquery 中 可以使用  $ (document) ,$ (this).  juery 对象可以表示文档中的多个元素，也可以传递一个元素数组给$()方法。在这种情况下，返回的jquery对象表示该数组中的元素集
   3  第三种调用方式是传递HTML文本字符串给$( )方法。在这种调用方式下，jquery会根据传入的文本创建好HTML元素并封装为jQuery 对象返回。jQuery 不会将创建的元素自动插入文档中。
   4   传递一个函数给$（）方法，此时当文档加载完毕并且DOM可操作时，传入的函数将被调用。
###each()
遍历jQuery对象中的所有元素时，可以调用each() 方法来代替for循环。each() 方法有点类似  es5中的 forEach() 数组方法。它接受一个回调函数作为唯一参数，然后它对JQuery对象中的美一个元素调用回调函数。回调函数作为匹配元素的方法来调用，因此在回到函数里this关键字指代Element对象。each( )方法还会将索引值和该元素作为第一个和第二个参数传递给回调函数。
###map( )
JQuery的map( )方法和Array.prototype.map( )方法很接近。它能够接受回调函数作为参数，并为JQuery对象中的每一个元素都调用回调函数，同时将回调函数的返回值收集起来，并将这些返回值封装成一个新的JQuery对象返回，map( )调用回调函数的方式和each( )方法相同；元素作为this 值和第二个参数传入，元素的索引值作为第一个参数传入。
###index（）
该方法接受一个元素作为参数，返回值是该元素在此JQuery对象中的索引值，如果找不到的话，则返回-1，由于受到Jquery典型风格的影响，index( )方法会对该对象的第一个元素进行搜索。如果传入的是字符串，index( )会把它当成css选择器，并返回该JQuery对象中匹配该选择器的一组元素中的第一个元素的索引值。如果什么参数都不传入，index( )方法返回该JQuery对象中的第一个毗邻元素的索引值。
###is()
它接受一个选择器作为参数，如果选中元素中至少有一个匹配该选择器时，则返回true.可在each( )回调函数中使用它。
###jQUery 中的getter 和setter
 JQuery 对象最简单、最常见的操作时获取  get或设置 set HTML属性， css样式 ，元素内容和位置宽高的值，
 这种功能的方法有   attr( )   css(  ).....方法
##  使用JQuery 处理事件
##### 事件处理程序的简单注册
jquery 中定义的简单事件处理程序注册的方法
blur( )  focusin ( )  mousedown( ) mouseup( ) change( )
fouseout( )  mouseenter( ) resize( ) click( ) keydown( )
mouseleave( ) scroll( ) dbclick( )keypress( ) mousemove()  select( ) error( ) keyup( )
mouseout( ) submit( ) focus( ) load( )
mouseover( ) unload( )
## 下面给出一些注意事项
  focus 和blur 不支持冒泡，但 focusin和focusout事件支持，jQuery确保这些事件在所有浏览器下都支持。相反地，mouseover和mouseout事件支持冒泡，但这经常不方便，因为很难知道鼠标是从资金感兴趣的元素中一开了，还只是从该元素的子元素中移开了。mouseenter和mouseleave 是非冒泡事件，可以解决刚才饿问题。resize和unload 事件类型只在window对象中触发，如果想要给这两个事件类型注册处理程序，应该在$(window)上调用 resieze( ) 和 unload( ) 方法。
scroll ( )方法经常也用于$(window)对象上，但它可以用在有滚动条的任何元素上。
load( )方法可在$(window)上调用，用来给串口注册加载事件处理程序。
## 事件处理程序的高级注册
我们已经看到，jQuery 定义了相当多简单的方法来注册事件处理程序，所有的这些方法都是简单的调用单一的更复杂的bind( )来为命名的事件类型绑定处理程序，该处理程序会绑定到jQuery 对象中的每一个元素上，可以直接使用bind( ) .
在最简单的形式下，bind( )需要一个事件类型字符串作为其第一个参数，以及一个事件处理程序作为其第二个参数。事件注册的简单方式使用该形式的bind( ). 
例如调用$( 'p').click( f )；
调用 bind( )时还可以带有三个参数。在这种形式下，事件类型是第一个参数，处理程序函数是第三个参数。在这两个参数中间可以传入任何值，jQuery会在调用处理程序前，将指定的值设置为Event对象 的data属性。通过这种方式传递额外的数据给处理程序，不需要使用闭包，有时候很有用。
bind( )还有其他高级特性，如果第一个参数是有空格分隔的事件类型列表，则处理程序函数会为每一个命名的事件类型注册。
bind( )的另一个重要特性是允许为注册的事件处理程序制定命名空间。这是得可以定义处理程序组，能方便后续触发或卸载特定命名空间下的处理程序。处理程序的命名空间对于开发可复用jQuery代码的类库或模块的程序员来说特别有用。事件命名空间类似css的类选择器。要绑定事件处理器到命名空间中时，添加.和命名空间名到事件类型字符串中即可。
bind( )的最后一个特性是，第一个参数可以使对象，该对象把事件名映射到处理程序函数。再次使用hover( )方法来举例，调用$( '.a').hover(f,g)
####one( )
JQuery 还有一个事件处理程序注册方法。调用one( )方法就和bind( )一样，二者的工作原理也类似，除了在调用事件处理程序之后会自动注销它。这意味着，和该方法名字暗示一样，使用one( )注册的事件处理器永远只会触发一次
###注销事件处理程序
用bind( )注册事件处理程序后，可以使用unbind( )来注销它，以避免在将来的事件中触发它。
###动画的取消、延迟和队列
jQuery还定义了一些动画和队列相关的方法，我们需要进一步了解。首先是stop( )方法：它用来停止选中元素上的当前正在执行的任何动画。top( )方法接受两个可选的布尔值参数。如果第一个参数是true,会清除选中元素上的动画队列。除了会停止当前动画，还会取消任何等待执行的动画。第一个参数的默认值是false:  如果忽略该参数，等待执行的动画不会被取消。第二个参数用来指定正在连续变化的css属性是否保留当前值，还是应该变化到最终目标值。传入true可以让它们变化到最终值。传入false会让它们保持为当前值。
当动画是由用户事件触发时，在开始新的动画前，可能需要取消当前或等待执行的任何动画.
###jQuery  中Ajax 
在web应用编程技术里，Ajax 很流行，它使用HTTP脚本来按需加载数据，而不需要刷新整个页面。在现代web应用中，Ajax技术非常有用，因此JQuery内置了Ajax 工具来简化使用。jQuery 定义了一个高级工具方法和四个高级工具函数。这些高级工具都基于同一个强大的底层函数：Jquery( ).ajax( ).
####load( )
load( )是所有jQuery 工具中最简单的 ：向他传入一个URL ,它会异步加载该URL的内容，然后将内容插入每一个选中元素中，替换掉一件存在的任何内容。
除了必须的URL参数，load( )方法还接受两个可选参数。第一个可选参数表示的是数据，可以追加到URL后面，或者与请求以前发送。如果传入的是字符串，则会追加到URL后面（放在“？” 或“&”后面）如果传入对象，该对象会被转化为一个用 “&”分隔的名/值对。如果传入对象，该对象会被转化为一个用&分隔的名/值对后与请求一起发送。通常情况下，load( )方法发送http get ( )请求，但是如果传入数据对象，则会发送POST请求。
load( )方法的另一个可选参数是回调函数，当Ajax 请求成功或未成功，以及URL加载完毕并插入选中元素时，会调用该回调函数。如果没有指定任何数据，回调函数可以作为第二个参数传入。否则，它必须是第三个参数。在jQuery 对象的每一个元素上都会调用回调函数，并且每次调用都会传入三个参数： 被加载URL的完整文本内容、状态码字符串，以及用来加载该URL的XMLHttpRequest 对象。其中状态参数是JQuery 的状态码，不是HTTP状态码，其值是类似 “success” "error" "timeout"
#### Ajax 工具函数
1  $.getScript( )
2  $.getJSON()
3  $.get()和$.post()

