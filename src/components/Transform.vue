<template>
  <div>
    <label>perspective: {{ transform.perspective }}px;</label>
    <input type="range" min="0" max="999" v-model="perspective" />

    <label>rotateX: {{ transform.rotateX }}deg; </label>
    <input type="range" min="-180" max="180" v-model="rotateX" />

    <label>rotateY: {{ transform.rotateY }}deg; </label>
    <input type="range" min="-180" max="180" v-model="rotateY" />

    <label>rotateZ: {{ transform.rotateZ }}deg; </label>
    <input type="range" min="-180" max="180" v-model="rotateZ" />
  </div>
</template>

<script>
export default {
  name: "Transform",
  props: ['transform'],
};
</script>
