<script>
  export default {
    data() {
      return {
        visible2: false,
        gridData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
        gridData2: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          $info: true
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          $positive: true
        }],
        gridData3: [{
          tag: '家',
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '公司',
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '公司',
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '家',
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '公司',
          date: '2016-05-08',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '家',
          date: '2016-05-06',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          tag: '公司',
          date: '2016-05-07',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
        singleSelection: {},
        multipleSelection: []
      };
    },

    watch: {
      singleSelection(val) {
        console.log('selection: ', val);
      },

      multipleSelection(val) {
        console.log('selection: ', val);
      }
    },

    events: {
      handleClick(row) {
        console.log('you clicked ', row);
      }
    }
  };
</script>

<style>
  .demo-box.demo-popover {
    .el-popover + .el-popover {
      margin-left: 10px;
    }
    .el-input {
      width: 360px;
    }
    .el-button + .el-button {
      margin-left: 10px;
    }
  }
</style>

## 基础用法
Popover 的属性与 Tooltip 很类似，它们都是基于`Vue-popper`开发的，因此对于重复属性，请参考 Tooltip 的文档，在此文档中不做详尽解释。

要使用它，必须设置索引`ref`，在按钮中，我们注册了自定义指令`v-popover`，指向索引ID。

`trigger`属性用于设置何时触发 Popover ，提供三种触发方式：`hover`, `click` 和 `focus`，下面是样例，一些没有做解释的属性是与 Tooltip 一致的。

<div class="demo-box demo-popover">
  <el-popover
    ref="popover1"
    placement="top-start"
    title="标题"
    width="200"
    trigger="hover"
    content="这是一段容,这是一段容,这是一段容,这是一段容。">
  </el-popover>

  <el-popover
    ref="popover2"
    placement="bottom"
    title="标题"
    width="200"
    trigger="click"
    content="这是一段容,这是一段容,这是一段容,这是一段容。">
  </el-popover>

  <el-popover
    ref="popover3"
    placement="right"
    title="标题"
    width="200"
    trigger="focus"
    content="这是一段容,这是一段容,这是一段容,这是一段容。">
  </el-popover>

  <el-button v-popover:popover1>hover 激活</el-button>
  <el-button v-popover:popover2>click 激活</el-button>

  <el-input v-model="model" v-popover:popover3 placeholder="focus 激活"></el-input>
</div>


```html
<el-popover
  ref="popover1"
  placement="top-start"
  title="标题"
  width="200"
  trigger="hover"
  content="这是一段容,这是一段容,这是一段容,这是一段容。">
</el-popover>

<el-popover
  ref="popover2"
  placement="bottom"
  title="标题"
  width="200"
  trigger="click"
  content="这是一段容,这是一段容,这是一段容,这是一段容。">
</el-popover>

<el-popover
  ref="popover3"
  placement="right"
  title="标题"
  width="200"
  trigger="focus"
  content="这是一段容,这是一段容,这是一段容,这是一段容。">
</el-popover>

<el-button v-popover:popover1>hover 激活</el-button>
<el-button v-popover:popover2>click 激活</el-button>
<el-button v-popover:popover3>focus 激活</el-button>
```

## 嵌套信息

和其他组件一样，Popover 组件也可以利用分发取代`content`属性，下面我们嵌套了一个表格：

<div class="demo-box demo-popover">
  <el-popover
    ref="popover4"
    placement="right"
    width="400"
    trigger="click">
    <el-table :data="gridData">
      <el-table-column width="150" property="date" label="日期"></el-table-column>
      <el-table-column width="100" property="name" label="姓名"></el-table-column>
      <el-table-column width="300" property="address" label="地址"></el-table-column>
    </el-table>
  </el-popover>

  <el-button v-popover:popover4>click 激活</el-button>
</div>

```html
<el-popover
  ref="popover4"
  placement="right"
  width="400"
  trigger="click">
  <el-table :data="gridData">
    <el-table-column width="150" property="date" label="日期"></el-table-column>
    <el-table-column width="100" property="name" label="姓名"></el-table-column>
    <el-table-column width="300" property="address" label="地址"></el-table-column>
  </el-table>
</el-popover>

<el-button v-popover:popover4>click 激活</el-button>
```


## 嵌套操作

当然，你还可以嵌套操作，这相比 Dialog 更为轻量：

<div class="demo-box demo-popover">
  <el-popover
    ref="popover5"
    placement="top"
    width="160"
    :visible.sync="visible2">
    <p>这是一段内容这是一段内容确定删除吗？</p>
    <div style="text-align: right; margin: 0">
      <el-button size="mini" type="text" @click="visible2 = false">取消</el-button>
      <el-button type="primary" size="mini" @click="visible2 = false">确定</el-button>
    </div>
  </el-popover>

  <el-button v-popover:popover5>删除</el-button>
</div>

```html
<el-popover
  ref="popover5"
  placement="top"
  width="160"
  :visible.sync="visible2">
  <p>这是一段内容这是一段内容确定删除吗？</p>
  <div style="text-align: right; margin: 0">
    <el-button size="mini" type="text" @click="visible2 = false">取消</el-button>
    <el-button type="primary" size="mini" @click="visible2 = false">确定</el-button>
  </div>
</el-popover>

<el-button v-popover:popover5>删除</el-button>
```

## API
| 参数               | 说明                                                     | 类型              | 可选值      | 默认值 |
|--------------------|----------------------------------------------------------|-------------------|-------------|--------|
| trigger | 触发方式 | String  | 'click', 'focus', 'hover' |    click    |
|  title              | 标题 | String |  |   |
|  content        |  显示的内容，也可以通过 `slot#` 传入 DOM   | String            |  |  |
|  width        |  宽度  | String, Number            |  | 最小宽度 150px |
|  placement        |  出现位置  | String           |  `top`, `top-start`, `top-end`, `bottom`, `bottom-start`, `bottom-end`, `left`, `left-start`, `left-end`, `right`, `right-start`, `right-end` |  bottom |
|  visible        |  初始状态是否可见  | Boolean           |  |  false |
|  offset        |  出现位置的偏移量  | Number           |  |  0 |
|  transition     |  定义渐变动画      | String             |  | `fade-in-linear` |
|  visible-arrow   |  是否显示 Tooltip 箭头，更多参数可见[Vue-popper](https://github.com/element-component/vue-popper) | Boolean |  | true |
|  options        | [popper.js](https://popper.js.org/documentation.html) 的参数 | Object            | 参考 [popper.js](https://popper.js.org/documentation.html) 文档 | `{ boundariesElement: 'body', gpuAcceleration: false }` |

## Slot
| 参数               | 说明                                                     |
|--- | ---|
| - | Popover内嵌HTML文本 |