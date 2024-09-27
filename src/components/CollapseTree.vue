<script setup>
import CollapseComponent from './CollapseComponent.vue'
const treeData = [
    {
        id: 1,
        name: 'Models',
        children: [
            { id: 2, name: 'Data warehouse' },
            {
                id: 3,
                name: 'Report samples',
                children: [
                    { id: 4, name: 'Sales performance' },
                    {
                        id: 5, name: 'parent',
                        children: [
                            { id: 11, name: 'child' },
                            { id: 12, name: 'child' },
                            { id: 13, name: 'child' }
                        ]
                    }
                ]
            }
        ]
    },
    {
        id: 6,
        name: 'Statistics',
        children: [
            { id: 7, name: 'For month' },
            { id: 8, name: 'For year' },
            { id: 7, name: 'For week' }
        ]
    }
];

</script>

<template>
    <CollapseComponent v-for="node in treeData" :key="node.id" :node="node" style="width: 300px; background:#f4f4f5" />
</template>

<style scoped></style>