## 安装

```shell
npm install watermark-for-vue
```



## 使用方式

```js
import Watermark from 'watermark-for-vue'
```

```js
export default {
  name: 'App',
  components: {
    Watermark
  },
  data() {
    return {
      options:{
        content:''
      }
    }
  }
}
```



```html
<watermark :options="options">
  <template slot="content">
    <div>
      内容区域
    </div>
  </template>
</watermark>
```

## options配置

|     属性     |           说明           |  类型  |        默认值        |
| :----------: | :----------------------: | :----: | :------------------: |
|    width     |          canvas          | 元素宽 |      string 300      |
|    height    |          canvas          | 元素高 |      string 200      |
|  textAlign   |    绘制文本的对齐方式    | string |         left         |
| textBaseline |        文本基准线        | string |        bottom        |
|     font     |      字体大小及样式      | string | 16px Microsoft Yahei |
|  fillStyle   |     自定义水印的颜色     | string |        black         |
|   content    |         水印内容         | string |  内部文档，请勿外传  |
| globalAlpha  | 设置图形和图像透明度的值 | number |         0.1          |
|    rotate    |       文字旋转角度       | number |          16          |
|      x       |    canvas 横向偏移量     | number |          15          |
|      y       |    canvas 纵向偏移量     | number |          15          |

## 兼容性

使用了[MutationObserver API](https://www.caniuse.com/?search=MutationObserver)，低版本浏览器无法使用，自行查看
