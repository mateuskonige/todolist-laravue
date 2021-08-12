<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item
            :item="item"
            class="item"
            v-on:itemchanged="$emit('reloadList')"
            />
        </div>
    </div>
</template>

<script>
import listItem from './listItem.vue';

export default {
    props: ['items'],
    components: {
        listItem
    }
}
</script>

<style scoped>
.item {
    background: #ddd;
    padding: .5rem 1rem;
    margin-top: .25rem;
}
</style>
