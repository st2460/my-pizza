<template>
  <div class="admin">
    <div class="col-7">
      <newPizza></newPizza>
    </div>
    <div class="col-5"></div>
  </div>
</template>

<script>
import newPizza from '@/components/newPizza'
export default {
  name: 'Admin',
  data () {
    return {
      
    }
  },
  components:{
    'newPizza':newPizza
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
