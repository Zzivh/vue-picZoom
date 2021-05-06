<template>
  <div id="app">
    <PicZoom
      :boxSize="300"
      :hoverBoxSize="150"
      picURL="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201901%2F03%2F20190103195747_jfzul.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1622903075&t=5f678cb085b0860820d8f9fa7be67c15"
    />
  </div>
</template>

<script>
import PicZoom from "./components/PicZoom.vue";

export default {
  name: "App",
  components: {
    PicZoom,
  },
};
</script>
