<template>
  <div class="main" ref="main">
    <div
      class="box-img"
      ref="boxImg"
      @mouseover="handleOver"
      @mousemove="handleMove"
      @mouseleave="handleLeave"
    >
      <img src="@/assets/logo.png" alt="img" />
      <div
        class="box-hover"
        :style="this.mousePositon"
        v-show="isMouseOver"
      ></div>
    </div>
    <div class="box-img-mini" v-show="isMouseOver">
      <img src="@/assets/logo.png" alt="img" />
    </div>
  </div>
</template>

<script>
export default {
  name: "PicZoom",
  computed: {
    // hover状态时阴影块的位置
    hoverBoxStyle() {
      return {
        top: this.mousePositon.top,
        left: this.mousePositon.left,
      };
    },
  },
  data() {
    return {
      hoverLimitPosition: {
        maxTop: 0,
        minTop: 0,
        maxLeft: 0,
        minLeft: 0,
      },
      isMouseOver: false,
      mousePositon: {
        top: "8px",
        left: "8px",
      },
    };
  },
  methods: {
    handleOver() {
      this.isMouseOver = true;
    },
    handleMove(e) {
      console.log(e.clientY);
      // this.mousePositon = {
      //   top: `${e.clientY - 25 > 200 ? 0 : e.clientY - 25}px`,
      //   left: `${e.clientX - 25 > 200 ? 0 : e.clientX - 25}px`,
      // };
      if (e.clientY < this.hoverLimitPosition.minTop + 25) {
        this.mousePositon.top = this.hoverLimitPosition.minTop + "px";
      } else if (e.clientY > this.hoverLimitPosition.maxTop - 25) {
        this.mousePositon.top = this.hoverLimitPosition.maxTop - 50 + "px";
      } else {
        this.mousePositon.top = e.clientY - 25 + "px";
      }
      if (e.clientX < this.hoverLimitPosition.minLeft + 25) {
        this.mousePositon.left = this.hoverLimitPosition.minLeft + "px";
      } else if (e.clientX > this.hoverLimitPosition.maxLeft - 25) {
        this.mousePositon.left = this.hoverLimitPosition.maxLeft - 50 + "px";
      } else {
        this.mousePositon.left = e.clientX - 25 + "px";
      }
    },
    handleLeave() {
      this.isMouseOver = false;
    },
  },
  mounted() {
    this.hoverLimitPosition = {
      maxTop: this.$refs.main.offsetTop + 200,
      minTop: this.$refs.main.offsetTop,
      maxLeft: this.$refs.main.offsetLeft + 200,
      minLeft: this.$refs.main.offsetLeft,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
  display: inline-block;
  position: relative;
  .box-img {
    box-sizing: border-box;
    border: 1px solid #f2f2f2;
    width: 200px;
    height: 200px;
    z-index: 9;
    img {
      width: 100%;
      height: 100%;
    }
  }
  .box-hover {
    width: 50px;
    height: 50px;
    background: rgba(0, 0, 0, 0.2);
    position: fixed;
    top: 0;
    bottom: 0;
  }
  .box-img-mini {
    border: 1px solid #f2f2f2;
    position: absolute;
    left: 200px;
    bottom: 0;
    top: 0;
  }
}
</style>
