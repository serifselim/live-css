<template>
  <div id="app">
    <h2>Live Css</h2>
    <main>
      <section class="settings">
        <div class="settings-container">
          <label>perspective: {{ transform.perspective }}px;</label>
          <input type="range" min="0" max="999" v-model="transform.perspective" />

          <label>rotateX: {{ transform.rotateX }}deg; </label>
          <input type="range" min="-180" max="180" v-model="transform.rotateX" />

          <label>rotateY: {{ transform.rotateY }}deg; </label>
          <input type="range" min="-180" max="180" v-model="transform.rotateY" />

          <label>rotateZ: {{ transform.rotateZ }}deg; </label>
          <input type="range" min="-180" max="180" v-model="transform.rotateZ" />
        </div>
        <div class="settings-container">
          <label>R: {{ color.r }};</label>
          <input type="range" min="0" max="255" v-model="color.r" />

           <label>G: {{ color.g }}px;</label>
          <input type="range" min="0" max="255" v-model="color.g" />

           <label>B: {{ color.b }}px;</label>
          <input type="range" min="0" max="255" v-model="color.b" />
        </div>
        
        <div class="buttons-container">
          <button type="button" @click.prevent="reset">Reset</button>
          <button type="button" @click.prevent="copy">Copy</button>
        </div>
      </section>
      <Box :box="box" />
    </main>
  </div>
</template>

<script>
import Box from "./components/Box.vue";
export default {
  name: "App",
  components: {
    Box
  },
  data() {
    return {
      transform: {
        perspective: 100,
        rotateX: 0,
        rotateY: 0,
        rotateZ: 0,
      },
      color: {
        r : 0,
        g : 0,
        b : 0, 
      },
    };
  },
  computed: {
    box() {
      return {
        transform: `
          perspective(${this.transform.perspective}px)
          rotateX(${this.transform.rotateX}deg)
          rotateY(${this.transform.rotateY}deg)
          rotateZ(${this.transform.rotateZ}deg)
        `,
        background: `rgba(${this.color.r},${this.color.g},${this.color.b},1)`
      };
    },
  },
  methods: {
    changeBackground() {
      this.background = "red";
    },
  },
};
</script>

<style>
html {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
}

*,
*:before,
*:after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;
}
body {
  font-family: sans-serif;
  height: 100%;
  margin: 0;
  background: #261c33;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

h2 {
  color: #8d81f3;
  text-align: center;
  font-size: 40px;
  margin: 20px;
}
main {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 420px;
  max-width: 768px;
  margin: 0 auto;
  font-family: monospace, sans-serif;
  font-size: 22px;
}
main label {
  display: block;
}
main input[type="range"] {
  display: block;
  margin-bottom: 10px;
  width: 200px;
}
section.settings {
  display:flex;
  align-items: center;
  z-index: 2;
}
.settings-container{
  margin-left: 15px;
}
.buttons-container{
  display: flex;
  flex-direction: column;
  margin-left: 15px;
}
.box-container {
  padding: 50px;
  border: 1px solid #8d81f3;
  margin-left: 15px;
}
.box {
  width: 150px;
  height: 150px;
  background: #8d81f3;
}

button {
  background-color: #8d81f3;
  color: #fff;
  display: inline-block;
  font-size: 20px;
  padding: 10px;
  outline: none;
  border: none;
  margin-top: 15px;
}

label {
  color: #fff;
  font-size: 16px;
}
</style>
