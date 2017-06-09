<template>
    <div class="list">
        <h1>To-Do List</h1>
        <form v-on:submit="addItem">
            <input type="text" v-model="newItem.name" placeholder="Insert...">
            <br />
            <input type="submit" value="Submit">
        </form>
        <ul>
            <li v-for="item in list">
                <input type="checkbox" class="toggle" v-model="item.done">
                <span :class="{done: item.done}">
                    {{item.name}} <button v-on:click="deleteItem(item)">x</button>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'toDoList',
        data() {
            return {
                newItem: {},
                list: []
            }
        },
        methods: {
            addItem: function(e) {
                this.list.push({
                    name: this.newItem.name,
                    done: false
                });
                e.preventDefault();
            },
            deleteItem: function(item) {
                this.list.splice(this.list.indexOf(item), 1);
            }
        }
    }
</script>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>