[法]马克·布洛赫
出版社: 商务印书馆
副标题: 依附关系的成长+社会等级和政治制度
原作名: La Société féodale
译者: 张绪山 / 李增洪 / 侯树栋 / 郭守田(校) / 徐家玲(校)

美国反对美国

现代世界的诞生

[汉译世界学术名著丛书·纪念版]封建社会（上）：依附关系的成长-[法]马克·布洛赫著，张绪山译-商务印书馆-2017

[比]弗朗索瓦·冈绍夫著，张绪山、卢兆瑜译-商务印书馆

[名家后人忆丛]罗家伦与张维桢：我的父亲母亲-罗久芳著-百花文艺出版社-2006

在HTML中，创建一个固定表头的效果可以通过多种方式实现，其中最常见的方法是使用CSS。下面是一些实现固定表头的方法：

方法1：使用`position: sticky;`

这是最简单且现代的方法之一，适用于大多数浏览器。你可以将表头所在的`<th>`或`<tr>`元素设置为`position: sticky;`，并指定其`top`值，使其在滚动时保持固定。

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fixed Header Table</title>
<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
  }
  thead th {
    position: sticky;
    top: 0;
    background-color: white; /* 为了更好的视觉效果，背景色可以设置为与表格背景相同 */
  }
</style>
</head>
<body>

<table>
  <thead>
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
      <th>Header 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
      <td>Data 3</td>
    </tr>
    <!-- 更多行 -->
  </tbody>
</table>

</body>
</html>
```

方法2：使用JavaScript和CSS（适用于更复杂的布局）

如果你需要更复杂的布局控制或者`position: sticky;`在某些情况下不起作用，你可以使用JavaScript来动态调整表头的位置。例如，监听滚动事件，然后根据滚动位置调整表头的位置。

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fixed Header Table with JS</title>
<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
  }
  .fixed-header {
    position: fixed; /* 使用fixed定位 */
    top: 0; /* 在顶部固定 */
    width: calc(100% - 2px); /* 根据需要调整宽度 */
    background-color: white; /* 设置背景色 */
    z-index: 1000; /* 确保在内容之上 */
  }
</style>
</head>
<body>
<div style="height: 1000px;"> <!-- 模拟滚动内容 --> </div> <!-- 确保有足够的内容来滚动 -->
<table id="myTable">
  <thead class="fixed-header"> <!-- 使用JS来添加类 -->
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
      <th>Header 3</th>
    </tr>
  </thead>
  <tbody> <!-- 表体内容 --> </tbody> <!-- 这里填充你的数据 -->
</table>
<script>
window.addEventListener('scroll', function() {
  var table = document.getElementById('myTable'); // 获取表格元素
  var header = table.querySelector('thead'); // 获取表头元素
  var scrollTop = window.pageYOffset || document.documentElement.scrollTop; // 获取滚动位置
  if (scrollTop > 0) { // 如果开始滚动，则添加类以固定表头位置
    header.classList.add('fixed-header'); // 添加类以应用CSS样式来固定表头位置
  } else { // 如果停止滚动，则移除类以恢复默认状态（可选）
    header.classList.remove('fixed-header'); // 移除类以应用CSS样式来固定表头位置（可选）
  }
});
</script>
</body>
</html>
```
方法3：使用第三方库（如 DataTables）
如果你正在处理大型表格