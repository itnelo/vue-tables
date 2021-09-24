<template>
    <div id="app">
        <h1>Click by table row</h1>

        <!--    <hr />-->
        <Table
            v-bind:tableData="firstTableData"
            v-on:moved-table-row="movedFirstTableRow"
        />

        <Table
            v-bind:tableData="secondTableData"
        />
    </div>
</template>

<script>
import firstTableUsers from './firstTableData.json';
import Table from '@/components/Table';

export default {
    name: 'App',
    data() {
        return {
            secondTableData: [
                { name: 'Paul', id: 6 },
                { name: 'Mike', id: 7 },
                { name: 'Alex', id: 8 },
                { name: 'Natasha', id: 9 },
                { name: 'Katya', id: 10 },
            ],
            firstTableData: firstTableUsers,
        };
    },
    mounted() {
        // this.firstUsers = JSON.parse(firstTableUsers);
        // // this.movedFirstTableRow();
        // this.movedSecondTableRow();
    },
    methods: {
        movedFirstTableRow(name, index) {
            let firstArrayItem  = { ...this.firstTableData[index] };
            this.firstTableData = this.firstTableData.filter(t => t.name !== name);
            this.secondTableData.push(firstArrayItem);
        },
    },
    components: {
        Table,
    },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Display&display=swap');


#app {
    font-family: 'Red Hat Display', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

h1 {
    color: #f3f3f3;
}

.tables {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.table {
    margin: 10px;
    color: #000;
}

.table th,
.table td {
    padding: 10px 20px;
    border: 2px solid #fff;
}

table.table tr {
    transition: .4s cubic-bezier(0.55, 0.43, 0.18, 1.54);
}

table.table tr:not(:first-child):hover {
    background: #e3e3e3;
    transform: scale(.9);
    border: none;
}

.table td {
    cursor: pointer;
}

.table .cell-name {
    width: 150px;
}

table.table tr:not(:first-child) {
    background: #fbfbfb;
}
</style>
