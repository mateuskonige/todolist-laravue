<template>
    <div class="addItem">
        <input type="text" v-model="item.name" placeholder="ex.: Tirar o lixo hoje">
        <button :class="[item.name ? 'active' : 'inactive']" @click="saveItem">Adicionar</button>
    </div>
</template>

<script>
    export default {
        data: () => {
            return {
                item: {
                    name: ""
                }
            }
        },
        methods: {
            saveItem() {
                if(this.item.name == ""){
                    return;
                }

                axios.post('api/item/store', {
                    item: this.item
                })
                .then(response => {
                    if(response.status == 201) {
                        this.item.name = "";
                        this.$emit('reloadList');
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
.addItem {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 1rem;    
}

input {
    width: 100%;
    border-radius: .25rem;
    padding: .25rem;
    outline: none;
    border: none;
}

.active {
    background-color: rgb(73, 167, 70);
    color: white;
    border-radius: .25rem;
    padding: .25rem;
    outline: none;
    border: none;
    margin-left: 1rem;
}

.inactive {
    display: none;
}
</style>
