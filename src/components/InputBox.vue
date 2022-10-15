<script>
export default {
    data()
    {
        return {
            link: 'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json'
        };
    },
    emits: ['getPlaces'],
    methods: {
        async getInfo(event)
        {   
            const value = event.target.value.toLowerCase();

            await fetch(this.link)
                .then( response => {
                    if(response.ok)
                    {
                        return response.json();
                    }
                    return Promise.reject();
                })
                .then( data => {
                    const arr = data.filter( item => {
                                        const city = item.city.toLowerCase();
                                        const state = item.state.toLowerCase();

                                        return city.includes(value) || state.includes(value);
                                    })
                                    .sort( (a, b) => {
                                        return (a.population - b.population)? 1 : -1;
                                    })
                                    .map( item => (
                                        { 
                                            city: item.city,
                                            state: item.state,
                                            population: item.population
                                        }
                                    ));

                    this.$emit('getPlaces', arr);
                })
                .catch( error => {
                    console.log(`Error: ${error}`);
                });
        }
    }
};
</script>

<template>
    <div class="input-box">
        <input type="text" placeholder="City or State" @input="getInfo">
    </div>
</template>

<style scoped>
    .input-box {
        width: 22rem;
        height: 5rem;
        background-color: var(--bg-dark-white);
        border-radius: var(--border-rd);

        display: flex;
        justify-content: center;
        align-items: center;
    }

    .input-box input {
        width: 95%;
        height: 80%;
        font-size: 2rem;
        text-align: center;
        outline: none;
        border: var(--border-rd) solid var(--border-white);
        border-radius: var(--border-rd);
    }
</style>