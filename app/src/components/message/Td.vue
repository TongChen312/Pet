<template>
  <div>
    <titleBar :title="`${arr.ptype}`"></titleBar>
    <div class="X">
      <img :src="require(`../../assets/pet/dog/${arr.dimg}`)">
    </div>
    <div class="XX">
      <p>简介:</p>
      <p style="text-indent:2em">{{arr.total}}</p>
      <p>形态特征:</p>
      <p  style="text-indent:2em">{{arr.nature}}</p>
    </div>
  </div>
</template>
<script>
import TitleBar from "./TitleBar.vue";
export default {
  data() {
    return { arr: {dimg:"d00.jpg"} };
  },
  components: {
    titleBar: TitleBar
  },
  mounted() {
    var url = window.location.href.split("=")[1]; //截取字符串
    url = decodeURI(url); //解码
    this.dog(url);
  },
  methods: {
    dog(xx) {
      var url = "dog";
      this.axios.get(url).then(res => {
        this.arr = res.data[xx];
          console.log(this.arr)
      });
    }
  }
};
</script>
<style scoped>
.X {
  width: 100%;
  text-align: center;
}
.X img {
  width: 50%;
}
.XX {
  margin: 0.1rem;
}
.XX p {
  font-size: 0.3rem;
}
.XX :first-child {
  color: coral;
  margin: 0;
}
.XX :nth-child(3) {
  color: coral;
  margin: 0;
}
</style>