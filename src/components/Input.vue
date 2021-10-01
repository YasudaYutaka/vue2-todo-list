<template>
  <!-- <v-container class=""> -->
    <v-card class="pa-5 d-flex flex-column mx-auto align-center mt-10 container" max-width="70vw">
        <form @submit.prevent="addInput" class="d-flex flex-column">
            <label for="todo-input" >New To Do</label>
            <input type="text" id="todo-input" v-model="enteredValue" @input="entering" class="pa-3" :class="valueHasError ? 'invalid' : ''" />
            <p v-if="valueHasError">Enter something valid!</p>
            <v-btn type="submit" class="mt-5 deep-purple darken-4" dark>Add</v-btn>
        </form>  
    </v-card>  
  <!-- </v-container> -->
</template>

<script>
export default {
    data() {
        return {
            enteredValue: '',
            isValueValid: false,
            isInputTouched: false,
            toDoList: []
        };
    },
    computed: {
        valueHasError() {
            return !this.isValueValid && this.isInputTouched ? true : false;
        }
    },
    methods: {
        addInput() {
            this.isInputTouched = true;
            if(this.enteredValue.trim() === '') {
                this.isValueValid = false
                console.log(this.valueHasError)
                return;
            }
            this.isValueValid = true;
            console.log(this.valueHasError)
            this.toDoList.push(this.enteredValue);
            this.enteredValue = '';
        },
        entering() {
            this.isInputTouched = true;
            if(this.enteredValue.trim() !== '') {
                this.isValueValid = true;
            }
        }
    }
}
</script>

<style scoped>
    form {
        width: 100%;
    }

    input {
        border: 1px solid gray;
        width: 100%;
    }

    .invalid {
        border: 1px solid #D81B60;
    }

    @media (min-width: 1193px) {
        .container {
            max-width: 40vw !important;
        }
    }
</style>
