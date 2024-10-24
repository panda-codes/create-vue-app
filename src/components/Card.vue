<script setup>
    import { defineProps } from 'vue';

    defineProps({
        bg:{
            type: String,
            default:"bg-gray-100"
        }
    })
</script>

<template>
    <div :class="`${bg} p-6 rounded-lg shadow-md`"><!--backticks within the double quotes to use javaScript/ :class to bind dynamic value-->
        <slot></slot>
    </div>
</template>