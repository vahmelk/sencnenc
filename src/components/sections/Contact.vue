<template>
  <div class="all" id="Lets">
    <div class="con">
      <div class="first">
        <div class="inner" @click="download()">
          <div class="btn">
            <a ref="pdf" href="../../assets/Lebenslauf.pdf" download="CV_ZavenBadalyan.pdf"></a>
            <h3>{{contact.CV}}</h3>
          </div>
        </div>
      </div>
      <div class="second">
        <div class="inner" @click="openConv">
          <div class="btn">
            <h3>{{contact.lets}}</h3>
            <h2>{{contact.conv}}</h2>
          </div>
        </div>
      </div>
    </div>
    <div id="Conv"></div>
    <transition name="slide-fade">
      <Conv
        :pl1="contact.yEmail"
        :pl2="contact.yText"
        :subTxt="contact.subTxt"
        v-show="showDialog"
      />
    </transition>
  </div>
</template>

<script>
import Conv from "./Conv.vue";
import { scroller } from "vue-scrollto/src/scrollTo";
const scroll = scroller();

export default {
  name: "Contact",
  components: {
    Conv
  },
  data() {
    return {
      showDialog: false
    };
  },
  props: {
    contact: Object
  },
  methods: {
    openConv() {
      (this.showDialog = !this.showDialog) && scroll(`#Conv`);
    },
    download() {
      this.$refs.pdf.click();
    }
  }
};
</script>

<style scoped>
.btn {
  position: absolute;
  padding: 10px 40px;
  border-radius: 40px;
  text-align: center;
  cursor: pointer;
  color: white;
}
.inner {
  width: 100%;
  height: 10px;
  cursor: pointer;
  position: relative;
  align-items: center;
  display: flex;
  justify-content: center;
}
.first div {
  background-color: orange;
}
.second div {
  background-color: green;
}
.con > div {
  height: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.con a {
  display: none;
}
.con {
  height: 1098px;
  width: 100%;
  background-image: url("../../assets/gcer.png");
  background-repeat: no-repeat;
  background-size: cover;
}
.all {
  background-color: #f1f1f1;
}
</style>
<style>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease;
}
.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}
</style>