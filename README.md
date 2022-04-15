## 安装

```shell
npm install watermark-for-vue
```

## 使用方式

```js
import Watermark from "watermark-for-vue";
```

```js
export default {
  name: "App",
  components: {
    Watermark,
  },
  data() {
    return {
      options: {
        content: "",
      },
    };
  },
};
```

```html
<watermark :options="options">
    <div class="container">
      内容区域
    </div>
</watermark>
```

## 注意事项

默认使用文字填充水印，当传入 src 时水印内容为图片水印，优先级高于文字水印。

```js
options: {
  src: require("@/assets/logo.png");//https://avatars.githubusercontent.com/u/58333667?s=60&v=4
}
```

## options 配置

|     属性     |                   说明                   |  类型  |        默认值        |
| :----------: | :--------------------------------------: | :----: | :------------------: |
|    width     |                  canvas                  | 元素宽 |      string 300      |
|    height    |                  canvas                  | 元素高 |      string 200      |
|  textAlign   |            绘制文本的对齐方式            | string |         left         |
| textBaseline |                文本基准线                | string |        bottom        |
|     font     |              字体大小及样式              | string | 16px Microsoft Yahei |
|  fillStyle   |             自定义水印的颜色             | string |        black         |
|   content    |                 水印内容                 | string |  内部文档，请勿外传  |
| globalAlpha  |         设置图形和图像透明度的值         | number |         0.1          |
|    rotate    |                 旋转角度                 | number |          16          |
|    repeat    |               水印重复属性               | string |        repeat        |
|      x       |            canvas 横向偏移量             | number |          15          |
|      y       |            canvas 纵向偏移量             | number |          15          |
|     src      | 水印为图片时的路径（支持本地和网络图片） | string |         null         |
|      sx      |          开始剪切的 x 坐标位置           | number |          0           |
|      sy      |          开始剪切的 y 坐标位置           | number |          0           |
|      dx      |      在画布上放置图像的 x 坐标位置       | number |          0           |
|      dy      |      在画布上放置图像的 y 坐标位置       | number |          0           |
|    iwidth    |  要使用的图像的宽度。（伸展或缩小图像）  | number |          60          |
|   iheight    |  要使用的图像的高度。（伸展或缩小图像）  | number |          60          |

```js
//canvas绘制图片水印的参数
ctx.drawImage(img, sx, sy, img.width, img.height, dx, dy, iwidth, iheight);
```

## 兼容性

使用了[MutationObserver API](https://www.caniuse.com/?search=MutationObserver)，低版本浏览器无法使用，自行查看
