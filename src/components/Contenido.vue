
<template>
  <div>
    <!-- <img class="bhome" src="../assets/homeb.png" alt />

    <img @click.stop="click" class="baudio" src="../assets/audiob.png" alt />-->

    <!-- <button>Audio</button> -->

    <div class="wrapper">
      <div class="wrapper-picto">
        <div class="tooltip" v-bind:key="p1" v-for="p1 in p " :class="classpictogramas">
          <span class="tooltip-content">{{p1.name}}</span>
          <img class="picto" :src="p1.url" />
        </div>
      </div>
      <div class="wrapper-text">
        <span v-for="(s,i) in textoarray" v-bind:key="i" :class="classtext">{{s}}</span>
      </div>
      <div class="audio">
        <span v-for="(a,i) in textaudio " v-bind:key="i" :class="classaudio">{{a}}</span>
      </div>
    </div>

    <img class="bhome" src="../assets/homeb.png" alt />
    <img @click.stop="click" class="baudio" src="../assets/audiob.png" alt />

    <!-- <button @click.stop="click2">Audio</button> -->
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "Contenido",
  props: {
    texto: {
      type: String,
    },
    pictogramas: {
      type: Array,
    },
    audio: {
      type: String,
    },
  },
  data() {
    return {
      textoarray: "",
      classtext: "visible",
      classpictogramas: "visible",
      textaudio: "",
      classaudio: "visible",
      p: [],
    };
  },
  mounted() {
    this.textoarray = this.texto.split(" ");
    this.p = this.pictogramas;
    this.textaudio = this.textaudio;
  },

  methods: {
    click() {
      this.classpictogramas = "hide";
      let cont = 0;
      let temp = this.p;
      if (this.classpictogramas == "hide") {
        this.classpictogramas = "visible";
        this.p = [];
        let t = setInterval(() => {
          this.p.push(temp[cont]);
          console.log(cont);

          cont++;
          if (cont === temp.length) {
            clearInterval(t);
          }
        }, 800);
      }
    },

    click2() {
      let cont = 0;
      let spans = this.$el.querySelectorAll(".visible");
      this.classpictogramas = "hide";
      let t = setInterval(() => {
        spans[cont].className = "visible";
        gsap.fromTo(
          spans[cont],
          { opacity: 0, y: -40 },
          { opacity: 1, y: 0, duration: 1.5, ease: "elastic" }
        );
        console.log(cont, this.classpictogramas);
        cont++;
        if (cont === this.p.length) {
          clearInterval(t);
          this.classpictogramas = "visible";
        }
      }, 700);
    },
  },
  computed: {},
};
</script>

<style scoped>
.list-item,
span {
  /* display: ruby; */
  display: inline-block;
  margin-right: 10px;
  transition: 0.2s ease;
}
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}

.tooltip {
  width: 15%;
  padding: 5px;
  margin: 0 auto;
  text-align: center;
  cursor: pointer;
  float: left;
  box-sizing: border-box;
}

.tooltip-content {
  /* opacity: 0; */
  /* background-color: rgb(12, 128, 47); */
  color: rgb(0, 0, 0);
  text-align: center;
  border-radius: 6px;
  padding: 5px 20px;
  z-index: 1;
}

.tooltip:hover .tooltip-content {
  /* opacity: 1; */
  color: rgb(255, 255, 255);
  background-color: rgb(12, 128, 47);
  text-align: center;
  border-radius: 6px;
  padding: 5px 20px;
  z-index: 1;
}

.hide {
  visibility: hidden;
  transition: 0.1s;
}

.visible {
  visibility: visible;
  transition: 0.1s;
}
.wrapper {
  height: fit-content;
}

.wrapper-text {
  clear: both;
  padding-top: 40px;
  font-size: 28px;
}

.audio {
  font-size: 20px;
}
.wrapper-picto {
  width: 100%;
  /* height: fit-content; */
  height: 50%;
  /* display: flex;
  align-items: flex-start; */
}
.picto {
  width: 90px;
  margin: auto 5px 0 5px;
}

.bhome,
.baudio {
  padding-top: 20px;
  width: 70px;
}

@media only screen and (max-width: 812px) {
  .wrapper-text {
    margin-top: 15px;
    margin-bottom: 15px;
    font-size: 10pt;
    padding: 0;
  }
}
</style>