<template>
<div class="">
    <form class="" @submit="sendForm" method="post">
        <input v-model="address" type="url" name="url-input" id="url-input"
        placeholder="https://site-to-check.com" required>
        <input type="submit" name="submit" id="submit" value="submit">
    </form>
</div>
</template>

<script>
import axios from 'axios';
import {eventBus} from "../main.js";

const URL = 'http://127.0.0.1:8000/add_address/'

export default {
    name: 'Form',

    data() {
        return {
            address: '',
        }
    },

    methods: {
        sendForm: function(e) {
            e.preventDefault();

            axios({
                method: 'post',
                url: URL,
                params: {
                    address: this.address
                },
            }).then(() => {
                this.address = '';
                eventBus.$emit('runUpdate')
            }).catch(
                (e) => {
                    console.log(e);
                }
            )
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Quicksand&display=swap');

input[type=url] {
    background-color: #46B34D;
    border-top: none;
    border-left: none;
    border-right: none;
    border-bottom: 2px dotted #d6e0db;
    color: #d6e0db;
    font-family: 'Quicksand', sans-serif;
    font-size: 24px;
    text-align: center;
    margin-bottom: 30px;
}

input[type=url]:focus {
    outline: none;
}

::placeholder {
    color: #d6e0db;
    font-size: 24px;
}

input[type=submit] {
    width: 60px;
    height: 32px;
    font-family: 'Quicksand', sans-serif;
    font-size: 12px;
    text-transform: uppercase;
    border: 2px solid #d6e0db;
    background-color: #737dec;
    color: #d6e0db;
    margin-left: 5px;
    font-weight: bold;
    border-radius: 8px;
}
</style>
