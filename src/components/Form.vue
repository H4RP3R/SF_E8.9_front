<template>
<div class="">
    <form class="" action="index.html" method="post">
        <input type="text" name="url-input" id="url-input" placeholder="site-to-check.com">
        <input type="submit" name="submit" id="submit" value="submit">
    </form>
</div>
</template>

<script>
export default {
    name: 'Form',
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Quicksand&display=swap');

input[type=text] {
    background-color: #46B34D;
    border-top: none;
    border-left: none;
    border-right: none;
    border-bottom: 2px dotted #d6e0db;
    color: #d6e0db;
    font-family: 'Quicksand', sans-serif;
    font-size: 24px;
    text-align: center;
}

input[type=text]:focus {
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
    background-color:#737dec;
    color: #d6e0db;
    margin-left: 10px;
    font-weight: bold;
    border-radius: 8px;
}
</style>
