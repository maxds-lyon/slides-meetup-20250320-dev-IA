<template>
    <default class="two-cols-header">
        <slot />
        <div class="flex items-center ">
            <div class="w-1/2">
                <slot name="left"/>
            </div>
            <div class="w-1/2">
                <slot name="right"/>
            </div>
        </div>
    </default>
</template>

<script setup lang="ts">
import Default from "../layouts/default.vue";
</script>