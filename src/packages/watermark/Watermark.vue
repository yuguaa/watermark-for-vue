<template>
  <div id="watermark">
    <slot name="content"></slot>
  </div>
</template>

<script>
export default {
  name: 'Watermark',
  props: {
    options: {
      type: Object,
      default: () => {
        return {
          width: '300', // canvas元素宽
          height: '200', // canvas元素高
          textAlign: 'left', // 文字对齐
          textBaseline: 'bottom', // 基准线
          font: '16px Microsoft Yahei', // 字体大小及样式
          fillStyle: '#000', // 自定义水印的颜色
          content: '内部文档，请勿外传', // 水印内容
          globalAlpha: 0.1, // 设置图形和图像透明度的值
          rotate: 16, // 文字旋转角度
          zIndex: 1000, // 元素堆叠顺序
          x:15,// canvas元素横向偏移量
          y:15// canvas元素纵向向偏移量
        }
      }
    }
  },
  data() {
    return {
    }
  },
  mounted() {
    this.watermark(this.options)
  },
  methods: {
    watermark(options) {
      const {
        width,
        height, 
        textAlign,
        textBaseline,
        font,
        fillStyle, 
        content,
        globalAlpha, 
        rotate, 
        zIndex, 
        x,
        y
      } = options;
      const container = document.querySelector('#watermark')
      let canvas = document.createElement('canvas');
      canvas.setAttribute('width', width);
      canvas.setAttribute('height', height);
      let ctx = canvas.getContext('2d'); // 获取 canvas2d 上下文
      ctx.globalAlpha = globalAlpha;
      ctx.textAlign = textAlign;
      ctx.textBaseline = textBaseline;
      ctx.font = font;
      ctx.fillStyle = fillStyle;
      ctx.background = 'red';
      ctx.rotate((Math.PI * rotate) / 180);
      ctx.fillText(content, x, y);

      const base64Url = canvas.toDataURL(); // 返回一个包含图片展示的 data URI

      const __wm = document.querySelector('.__wm');//选择器
      const watermarkDiv = __wm || document.createElement("div");
      const styleStr = `
        position:absolute;
        top:0;
        left:0;
        right:0;
        bottom:0;
        width:100%;
        height:100%;
        z-index:${zIndex};
        pointer-events:none;
        background-repeat:repeat;
        background-image:url('${base64Url}')`;

      watermarkDiv.setAttribute('style', styleStr);
      watermarkDiv.classList = ['__wm']; //防止调试工具隐藏节点
      container.style.position = 'relative';
      if (!__wm) {
        container.appendChild(watermarkDiv); // 添加元素
      }

      const MutationObserver = window.MutationObserver || window.WebKitMutationObserver;
      // 检查浏览器是否支持这个API
      if (MutationObserver) {
        const args = arguments[0];
        let mo = new MutationObserver(() => {
          const __wm = document.querySelector('.__wm');
          // 只在__wm元素变动才重新调用
          if ((__wm && (__wm.getAttribute('style') !== styleStr || __wm.classList.length>1)) || !__wm || container.style.position !== 'relative') {
            // 避免一直触发
            mo.disconnect();
            mo = null;
            this.watermark(args);
          }
        })
        mo.observe(container, {
          attributes: true, // 观察目标节点的属性节点
          subtree: true, // 观察目标节点的所有后代节点
          childList: true, // 观察目标节点的子节点
        })
      }
    }
  }
}
</script>
