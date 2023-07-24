<script>

    import { store } from '../store';

    export default {
        data(){
            return{
                store,
                archetypeName: '',
            }
        }        
    }

</script>

<template lang="">

    <div class="selector-container d-flex justify-content-center">
        <label for="cards-selector">Select cards type:</label>
        <select v-model="archetypeName" @change="$emit('selectArc', archetypeName)">
            <option id="cards-selector" v-for="(item, index) in store.archetypes" :key="index" :value="item.archetype_name">
                {{item.archetype_name}}
            </option>
        </select>
    </div>

</template>

<style lang="scss">
    @use '../assets/scss/partials/variables.scss' as *;

    .selector-container{
        background-color: $orange;
        padding:  1rem 5rem 0 1rem;

        label{
            padding-right: 10px;
        }

        select{
            min-width: 150px;
        }
    }
</style>