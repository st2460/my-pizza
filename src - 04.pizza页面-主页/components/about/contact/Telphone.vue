<template>
  <div class="telphone">
    <h3 class="mt-3">欢迎拨打：{{tel}}</h3>
  </div>
</template>

<script>
export default {
  name: 'Telphone',
  data () {
    return {
      tel:'100-500-8888' 
    }
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
