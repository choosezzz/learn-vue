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

   4. 