# javascript 💪第四天

## 项目目的

主要是熟悉ES5（filter,map）的几个对于数组的操作，熟练的掌握各种数据的处理。其中有filter、map是ES5定义的迭代方法，这些迭代方法都有一个特点，就是对**数组的每一项都运行给定的回调函数**，根据使用的迭代方法的不同，返回不同的结果。

## 酷炫的效果

我们可以通过`console.table()`输出一个一个表格的形式，方便我们对数据进行比较和查看

![console.table](C:\Users\Z7\Desktop\console.table.png)

## 知识点总结（数组的总结）
1. `Array.prototype.filter()`   [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

   **关键点总结： **过滤操作，有点像 SQL 里面的 select 语句。筛出运行结果是 true 的组成数组返回。

   * 返回一个新数组
   * 数组循环，过滤掉值为`false`的元素，得到通过测试的元素集合
   * 回调函数的三个参数 （元素的值，元素的索引，被遍历的数组）

   ```javascript
   // 1. Filter the list of inventors for those who were born in the 1500's
   const fifteen  = inventors.filter(inventor => inventor.year > 1500 && inventor.year < 1600)
   console.table(fifteen)
   ```

2. `Array.prototype.map`  [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

   **关键点总结：**map 形象的理解就是，把数组中的每个元素进行处理后，返回一个新的数组。

   * 返回一个新数组
   * 根据迭代函数计算数组的每一项

   ```javascript
   // 展示数组对象  inventors 里发明家的姓名  
   const fullNames = inventors.map(inventor => inventor.first + ' ' + inventor.last);
   ```

3. `Array.prototype.sort`  [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

   **关键点总结：**sort形象的理解就是，把数组中的前后2个元素进行比较，通过值得正负排序，返回一个新的数组。

   ```javascript
   const __ordered = inventors.sort((a, b) => (a > b) ? 1 : -1);
   console.table(__ordered);
   ```

4. `Array.prototype.reduce` [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce` )

   这是一个归并数组的方法，它接受一个函数作为参数（这个函数可以理解成累加器），它会遍历数组的所有项，然后构建一个最终的返回值，这个值就是这个累加器的第一个参数。例子如下：

   ```javascript
   [0,1,2,3,4].reduce(function(previousValue, currentValue, index, array){
     return previousValue + currentValue;
   });
   ```

   而此处我们需要统计一个给定数组中各个项的值，恰好可以用到这个方法，在累加器之中，将统计信息存入一个新的对象，最后返回统计值。

   ```javascript
   const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck' ];
     const reduce = data.reduce( (obj, item) => {
   	  if( !obj[item]  ) {
   		  obj[item] = 0;
   	  }
   		  obj[item]++;
   		  return obj;
     }, {});
     console.log(reduce);
   ```

## filter 和 map的结合

我们根据计算和过滤可以很方便的获取我们想要的值，做一些很好玩的事情

筛选出这一个页面中包含 CSS 的书名。代码如下：

```javascript
  // https://book.douban.com/tag/web
  const cate = document.querySelectorAll('.subject-list h2 a');
  const book = links
			.map(link => link.title)
			.filter(title => title.includes('CSS'));
```

#### **在这个好高骛远的时代，坚持JavaScript原生30天**