<script>
import InputBox from './components/InputBox.vue';

export default {
    components: {
        InputBox
    },
    data()
    {
        return {
            places: []
        };
    }, 
    methods: {
        placesHandler(value)
        {
            this.places = value;
        }
    }
};
</script>

<template>
    <InputBox @get-places="placesHandler"/>
    <div class="container" v-for="place of places">
        <div class="names">
            <p>{{place.city}}, {{place.state}}</p>
        </div>
        <div class="numbers">
            <p>{{place.population}}</p>
        </div>
    </div>
</template>

<style scoped>
    .container {
        margin: 0 auto;
        padding: .5rem;
        width: 20rem;
        height: 3.5rem;
        background: linear-gradient(to top, var(--list-bg) 0%, var(--border-white) 100%);
        border-bottom: 2px solid var(--list-bg);
        box-shadow: 0px 0px 10px var(--list-shadow);
        font-size: 1.2rem;

        display: flex;
        justify-content: space-around;
        align-items: center;
    }

    .container:nth-child(odd) {
        transform: perspective(100px) rotateX(3deg) translateY(-2px);
    }

    .container:nth-child(even) {
        margin-top: -3px;
        transform: perspective(100px) rotateX(-3deg);    
    }
</style>