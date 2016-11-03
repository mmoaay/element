<script>
  import dateUtil from 'main/utils/date'
  export default {
    data() {
      return {
        currentDate: dateUtil.format(new Date(), 'yyyy-MM-dd HH:mm')
      };
    }
  }
</script>

<style scoped>
  .text {
    font-size: 14px;
  }

  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .item {
    padding: 18px 0;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix {
    @utils-clearfix;
  }

  .box-card {
    width: 480px;
  }
</style>

## Card

Display information aggregated into a card container.

### How to use

Contains the title, content, and operations.

:::demo Card component include the `header` and `body` parts. The ` header ` part need content distribution with named slots, but alse optional. 

```html
<el-card class="box-card">
  <div slot="header" class="clearfix">
    <span style="line-height: 36px;">Card name</span>
    <el-button style="float: right;" type="primary">Action</el-button>
  </div>
  <div v-for="o in 4" class="text item">
    {{'List' + o }}
  </div>
</el-card>
```

:::

### Simple card

The card can only has the content area.

:::demo

```html
<el-card class="box-card">
  <div v-for="o in 4" class="text item">
    {{'List' + o }}
  </div>
</el-card>
```

:::

### With pictures

You can define a richer presentation of the content.

:::demo Configuring the `body-style` attribute from the `style` of the `body` definition, and we also use the layout component.

```html
<el-row>
  <el-col :span="8" v-for="(o, index) in 2" :offset="index > 0 ? 2 : 0">
    <el-card :body-style="{ padding: '0px' }">
      <img src="~examples/assets/images/hamburger.png" class="image">
      <div style="padding: 14px;">
        <span>A Good Burger</span>
        <div class="bottom clearfix">
          <time class="time">{{ CurrentDate }}</time>
          <el-button type="text" class="button">Action</el-button>
        </div>
      </div>
    </el-card>
  </el-col>
</el-row>
```

:::

### Attributes
| Parameters      | Description    | Type      | Options       | Default   |
|---------- |-------- |---------- |-------------  |-------- |
| header | set header or be passed to DOM by `slot#header` | string| — | — |
| body-style | set the style of body| object| — | { padding: '20px' } |

