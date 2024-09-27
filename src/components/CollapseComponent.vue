<template>
    <li class="body-list">
        <div @click="toggle" class="node-label">
            <span v-if="hasChildren" class="arrow" :class="{ open: isOpen }">
                <svg width="8" height="10" viewBox="0 0 18 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M18 11L2.14577e-06 21.3923V0.607695L18 11Z" fill="#231F20" />
                </svg>
            </span>
            {{ node.name }}
        </div>
        <ul v-if="hasChildren && isOpen">
            <CollapseComponent v-for="child in node.children" :key="child.id" :node="child" />
        </ul>
    </li>
</template>
<script setup>
import { ref } from 'vue';

const props = defineProps({
    node: Object
});

const isOpen = ref(false);

const toggle = () => {
    isOpen.value = !isOpen.value;
};

const hasChildren = props.node.children && props.node.children.length > 0;
</script>
<style scoped>
.node-label {
    cursor: pointer;
    padding: 5px 24px;
    user-select: none;
    display: flex;
    align-items: center;
}

.arrow {
    display: inline-block;
    transition: transform 0.3s ease;
    margin-right: 5px;
}



.arrow.open {
    transform: rotate(90deg);
}

li {
    list-style-type: none;
}

ul {
    list-style-type: none;
    padding-left: 20px;
}
</style>