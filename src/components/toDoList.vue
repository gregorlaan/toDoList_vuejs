<template>
    <div class="list">
        <div class="container">
        <h1>To-Do List</h1>
            <form v-on:submit="addItem">
                <input class="insert" type="text" v-model="newItem.name" placeholder="Add an item to the list">
            </form>
            <ul>
                <li :class="{done: item.done}" v-for="item in list">
                    <label>
                        <input type="checkbox" name="checkbox" class="toggle" v-model="item.done">
                            {{item.name}}
                    </label>
                    <a class="remove" v-on:click="deleteItem(item)"><i class="fa fa-times" aria-hidden="true"></i></a>    
                </li>
            </ul>
        </div>
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
                if(this.newItem.name.length) {
                    this.list.push({
                        name: this.newItem.name,
                        done: false
                    });
                };
                e.preventDefault();
                this.newItem.name = "";
            },
            deleteItem: function(item) {
                this.list.splice(this.list.indexOf(item), 1);
            }
        }
    }
</script>

<style scoped>
    .done {
        background: #ecffec;
    }
     .done label {
        text-decoration: line-through;
    }
    .container {
        background: white;
        box-shadow: 0px 0px 5px 1px #c3c3c3;
        width: 100%;
        max-width: 540px;
        margin: 0 auto;
    }
    h1 {
        background: #0093ff;
        margin: 0;
        padding: 20px;
        color: white;
        text-align: center;
    }
    ul {
        list-style: none;
        padding: 0;
        margin: 0;
    }
    li {
        border-top: 1px solid whitesmoke;
        display: block;
        padding: 10px;
        position: relative;
    }
    label {
        display: inline-block;
        padding: 10px;
        width: 100%;
        min-height: 18px;
        position: relative;
        font-size: 18px;
        font-weight: bold;
    }
    .toggle {
        display: none;
    }
    input.insert {
        width: calc(100% - 95px);
        border: 0;
        font-size: 24px;
        padding: 10px;
        display: inline-block;
    }
    li:hover > a.remove {
        display: block;
    }
    a.remove {
        display: none;
        position: absolute;
        top: 0;
        right: 0;
        height: 100%;
        bottom: 0;
        margin: auto;
        width: 50px;
        font-size: 32px;
        line-height: 55px;
        text-align: center;
    }
    :focus {
        outline: 0;
    }
</style>