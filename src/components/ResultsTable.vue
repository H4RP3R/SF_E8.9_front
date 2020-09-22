<template>
<div class="">
    <table>
        <thead>
            <tr>
                <th>id</th>
                <th>address</th>
                <th>matches</th>
                <th>status code</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="result in results" :key="result.id" v-bind:class=" {'unsuccessful' : result.http_status_code==0}">
                <td>{{ result.id }}</td>
                <td>{{ result.address }}</td>
                <td>{{ result.words_count }}</td>
                <td>{{ result.http_status_code }}</td>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
import axios from 'axios';
import {
    eventBus
} from '../main.js';



const URL = 'http://127.0.0.1:8000/results/'

export default {
    name: 'ResultsTable',

    data() {
        return {
            results: [],
        }
    },

    methods: {
        getData: function() {
            axios.get(URL)
                .then((response) => {
                    this.results = response.data.results;
                }).catch((e) => {
                    console.log(e);
                })
        },

        pollData() {
            let i = 0;
            const oldResults = this.results
            let x = this.polling = setInterval(() => {
                if ((i >= 12) || (oldResults.length < this.results.length)) {
                    clearInterval(x)
                    return
                }
                this.getData()
                i++;
            }, 2000)
        },
    },

    created() {
        this.getData();

        eventBus.$on('runUpdate', () => {
            this.pollData();
        })
    },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cabin+Sketch:wght@700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Quicksand&display=swap');

table {
    max-width: 960px;
    color: white;
}

th {
    font-family: 'Cabin Sketch', cursive;
    font-size: 22px;
    background-color: rgba(115, 125, 236, 0.8);
}

td,
th {
    border: 2px dashed #d6e0db;
    padding: 8px;
}

tr {
    font-family: 'Quicksand', sans-serif;
    font-weight: bold;
    background-color: rgba(129, 210, 203, 0.5);
}

.unsuccessful {
    font-family: 'Quicksand', sans-serif;
    font-weight: bold;
    background-color: rgba(210, 77, 77, 0.85);
}
</style>
