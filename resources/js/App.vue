<template>
    <div class="toDoListContainer">
        <div class="header">
            <h2 id="title">To Do List</h2>
            <add-item-form
                v-on:reloadList="getList()"
            />
        </div>
        <div>
            <list-view
                :items="items"
                v-on:reloadList="getList()"
            />
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
        },
        data: () => {
            return {
                items: []
            }
        },
        methods: {
            getList() {
                axios.get('api/items')
                .then(response => {
                    this.items = response.data;
                })
                .catch(error => {
                    console.log(error);
                })
            }
        },
        created() {
            this.getList();
        }
    }
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: sans-serif;
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
