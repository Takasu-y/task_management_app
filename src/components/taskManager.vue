<template>
<div class="d-flex">
    <v-list
    class="d-flex align-start overflow-x-auto"
    >
        <task-section
            v-for="i in counter"
            :key="i"
        ></task-section>
    </v-list>
    <v-btn
        @click="counter +=1"
        class="pa-2 mt-6"
    >
        <v-icon>mdi-plus-circle</v-icon>セクションを追加
    </v-btn>
</div>
</template>

<script>

import taskSection from './taskSection.vue'

export default {
    name: "taskManager",
    components: {
        taskSection,
    },
    data: ()=> ({
        counter: 1,
    }),
};
</script>
