---
title: "HTML重难点标签"
date: 2019-11-16T15:23:52+08:00
draft: false
---

# HTML重难点标签

### a标签

1. 作用:
     * 跳转到外部页面
     * 跳转到内部锚点
     * 跳转到邮箱或者电话号码等

2. 属性:

   1. href属性:
      1. 用途:在内部写入跳转地址
      2. href的取值
         1. 网址:
              * http://baidu.com
              * https://google.com
              * //google.com

         2. 路径:
             * /a/b/c
             * a/b/c

         3. 伪协议:
              1. javascript伪协议:
   
                      javascript:(代码);

                      应用在使a标签实现点击后不跳转不刷新上

                       ```HTML
                       <a href="javascript:;">查看</a>
                       ```
              2. 邮箱：点击后发送邮件给冒号后的地址

                     mailto:(邮箱名)  

              3. 电话号:点击后打电话给冒号后的号码

                     tel:电话号

         4. id:用于内部跳转

                 href=#xxx

   2. target属性:

      1. 属性内容:

         * _black :在新的页面打开
         * _self : 在单签页面打开
         * _top: 在顶级窗口打开
         * _parent : 在单签页面上一层的iframe打开
  
      2. 程序员命名:                 

             如果没有程序员自命的target属性值，则新开一个名为target属性值的窗口，否则会在target属性值的窗口中跳转


### table标签

1. table内写的标签
   1. 表头标签:
   
         `<thead></thead>`
   2. 表主题标签:

         `<tbody></tbody>`

   3. 表尾标签:

         `<tfoot></tfoot>`

   4. 表头单元格标签:
   
         `<th></th>`      

   5. 行标签:

         `<tr></tr>`

   6. 行内内容标签:

         `<td></td>`

* table应用展示: 
    
      ```HTML
      <table>
      <thead>
          <th>
              <td>小红</td>
              <td>小明</td>
              <td>小刘</td>
          </th>
      </thead>
      <tbody>
          <tr>
              <th>数学</th>
              <td>90</td>
              <td>20</td>
              <td>10</td>
          </tr>
          <tr>
              <th>语文</th>
              <td>10</td>
              <td>24</td>
              <td>18</td>
         </tr>
         <tr>
            <th>英语</th>
            <td>30</td>
            <td>50</td>
            <td>70</td>
         </tr>
      </tbody>
      <tfoot>
          <tr>
              <th>总分</th>
              <td>140</td>
              <td>130</td>
          </tr>
      </tfoot>
     </table>   
    ```

     ![](/images/4.png)


### img标签

1. 用途:
      发出一个get请求，展示一张图片
    
2. 属性:
      1. alt属性:
   
         当图片加载失败时，显示alt内的文字

         ```HTML
          <img src="./dog.png" alt="狗子">
         ```

      2. height/weight属性:

         控制图片的高度或宽度   

         只写高度，宽度自适应，只写宽度，高度自适应，都写图片会变形

         **永远不要让图片变形** 

      3. src属性:
   
          填写图片地址              


3. 事件:
      1. onload事件：
   
         图片加载成功时触发

      2. onerror事件:
   
         图片加载失败时触发   

      * 例:
          ```HTML
          <img  id="xxx" src="./dog.png" alt="狗子">
          <script>
             xxx.onload = function(){
               console.log("图片加载成功");
             };
             xxx.onerror = function(){
               console.log("图片加载失败");
               xxx.src = "404.png";
             };
          </script>
          ```

4. 响应式:
   
      ```CSS
      img{
          max-width:100%
      }   
      ```

### form标签

1. 作用：
      发出get或post请求，用来向 Web 服务器提交信息。

2. 属性：
      1. action属性:
         
         填入一个地址，表示向这个地址发送表单数据

      2. method属性:
         
         填入get或post，表示以get或以post方式发送数据

      3. autocomplete属性:
         
         表示input元素是否能被推荐一个值

         该属性的值可以是on或off，on为autocomplete属性生效，off为失效

      4. target属性:
   
          指示在提交表单之后，在哪里显示收到的回复

          属性值的内容及每个内容的作用和a标签的target一致


## input标签

1. 用途:
      让用户输入内容(一般写在form标签内)

2. 属性
      1. type属性:
         1. button :表示按钮
         2. text:文本框
         3. password:密码框
         4. submit:提交框
         5. file:添加文件框
         6. color:按钮内是一种颜色
         7. radio:单选框(需要在标签内加name才能知道哪几个是一组)
             ```HTML
               <input type="radio" name="gender">男
               <input type="radio" name="gender">女
               <br>
               <input type="radio" name="iscar">有车
               <input type="radio" name="iscar">没车
             ```
         8. checkbox:多选框(需要在标签内加name才能知道哪几个是一组)
   
             ```HTML
              <input type="checkbox" name="hobby">唱
              <input type="checkbox" name="hobby">跳
              <input type="checkbox" name="hobby">Rap
              <input type="checkbox" name="hobby">篮球
              ```

3. 事件:
      1. onchange事件
      2. onfocus事件
      3. onblur事件

4. input的提交和button的提交的区别:

      * **input提交中按钮只能填入文字，而button的提交按钮内可以插入标签**


### 其他标签
1. textarea标签:

      用于写一段文本，比如评论之类。

2. select+option标签:
      
      标签的组合用于写下拉菜单

      * select的属性:

          name:控件名称

      * option的属性:
          
          value:表示提交的值

          selected:表示默认选中

      * 例:
          ```HTML
          <select name="select">
            <option value="value1">Value 1</option> 
            <option value="value2" selected>Value 2</option>
            <option value="value3">Value 3</option>
          </select>
          ```


### 注意事项

1. 一般不监听input中的click事件
2. form里头的input要有name属性
3. form中要放一个type=“submit”,才能触发submit事件
         