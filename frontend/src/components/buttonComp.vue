<template>
  <button class="button" :class="{normal, next, confirm, hit}">{{ label }}</button>
</template>

<script>
export default {
    name: 'buttonComp',
    props: {
        label: {},
        normal: {type: Boolean},
        next: {type: Boolean},
        confirm: {type: Boolean},
        hit: {type: Boolean},

    }
}
</script>

<style>

    .button {
        border: 1px solid black;
        border-radius: 10px;
        padding: 5px;
        margin: 10px;
    }

    .button.normal {
        width: 150px;
        height: 50px;
        background-color: #787a6c;
        color: #f4f4f4;
    }

    .button:hover {
        background-color: #787a5c;
    }

    .button:active {
        background-color: #788a5c;
    }

    .button.confirm {
        background-color: #65b307;
    }

    .button.hit {
        background-color: #f1e702;
    }

    .button.next {
        background-color: #005b8f;
    }
</style>