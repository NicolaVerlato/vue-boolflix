<template>
    <div class="header">
        <h1>BOOLFLIX</h1>

        <div class="search">
            <input type="text" placeholder="Cerca un film" v-model="searchText" @keyup.enter="$emit('startSearching', searchText)">
            <button @click="$emit('startSearching', searchText)">Search</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data(){
        return{
            searchText: ''
        }
    }
}
</script>

<style lang="scss" scoped>
.header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 40px;
    background-color: black;

    h1{
        color: red;
    }

    .search{
        color: white;

        input{
            padding: 3px;
        }
        button{
            padding: 3px;
        }
    }
}
</style>