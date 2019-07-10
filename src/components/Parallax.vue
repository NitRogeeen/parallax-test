<template>
  <div class="parallax" :style="parentStyles">
    <slot></slot>
    <div
      class="image"
      :style="{
      backgroundImage: `url(${src})`,
      backgroundPosition: `50% ${imgTop}px`
    }"
    ></div>
  </div>
</template>

<script>
export default {
  name: "Parallax",
  props: {
    src: { type: String },
    height: { type: [String, Number], default: 500 },
    weight: { type: [String, Number], default: 0.5 }
  },
  data() {
    return {
      imgTop: 0
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      let scrollTop =
        document.documentElement.scrollTop || document.body.scrollTop;
      this.imgTop = -scrollTop * +this.weight;
    }
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  computed: {
    parentStyles() {
      return {
        height: `${this.height}px`
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.parallax {
  position: relative;
  width: 100%;
  overflow: hidden;
  text-align: center;
  .image {
    position: absolute;
    height: 100vh;
    width: 100vw;
    background-repeat: repeat;
    filter: brightness(80%);
    z-index: -1;
  }
}
</style>
