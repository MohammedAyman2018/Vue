<template>

    <li class="collection-item">
        <slot></slot>
    </li>



</template>

<script>
export default {
	name: 'Mission',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    ul li {
        width: 100%;
        margin: auto;
        max-width: 100%;
        height: 100%;
        max-height: 100%;
        line-height: 30px;
        padding-right: 0;
        border: 0;
        outline: 0;
        background: transparent;
        box-sizing: border-box;
        z-index: 1;
        transition: all 0.4s ease
    }

    li:hover:not(:first-child){
        cursor: pointer;
        color: white;
        background-color: slateblue;
    }

    li:hover i{
        color: black
    }

    li:hover i{
        color: white;
    }
</style>
