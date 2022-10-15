<template>
    <div class="input-box">
        <input type="text" placeholder="City or State">
    </div>
</template>

<style scoped>
    .input-box {
        width: 20rem;
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