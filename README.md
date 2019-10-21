## learn Vue

#### Vue为数据驱动型，不用去操作dom，而是去操作数据，面向数据编程。

1. **创建Vue实例 ：new Vue()**

   ```javascript
   new Vue({
       el:"#root",
       data:{
           content:"hello word"
       }
   });
   ```

   - **el**：表示element，通过选择器与页面dom元素绑定
   - **data**：为Vue对象的数据，使用{{content}}插值表达式访问data中的content
   - **示例**：helloworld.html

2. **挂载点、模板、实例之间的关系**

   - 挂载点：el属性绑定的dom元素成为挂载点，只有挂载点可以操作vue实例的data
   - 模板：挂载点下的所有内容都称为模板内容，模板不仅可以写在html标签中，也可以在vue实例中使用template属性创建，当html标签与vue实例中都存在模板时，会使用vue实例中的模板
   - Vue实例会将模板以及数据展示在绑定的挂载点中
   - 示例：template.html

   ```javascript
   new Vue({
       el:"#root",
       template: "<h2>hello {{content}}</h2>",
       data:{
           content:"hello word"
       }
   });
   ```

3. Vue实例中的数据、事件与方法

   1. 访问data中的数据

      1. data中的数据支持任意类型
      2. 使用插值表达式{{key}}访问
      3. 使用v-text="key"访问，该方式将key对应的数据进行转义之后当做纯文本填充到模板中
      4. 使用v-html="key"访问，该方式不会将key对应的数据进行转义，直接填充到模板中
      5. 示例：vue-data.html

   2. Vue中的事件

      1. v-on:event 绑定事件
      2. v-on:可以简写为@
      3. 示例：event-methods.html

      ```javascript
      <!--绑定点击事件，执行handleClick方法-->
      <div v-on:click="handleClick">
      	{{content}}
      </div>
      <!--或者-->
      <div @click="handleClick">
      	{{content}}
      </div>
      ```

   3. Vue中的方法

      1. 定义在Vue实例中的methods属性中

      2. 示例：event-methods.html

         ```js
         methods: {
         	handleClick: function(){
         		this.content = "hello Vue"
         	}
         }
         ```

   4. 属性绑定(单项绑定)

      1. 单项绑定：data发生变化属性值改变，属性值改变data不会发生变化

      2. v-bind:attr_name="key"，使用v-bind:属性名的方式给该属性赋值，key为vue实例data中的字段

      3. 简写为":attr_name='key'"

      4. 示例：v-bind.html

         ```javascript
         <div v-bind:title="title">
         	<h1>使用v-bind:title</h1>
         </div>
         <div :title="title">
         	<h1>使用:title</h1>
         </div>
         ```

   5. 双向数据绑定

      1. v-model="key"：该语法将vue实例中key对应的数据与当前模板的value双向绑定，key变化时value变化，value变化时，key对应的数据也发生改变。

      2. 示例：v-model.html

         ```javascript
         <div id="root">
         	单向数据绑定：<input type="text" :value="content">
         	<br>
         	双向数据绑定：<input type="text" v-model="content"/>
         	<div>
         		<h1>{{content}}</h1>
         	</div>
         </div>
         <script>
         	new Vue({
         		el: "#root",
         		data: {
         			content: "hello vue"
         		}
         	});
         </script>
         ```

   6. 计算属性

      1. 使用computed属性声明计算属性，计算属性的值对应函数的返回值

      2. 示例：computed.html

         1. computed：声明计算属性
         2. result：表示计算属性名称
         3. function返回值为计算属性result的值

         ```javascript
         computed: {
         	result: function(){
         		return parseInt(this.firstNumber) + parseInt(this.nextNumber);
         	}
         }
         ```

   7. 侦听器

      1. 使用watch属性声明侦听器，侦听属性变化，对应处理变化的函数

      2. 示例：watch.html

         1. watch：声明侦听器
         2. fullName：要侦听的属性字段
         3. function：属性变化对应的处理函数

         ```javascript
         watch: {
         	fullName: function(){
         		this.changeCount ++;
         	}
         }
         ```

   8. v-if

      1. 用来控制元素是否存在，true则向dom中添加元素，false则从dom中删除该元素

      2. v-if每次都会创建新的dom元素或者删除dom元素

      3. 示例：v-if&v-show.html

         ```javascript
         <div id="if" v-if="isexist" @click="notExist">
         	{{content}}
         </div>
         ```

   9. v-show

      1. 用来控制元素是否展示，true则显示该元素，false则将display属性置为none

      2. v-show只是控制元素的display属性，不会频繁操作dom树，性能更好

      3. 示例：v-if&v-show.html

         ```javascript
         <div id="show" v-show="isshow" @click="notShow">
         	{{content}}
         </div>
         ```

   10. v-for

       1. 用来遍历某个集合

       2. 语法：v-for="item of list"，其中list为要遍历的集合，item为每次遍历到的属性值

       3. v-for="(item, index) of list"，其中index为遍历到的下标

       4. 最好为每一项绑定key属性,key值需要唯一不重复，提高渲染的性能

       5. 示例：v-for.html

          ```javascript
          <ul>
          	<li v-for="(item,index) of list" :key="index">{{item}}</li>
          </ul>
          ```

   11. 练习：todo-list.html

   12. vue组件拆分

       1. 

   13. 

   