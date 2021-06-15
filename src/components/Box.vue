<template>
    <section class="output">
        <div class="box-container">
          <div class="box" :style="box"></div>
        </div>
    </section>
</template>

<script>
    export default{
        name: 'Box',
        props:['box']
    }

</script>
