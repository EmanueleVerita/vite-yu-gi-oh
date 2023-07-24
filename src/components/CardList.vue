<script>
    import Card from './Card.vue';
    import { store } from '../store';

    export default {
        name: 'CardList',
        data(){
            return{
                store,
            }
        },
        components: {
            Card,
        }
    }
    
</script>

<template lang="">

    <div class="background-orange p-5">
        <div class="card-list-container container-fluid d-flex justify-content-between flex-wrap p-4 bg-white">
            <div class="row counter d-flex justify-content-center">
                <div class="col-auto">
                    Found {{ store.cards.length }} Cards
                </div>
            </div>
            <div class="row row-cols-5 g-5 justify-content-evenly">
                <Card v-for="(card, index) in store.cards" class="col-2 individual-card" :card="card" :key="index"/>
            </div>
        </div>
    </div>

</template>

<style lang="scss">
    @use '../assets/scss/main.scss';
    @use '../assets/scss/partials/variables.scss' as *;

    .background-orange{
        background-color: $orange;

        .card-list-container{
        gap: 10px;

            .counter{
            background-color: #18020B;
            width: 100%;
            margin: 0 auto;
            color: white;
            padding: 1rem 0;
            }
        }
        
    .individual-card{
        margin-right: 10px;
        margin-left: 10px
        }
    }
    
</style>