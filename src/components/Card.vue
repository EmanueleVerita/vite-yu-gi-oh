<script>
    import { store } from '../store';

    export default {
        props: {
            card: Object,
        },
        
        name: 'Card',
        data(){
            return{
                store,
            }
        }
    }

</script>


<template lang="">

    <div class="card card-item text-center">
        <img :src="card.card_images[0].image_url" alt="">
        <div class="card-name">
            {{ card.name }}
        </div>
        <div class="font">{{ card.archetype}}</div>
    </div>

</template>


<style lang="scss">
    @use '../assets/scss/partials/variables.scss' as *;
    
    .card-item{
        width: calc(90% / 5);
        background-color: $orange!important;

        .card-name{
            text-transform: uppercase;
            color:white;
        }
    }

</style>