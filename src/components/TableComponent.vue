<template>
    <div class="table-container">
        <table class="custom-table">
            <thead>
                <tr>
                    <th v-for="(col, index) in columns" :key="index">{{ col.header }}</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, rowIndex) in data" :key="rowIndex">
                    <td v-for="(col, colIndex) in columns" :key="colIndex">
                        <template v-if="col.key === 'tags'">
                            <span v-for="(tag, tagIndex) in item[col.key]" :key="tagIndex" class="tag"
                                :style="{ borderColor: tag.color, color: tag.color, backgroundColor: getAlfaColor(tag.color) }">
                                {{ tag.text }}
                            </span>
                        </template>
                        <template v-else>
                            <input v-if="col.editable" type="text" v-model="item[col.key]" @blur="updateItem(item)" />
                            <span v-else>{{ item[col.key] }}</span>
                        </template>
                    </td>
                    <td>
                        <button @click="deleteRow(rowIndex)" class="action-btn">Delete</button>
                        <button @click="invite(item)" class="action-btn">Invite - {{ item.name }}</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    data: {
        type: Array,
        required: true,
    },
    columns: {
        type: Array,
        required: true,
    },
});

const updateItem = (item) => {
    console.log('Updated item:', item);
};

const deleteRow = (index) => {
    props.data.splice(index, 1);
};

const invite = (item) => {
    alert(`Invited ${item.name}`);
};

const getAlfaColor = (bgColor) => {
    const color = bgColor.toLowerCase();
    return color + '1a';
};
</script>

<style scoped>
.table-container {
    width: 100%;
    overflow-x: auto;
}

.custom-table {
    width: 100%;
    border-collapse: collapse;
}

.custom-table th,
.custom-table td {
    border-bottom: 1px solid #e8e8e8;
    padding: 12px;
    text-align: left;
}

.custom-table th {
    font-weight: 600;
}

.custom-table th {
    background-color: #fafafa;
}

input[type='text'] {
    width: 100%;
    border: 1px solid transparent;
    border-radius: 4px;
    padding: 8px;
    outline: none;
    transform: translate(-8px)
}

input:focus {
    border-color: #0ea5e9;
}

button.action-btn {
    border: none;
    background: transparent;
    outline: none;
    color: #0d97d7;
    border-radius: 4px;
    padding: 8px;
    margin-left: 8px;
}

button.action-btn:hover {
    background: #0ea4e948;
}

.tag {
    display: inline-block;
    margin: 0 5px;
    padding: 2px 6px;
    border: 1px solid;
    border-radius: 4px;
    color: #ffffff;
    background: #ffffff42;
}
</style>