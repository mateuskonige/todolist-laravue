<template>
    <div class="toDoListContainer">
        <div class="header">
            <h2 id="title">To Do List</h2>
            <add-item-form/>
        </div>
        <div>
            <list-view/>
        </div>
    </div>
</template>

<script>
    import addItemForm from './components/addItemForm.vue'
    import listView from './components/listView.vue'

    export default {
        components: {
            addItemForm,
            listView
        }
    }
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.toDoListContainer {
    width: 350px;
    margin: auto;
}

.header {
    background-color: #ddd;
    padding: 1rem;
}

#title {
    text-align: center;
}
</style>
