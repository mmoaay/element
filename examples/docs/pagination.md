## 基础用法

Pagination 组件实现分页，只要设置`Number`类型的`total`值即可，它代表页码的个数，之后我们还可以设置`layout`，代码需要显示的内容，用逗号分隔，布局元素会依次显示。

下例中，`prev`表示上一页，`next`为上一页，`pager`表示页码列表，除此以外还提供了`jumper`和`total`，`size`和特殊的布局符号`->`，`->`后的元素会靠右显示，`jumper`表示跳页元素，`total`表示显示页码总数，`size`用于设置每页显示的页码数量。

<el-pagination
  layout="prev, pager, next"
  :total="1000">
</el-pagination>

```html
<el-pagination
  layout="prev, pager, next"
  :total="50">
</el-pagination>
```

## 小型分页

在空间有限的情况下，可以使用简单的小型分页，只需要一个`small`属性，它接受一个`Boolean`，默认为`false`，设为`true`即可启用。

<el-pagination
  small
  layout="prev, pager, next"
  :total="50">
</el-pagination>

```html
<el-pagination
  small
  layout="prev, pager, next"
  :total="50">
</el-pagination>
```

## 附加功能

此例是一个完整的用例，使用了`sizechange`和`currentchange`事件来处理页码大小和当前页变动时候触发的事件。

`page-sizes`接受一个整型数组，数组元素为展示的选择每页显示个数的选项，`[100, 200, 300, 400]`表示四个选项，每页显示100个，200个，300个或者400个。

`page-size`接受一个`Number`，表示每页显示个数。

`current-page`接受一个`Number`，表示当前页页码。

<el-pagination
  @sizechange="handleSizeChange"
  @currentchange="handleCurrentChange"
  :current-page="5"
  :page-sizes="[100, 200, 300, 400]"
  :page-size="100"
  layout="sizes, prev, pager, next, jumper, total"
  :total="1000">
</el-pagination>

```html
<template>
  <el-pagination
    @sizechange="handleSizeChange"
    @currentchange="handleCurrentChange"
    :current-page="5"
    :page-sizes="[100, 200, 300, 400]"
    :page-size="100"
    layout="sizes, prev, pager, next, jumper, total"
    :total="1000">
  </el-pagination>
</template>
<script>
  export default {
    methods: {
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
    }
  }
</script>
```

<script>
  module.exports = {
    methods: {
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
    }
  }
</script>

## Attributes
| 参数               | 说明                                                     | 类型              | 可选值      | 默认值 |
|--------------------|----------------------------------------------------------|-------------------|-------------|--------|
| small              |   是否使用小型分页样式     | Boolean |             | false |
| page-size              | 每页显示条目个数                                                   | Number |             | 10 |
| total | 总条目数 | Number | | 0 |
| current-page | 当前页数 | Number | | 0|
| layout | 组件布局，子组件名用逗号分隔。| String | `size`, `prev`, `pager`, `next`, `jumper`, `->`, `total` | 'prev, pager, next, jumper, ->, total'  |
| page-sizes | 每页显示个数选择器的选项设置 | Number[] | |  [10, 20, 30, 40, 50, 100] |

## Events
| 事件名称 | 说明 | 回调参数 |
|---------|--------|---------|
| sizechange | pageSize 改变时会触发 | 每页条数`size` |
| currentchange | currentPage 改变时会触发 | 当前页`currentPage` |