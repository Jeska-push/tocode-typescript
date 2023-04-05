<template>
<div class="wrapper-person">
    <div v-if="item">
        <img :src="item.img" :alt="item.descr">
        <h1 style="color:#ffffff" class="title">{{item.title}}</h1>
        <p>{{ item.descr }}</p>
        <footer-card 
            :title="title" 
            :value="value" 
            :info="item.info"
        >
        </footer-card>
        <router-link  to="/" class="btn btnPrimary">Back to home</router-link>
        </div>
        <div v-else>Страница не существует
         
            <router-link  to="/" class="btn btnPrimary">Back to home</router-link>
        </div>
    </div>

</template>


<script>
import items from '@/seeders/items.js'
import FooterCard from '@/pages/FooterCard.vue'



export default {
  name: 'itemAlias',
    components: {
        FooterCard
      },

  data() {
    return {
      item:null,
      title:null
    }
  },
  mounted() {
    this.getСheck();  
  },
  watch: { 
    $route() {
      console.log(this.$route.params.itemAlias);
      this.getСheck();
    }
  },
  created () {
    const alias = this.$route.params.itemAlias;
    const item = items.find(el => el.alias === alias);
    this.item = item;

  },
  methods: { 
     getСheck() {
        const alias = this.$route.params.itemAlias;
        const item = items.find(el => el.alias === alias);
        this.item = item;
        console.log(alias);
          if (item === undefined ) {
              console.log('Такой страницы нет');
              window.location.hash = '/404.html'
              const response = fetch(alias);
              console.log(response)
          } else {
              console.log('Такая страница существует');
          }
      },

  }
}   
</script>

<style lang="scss">
.wrapper-person {
  
    margin: 0px auto;
    text-align: center;
    width: 70%;
    font-style: normal !important;
}
.card-stats {
    margin: 20px 0;
    border: radius 14px;
    display: flex;

}
</style>