<template>
  <div class="parallax-test">
    <parallax ref="parallax" :src="bgImage" weight="0.2">
      <div class="title">Hello World!!</div>
      <nav :class="navStateClass">navigation bar!</nav>
    </parallax>
    <div class="contents">contents</div>
    <div style="text-align: center;">
      <a
        href="https://pixabay.com/ja/users/cocoparisienne-127419/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=3306655"
      >cocoparisienne</a>による
      <a
        href="https://pixabay.com/ja/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=3306655"
      >Pixabay</a>からの画像
    </div>
  </div>
</template>

<script>
import Parallax from "@/components/Parallax";
import BgImage from "@/assets/nature-3306655.jpg";

export default {
  name: "ParallaxTest",
  components: {
    Parallax
  },
  data() {
    return {
      navStyle: {
        position: "absolute",
        bottom: "0",
        top: "auto"
      },
      navStateClass: "normal",
      bgImage: BgImage
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      let parBottom = this.$refs.parallax.$el.getBoundingClientRect().bottom;
      if (parBottom > 50) {
        this.navStateClass = "normal";
      } else {
        this.navStateClass = "sticky";
      }
    }
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  }
};
</script>

<style lang="scss" scoped>
.contents {
  text-align: center;
  line-height: 500px;
  height: 1000px;
}
.title {
  position: absolute;
  display: inline-block;
  text-align: center;
  font-size: 60px;
  font-weight: 100;
  color: white;
  height: 60px;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
nav {
  color: white;
  height: 50px;
  width: 100%;
  line-height: 50px;
  text-align: center;
  font-size: 1.1rem;
  transition: all 250ms;
  z-index: 999;

  &.normal {
    position: absolute;
    bottom: 0;
    /* background-color: rgba(0, 0, 0, 0.3); */
  }

  &.sticky {
    position: fixed;
    top: 0;
    background-color: rgba(0, 0, 0, 0.8);
  }
}
</style>
