<template>
  <div class="one box-shadow-extra-large">
    <div class="value text-gray-dark">{{ thumb }}</div>
    <div class="info-title text-gray-dark">{{ title }}</div>
  </div>
</template>

<script>
    import {defineComponent} from 'vue'

    export default defineComponent({
      name: 'Card',
      props: {
        title: {
        type: String,
        required: true
        },
        thumb: {
            type: String,
            required: true
        }
      }
    })
</script>

<style>
.one {
  margin: 20px;
  border-radius: 20px;
  /* background: #ECEFF4; */
  background: #ffffff;
  width: 400px;
  height: 200px;
  text-align: center;
}
.info-title {
  font-size: 20px;
  font-weight: bolder;
  margin: 20px;
}
.value {
  font-size: 25px;
  font-weight: bold;
  margin: 20px;
}
</style>