<template>
    <div class="item">
        <input type="checkbox" @change="updateCheck" v-model="item.completed">
        <span :class="[item.completed ? 'completed' : '', 'itemText']">{{ item.name }}</span>
        <button @click="removeItem" class="remove">Remover</button>
    </div>
</template>

<script>
    export default {
        props: ['item'],
        methods: {
            updateCheck() {
                axios.put('api/item/' + this.item.id, {
                    item: this.item
                })
                .then(response => {
                    if(response.status == 200) {
                        this.$emit('itemchanged');
                    }
                })
                .catch(error => {
                    console.log(error);
                })
            },

            removeItem() {
                axios.delete('api/item/' + this.item.id)
                .then(response => {
                    if(response.status == 200) {
                        this.$emit('itemchanged');
                    }                
                })
                .catch(error => {
                    console.log(error);
                })
            }
        }
    }
</script>

<style scoped>
.completed {
    text-decoration: line-through;
    color: #aaa;
}

.itemText {
    width: 100%;
    margin-left: 1rem;
}

.item {
    display: flex;
    align-items: center;
    justify-content: center;
}

.remove {
    background-color: rgb(206, 75, 75);
    color: white;
    border-radius: .25rem;
    padding: .25rem;
    outline: none;
    border: none;
}
</style>
