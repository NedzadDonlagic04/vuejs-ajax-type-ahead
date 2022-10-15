<script>
import InputBox from './components/InputBox.vue';

export default {
    components: {
        InputBox
    },
    methods: {
        placesHandler(value)
        {
            console.log(value);
        }
    }
};
</script>

<template>
    <InputBox @get-places="placesHandler"/>
    <div class="container"></div>
</template>