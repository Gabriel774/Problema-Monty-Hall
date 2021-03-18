<template>
  <div>
      <Door v-for="value in quantity" :prize="prize" :key="value" :number="value" />
  </div>
</template>

<script>
import Door from './door'
export default {
    props: ['quantity', 'prize'],
    components: {Door}
}
</script>

<style scoped>
    div {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }
</style>