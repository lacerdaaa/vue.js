<template>
    <div class="vue-demo">
        <h1>{{ title }}</h1>

        <div class="counter-section">
            <p>Contagem atual: <strong>{{ counter }}</strong></p>
            <button @click="incrementCounter">Incrementar</button>
            <button @click="decrementCounter">Decrementar</button>
            <button @click="resetCounter">Resetar</button>
        </div>

        <div class="input-section">
            <p>Digite seu nome:</p>
            <input type="text" v-model="name" placeholder="Seu nome aqui">
            <p v-if="name">Olá, {{ name }}!</p>
        </div>

        <div class="list-section">
            <h2>Lista de Tarefas</h2>
            <ul>
                <li v-for="(task, index) in tasks" :key="index" :class="{ completed: task.completed }">
                    <input type="checkbox" v-model="task.completed">
                    {{ task.text }}
                    <button @click="removeTask(index)" class="remove-btn">X</button>
                </li>
            </ul>
            <div class="add-task">
                <input type="text" v-model="newTask" placeholder="Nova tarefa" @keyup.enter="addTask">
                <button @click="addTask">Adicionar</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VueDemo',

    // data: control de estado do componente. serve para delimitar o estado inicial das variaveis 
    data() {
        return {
            title: 'Aprendendo Vue ',
            counter: 0,
            name: '',
            tasks: [
                { text: 'Aprender Vue.js', completed: false },
                { text: 'Criar um componente', completed: false },
                { text: 'Entender reatividade', completed: false }
            ],
            newTask: '',
        }
    },

    // methods: funções que podem ser chamadas, ou seja, vao estar disponiveis publicamente para o template
    methods: {
        incrementCounter() {
            this.counter++
        },
        decrementCounter() {
            if (this.counter > 0) {
                this.counter--
            }
        },
        resetCounter() {
            this.counter = 0
        },
        addTask() {
            if (this.newTask.trim()) {
                this.tasks.push({ text: this.newTask, completed: false })
                this.newTask = ''
            }
        },
        removeTask(index) {
            this.tasks.splice(index, 1)
        }
    },

    // computed: propriedades que serão calculadas com base no estado inicial
    computed: {
        completedTasks() {
            return this.tasks.filter(task => task.completed).length
        },
        remainingTasks() {
            return this.tasks.filter(task => !task.completed).length
        }
    },

    // lifecycle hooks: métodos chamados em diferentes fases do ciclo de vida do componente
    mounted() {
        console.log('O componente foi montado!')
    }
}
</script>

<style scoped>
.vue-demo {
    font-family: Arial, sans-serif;
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

h1 {
    color: #42b983;
    text-align: center;
}

.counter-section,
.input-section,
.list-section {
    margin-bottom: 20px;
    padding: 15px;
    background-color: #f7f7f7;
    border-radius: 4px;
}

button {
    background-color: #42b983;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 3px;
    margin-right: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #33a06f;
}

input[type="text"] {
    padding: 5px;
    width: 80%;
    border: 1px solid #ddd;
    border-radius: 3px;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    padding: 8px;
    border-bottom: 1px solid #eee;
    display: flex;
    align-items: center;
}

.completed {
    text-decoration: line-through;
    color: #888;
}

.remove-btn {
    background-color: #ff6b6b;
    margin-left: auto;
}

.remove-btn:hover {
    background-color: #ff5252;
}

.add-task {
    display: flex;
    margin-top: 10px;
}

.add-task input {
    flex-grow: 1;
    margin-right: 5px;
}
</style>