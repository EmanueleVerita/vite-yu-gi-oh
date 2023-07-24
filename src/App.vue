<script>
  import HeaderApp from './components/HeaderApp.vue';
  import AppSearch from './components/AppSearch.vue';
  import CardList from './components/CardList.vue';
  import { store } from './store';

  export default {
    components: {
      HeaderApp,
      AppSearch,
      CardList,
    },

    data(){
        return{
            store,
            cardsList: [],
        }
    },

    created(){
        this.createCard();
        this.getArchetype();
    },

    methods: {
        createCard(){
            axios.get(store.api).then((reponse) => {
                store.cards = reponse.data.data ;
            })  
        },

        getArchetype(){
            axios.get(store.archetype_api).then((reponse) => {
                store.archetypes = reponse.data ;
                console.log(AppSearch.data)
            }) 
        },

        selectArc(value){          
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${value}`).then((response)=>{
                store.cards = response.data.data;
                store.selected_archetype = value;
            })
        }
    }
  }
</script>

<template lang="">

    <AppHeader />
    <AppSearch  @selectArc="selectArc" />
    <CardList />

</template>

<style lang="scss">
  @use './assets/scss/partials/variables.scss as *';

</style>