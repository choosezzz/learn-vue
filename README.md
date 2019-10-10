## learn Vue

#### Vue为数据驱动型，不用去操作dom，而是去操作数据

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
   - 模板：挂载点下的所有内容都称为模板内容，模板不仅可以写在html标签中，也可以在vue实例中使用template属性创建
   - 示例：template.html

3. 