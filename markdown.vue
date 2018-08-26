<template>
    <div>
      <textarea id="content" v-model="textareValue" @keyup="get" style="height:400px;width:600px;" @keydown.down.9="textareaTab"></textarea>
      <button type="button" @click="get">预览</button>
      <div id="result"></div>
    </div>
</template>
<script>
import showdown from 'showdown';
export default {
    name: '',
    data() {
        return {
          textareValue: ''
        }
    },
    methods: {
      get() {
        //获取要转换的文字
        var text = document.getElementById("content").value;
        //创建实例
        var converter = new showdown.Converter();
        //进行转换
        var html = converter.makeHtml(text);
        console.log(html);
        //展示到对应的地方  result便是id名称
        document.getElementById("result").innerHTML = html;
      },
      textareaTab () {
        /*跳几格由你自已决定*/
        this.textareValue = this.textareValue + "  ";
        window.event.returnValue = false;
      },
    }
}
</script>
<style scoped></style>
