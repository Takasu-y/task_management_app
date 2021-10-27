<template>
    <v-row>
        <task-section
            v-for="section in sections"
            :key="section.id"
            :section="section"
            class="task-section"
        ></task-section>
    </v-row>
</template>

<script>

import taskSection from './taskSection.vue'

let sectionId = 1;

export default {
    name: "taskManager",
    components: {
        taskSection,
    },
    data: ()=> ({
        sections: [
            {
                id: sectionId++,
                title: "Monday",
            },
            {
                id: sectionId++,
                title: "Tuesday",
            },
            // {
            //     id: sectionId++,
            //     title: "Wednesday",
            // },
        ],
    }),
};
</script>
