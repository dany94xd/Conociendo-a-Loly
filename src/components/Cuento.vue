<template>
  <div class="home">
    <!-- <p @click="next">Siguiente</p>
    <p @click="prev">Anterior</p>-->

    <div class="alert">
      <h1>Porfavor gire la pantalla</h1>
    </div>

    <span @click="next" class="flecha fdere">
      <img class="arrow" src="../assets/isq.png" alt />
    </span>

    <span @click="prev" class="flecha fisq">
      <img class="arrow" src="../assets/der.png" alt />
    </span>

    <div class="pasta">
      <book class="book" :data="pages" :turnPageByHand="true" ref="book">
        <template slot-scope="prop">
          <img v-if="prop.page.cover" :src="prop.page.urlcover" />
          <Contenido
            :texto="prop.page.title"
            :pictogramas="prop.page.pictogramas"
            :audio="prop.page.urlaudio"
          ></Contenido>
        </template>
      </book>
    </div>
  </div>
</template>

<script>
import Contenido from "./Contenido";
import $ from "jquery";
import book from "vue-book-component";

export default {
  name: "Cuento",
  components: { book, Contenido },
  data() {
    return {
      page: 1,
      pages: [
        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag1.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title:
            "Un día una linda lora nació de un huevo. Sus padres la llamaron Loly.",
          // urlaudio: require("../assets/sonido.mp3"),
          pictogramas: [
            { url: require("../assets/un.png"), name: "UN" },
            { url: require("../assets/dia.png"), name: "DÍA" },
            { url: require("../assets/de.png"), name: "DE" },
            { url: require("../assets/un.png"), name: "UN" },
            { url: require("../assets/huevo.png"), name: "HUEVO" },
            { url: require("../assets/nacer.png"), name: "NACIO" },
            { url: require("../assets/una.png"), name: "UNA" },
            { url: require("../assets/linda.png"), name: "LINDA" },
            { url: require("../assets/lora.png"), name: "LORA" },
            { url: require("../assets/sus.png"), name: "SUS" },
            { url: require("../assets/padres.png"), name: "PADRES" },
            { url: require("../assets/la.png"), name: "LA" },
            { url: require("../assets/llamaron.png"), name: "LLAMARON" },
            { url: require("../assets/loly.png"), name: "LOLY" },
          ],
          urlaudio: "que maspuez",
        },

        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag2.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title: "Loly iba al parque con su mamá, jugaba sola o con sus amigos",
          pictogramas: [
            { url: require("../assets/loly.png"), name: "LOLY" },
            { url: require("../assets/ir.png"), name: "IBA" },
            { url: require("../assets/al.png"), name: "AL" },
            { url: require("../assets/parque.png"), name: "PARQUE" },
            { url: require("../assets/conm.png"), name: "CON" },
            { url: require("../assets/su.png"), name: "SU" },
            { url: require("../assets/mama.png"), name: "MAMÁ" },
            { url: require("../assets/jugar.png"), name: "JUGABA" },
            { url: require("../assets/sola.png"), name: "SOLA" },
            { url: require("../assets/o.png"), name: "O" },
            { url: require("../assets/conm.png"), name: "CON" },
            { url: require("../assets/sus.png"), name: "SUS" },
            { url: require("../assets/amigos.png"), name: "AMIGOS" },
          ],
        },

        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag3.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title:
            "A Loly le gustaba estudiar mucho junto a sus compañeros de clase.",
          pictogramas: [
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/loly.png"), name: "LOLY" },
            { url: require("../assets/le.png"), name: "LE" },
            { url: require("../assets/gusta.png"), name: "GUSTABA" },
            { url: require("../assets/estudiar.png"), name: "ESTUDIAR" },
            { url: require("../assets/mucho.png"), name: "MUCHO" },
            { url: require("../assets/junto.png"), name: "JUNTO" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/sus.png"), name: "SUS" },
            { url: require("../assets/companeros.png"), name: "COMPAÑEROS" },
            { url: require("../assets/de.png"), name: "DE" },
            { url: require("../assets/clase.png"), name: "CLASE" },
          ],
        },

        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag4.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title: "A menudo Loly Soñaba con ayudar a otros niños a aprender.",
          pictogramas: [
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/menudo.png"), name: "MENUDO" },
            { url: require("../assets/loly.png"), name: "LOLY" },
            { url: require("../assets/soniar.png"), name: "SOÑABA" },
            { url: require("../assets/conm.png"), name: "CON" },
            { url: require("../assets/ayudar.png"), name: "AYUDAR" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/otros.png"), name: "OTROS" },
            { url: require("../assets/ninios.png"), name: "NIÑOS" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/aprender.png"), name: "APRENDER" },
          ],
        },

        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag5.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title: "Ya de grande, Loly trabajó muy duro para cumplir sus sueños",
          pictogramas: [
            { url: require("../assets/grande.png"), name: "YA" },
            { url: require("../assets/de.png"), name: "GRANDE" },
            { url: require("../assets/loly.png"), name: "LOLY" },
            { url: require("../assets/trabajo.png"), name: "TRABAJO " },
            { url: require("../assets/cumplir.png"), name: "CUMPLIR" },
            { url: require("../assets/sus.png"), name: "SUS" },
            { url: require("../assets/soniar.png"), name: "SUEÑOS" },
          ],
        },

        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag6.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title:
            "Y así creó a la robot Loly-1.0, quien te ayudará a aprender jugando.",
          pictogramas: [
            { url: require("../assets/y.png"), name: "Y" },
            { url: require("../assets/crear.png"), name: "CREÓ" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/la.png"), name: "LA" },
            { url: require("../assets/robot.png"), name: "ROBOT" },
            { url: require("../assets/loly1.0.png"), name: "LOLY" },
            { url: require("../assets/quien.png"), name: "QUIEN" },
            { url: require("../assets/te.png"), name: "TE" },
            { url: require("../assets/ayudar.png"), name: "AYUDARÁ" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/aprender.png"), name: "APRENDER" },
            { url: require("../assets/jugar.png"), name: "JUGANDO" },
          ],
        },
        {
          cover: true,
          have_title: false,
          button: false,
          urlcover: require("../assets/Pag7.png"),
          title: "",
        },
        {
          cover: false,
          have_title: true,
          button: true,
          title: "Junto a Loly-1.0 alcanzarás tus sueños al igual que ella.",
          pictogramas: [
            { url: require("../assets/y.png"), name: "Y" },
            { url: require("../assets/crear.png"), name: "CREÓ" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/la.png"), name: "LA" },
            { url: require("../assets/robot.png"), name: "ROBOT" },
            { url: require("../assets/loly1.0.png"), name: "LOLY" },
            { url: require("../assets/quien.png"), name: "QUIEN" },
            { url: require("../assets/te.png"), name: "TE" },
            { url: require("../assets/ayudar.png"), name: "AYUDARÁ" },
            { url: require("../assets/A.png"), name: "A" },
            { url: require("../assets/aprender.png"), name: "APRENDER" },
            { url: require("../assets/jugar.png"), name: "JUGANDO" },
          ],
        },
      ],
    };
  },
  methods: {
    next() {
      //this.$refs.book.turn()
      this.$refs.book.next();
      this.$refs.book.resetAnimateClass();
    },
    prev() {
      //this.$refs.book.turn(2)
      this.$refs.book.prev();
      this.$refs.book.resetAnimateClass();
    },
  },
  mounted: function () {},
};
</script>




<style scoped>
.book {
  /* position: relative;*/
  position: relative;
  margin: 0 auto;
  width: 95%;
  height: 80vh;
}

.bookMain {
  border: none !important;
  box-shadow: 0 0 20px #888;
}
.book img {
  width: auto;
  height: 100%;
  margin: auto;
}

.flecha {
  font-size: 36pt;
  cursor: pointer;
  z-index: 10;
  position: absolute;
}

.fdere {
  right: 50px;
}

.fisq {
  left: 50px;
}

.arrow {
  width: 60px;
  height: auto;
}
.fdere,
.fisq {
  position: fixed;
  width: 30px;
  padding-top: 250px;
}

.alert {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 20;
  background-color: rgba(0, 0, 0, 0.5);
}

.alert h1 {
  box-sizing: border-box;
}

.pasta {
  width: 99% !important;
  height: 99% !important;
  background-image: url(../assets/Pasta.png);
  background-size: 100% 100%;
  background-repeat: no-repeat;
  padding-top: 0.8%;
}
</style>