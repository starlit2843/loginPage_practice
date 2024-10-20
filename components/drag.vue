
<template>
    <draggable 
        v-model="myArray" 
        item-key="id">
        <template #item="{element}">
            <div>{{ element.name }}</div>
        </template>

    </draggable>
</template>