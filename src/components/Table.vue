<template>
    <div>
        <h1>My Table</h1>
        <TableComponent :data="tableData" :columns="tableColumns" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import TableComponent from './TableComponent.vue';

const tableData = ref([
    {
        name: 'John Brown',
        age: 32,
        address: 'New York No. 1 Lake Park',
        tags: [
            { text: 'nice', color: '#4CAF50' },
            { text: 'developer', color: '#2196F3' }
        ]
    },
    {
        name: 'Jim Green',
        age: 42,
        address: 'London No. 1 Lake Park',
        tags: [{ text: 'loser', color: '#F44336' }]
    },
    {
        name: 'Joe Black',
        age: 32,
        address: 'Sidney No. 1 Lake Park',
        tags: [
            { text: 'cool', color: '#FFEB3B' },
            { text: 'teacher', color: '#FF9800' }
        ]
    }
]);

const tableColumns = ref([
    { header: 'Name', key: 'name', editable: true },
    { header: 'Age', key: 'age', editable: true },
    { header: 'Address', key: 'address', editable: true },
    { header: 'Tags', key: 'tags', editable: false },
]);
</script>