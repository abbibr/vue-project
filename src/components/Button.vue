<template>
    <div>
        <button class="btn" :style="{background: color}" @click="onClick">
            {{ text }}
        </button>
    </div>
</template>

<script>
    export default {
        name: 'Button',

        props: ['text', 'color'],

        methods: {
            onClick(){
                this.$emit('toggle-add-task');
            }
        }
    }
</script>

<style></style>