<template >
  <div class="card-stats">
    <div 
      v-for="(stat, index) in info" 
      :key="index"> 
      <div  class="stat-value">{{stat.value }}</div>
      <div class="stat">{{ stat.title}}</div>
    </div>
  </div>
</template>

<script>
export default { 
  props: {    
    info:{
      title:{
         type:String
      },
      value:{
         type:Number
      }  
    }         
  }
}
</script>

<style>
  .stat-value {
    font-size: 14px !important;
  }
  .card-stats {
  padding: 20px 0;
  border-radius: 14px;
  display: flex;
  justify-content:space-around;
  }
</style>