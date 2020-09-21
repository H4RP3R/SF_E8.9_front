<template>
<div id="app">
    <div class="wrapper">
        <h1>Python Counter</h1>
        <Form />
        <ResultsTable />
    </div>
</div>
</template>

<script>
import Form from './components/Form.vue'
import ResultsTable from './components/ResultsTable.vue'

export default {
    name: 'App',
    components: {
        Form,
        ResultsTable,
    },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cabin+Sketch:wght@700&display=swap');

html,
body {
    height: 100%;
    margin: 0;
    padding: 0;
    background-color: #46B34D;
    background-attachment: fixed;
}

h1 {
    font-family: 'Cabin Sketch', cursive;
    font-size: 56px;
    color: #d6e0db;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    display: flex;
    height: 100%;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
}

.wrapper {
    margin-bottom: 20px;
}
</style>
