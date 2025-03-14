<template>
    <div :class="randomClass" :style="randomStyle">
        <p>{{ randomNumber }}</p>
        <button @click="generateRandom">Gerar Número Aleatório</button>
    </div>
</template>

<script>
export default {
    name: 'RandomNumberComponent',
    data() {
        return {
            randomNumber: 0,
            colors: ['red', 'blue', 'green', 'yellow', 'purple'],
            fontSizes: ['16px', '20px', '24px', '30px', '36px'],
        };
    },
    computed: {
        randomClass() {
            return this.colors[Math.floor(Math.random() * this.colors.length)];
        },
        randomStyle() {
            return {
                fontSize: this.fontSizes[Math.floor(Math.random() * this.fontSizes.length)],
            };
        },
    },
    methods: {
        generateRandom() {
            this.randomNumber = Math.floor(Math.random() * 100) + 1;
        },
    },
};
</script>

<style scoped>
.red {
    color: red;
}

.blue {
    color: blue;
}

.green {
    color: green;
}

.yellow {
    color: yellow;
}

.purple {
    color: purple;
}

button {
    margin-top: 10px;
    padding: 10px;
    background-color: #ccc;
    border: none;
    cursor: pointer;
}
</style>