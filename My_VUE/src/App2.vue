<script setup>
    import { ref, computed } from 'vue';

    const name = "Vue dinámico"

    const counter = ref(0)

    const arrayNumbers = ref([])

    const increment = () => {
        console.log('Aumentar contador')
        counter.value++

    }

    const decrement = () => {
        console.log('Decrementa contador')
        counter.value--
    }

    const reset = () => {
        console.log('Resetea contador')
        counter.value = 0
    }

    const add = () => { 
        arrayNumbers.value.push(counter.value)
    }
    
    const classCounter = computed(() => {
        if(counter.value === 0){
            return 'zero' 
        } if (counter.value > 0) {
            return 'positive'
        } if (counter.value > 0) {
            return 'negative'
        }
    })

    const classCounter2 = () => {
        if(counter.value === 0){
            return 'zero' 
        } if (counter.value > 0) {
            return 'positive'
        } if (counter.value < 0) {
            return 'negative'
        }
    }

    const bloqBtnAdd = computed(() => { 
        const numSearch = arrayNumbers.value.find( num => num === counter.value)
        console.log(numSearch)
        //if (numSearch === 0) return true
        //return numSearch ? true : false
        return numSearch || numSearch === 0
    })

    


</script>

<template>
    <div class="container text-center mt-5">
        <h1>Hola {{ name.toUpperCase() }}</h1>
        <h2 :class="classCounter2()">
            {{ counter }}
        </h2>

        <div class="btn-group">
            <button @click="increment" class="btn btn-success">Aumentar</button>
            <button @click="decrement" class="btn btn-danger">Decrementar</button>
            <button @click="reset"     class="btn btn-secondary">Resetear</button>
            <button @click="add" :disabled="bloqBtnAdd" class="btn btn-primary">Añadir</button>

        </div>
        
        <br>
        {{ arrayNumbers }}

        <ul class="list-group mt-2">
            <li class="list-group-item" v-for="(num, index) in arrayNumbers" :key="index">
                {{ num }}
            </li>
        </ul>
    </div>
    
</template>

<style>
h1 {
    color: red;
}
.positive{
    color: green;
}
.negative {
    color: red;
}
.zero {
    color: peru;
}
</style>