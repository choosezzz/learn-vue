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

   8. 