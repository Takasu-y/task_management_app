<template>
    <v-card
        width="320"
        min-width="320"
        class="mx-3 pa-3"
        elevation="10"
    >
        <v-card-text class="d-flex justify-center">
            <v-text-field
                v-if="section.editable"
                v-model="section.title"
                filled
                @keydown.enter="editFixSectionTitle"
                placeholder="セクション名を入力して下さい"
                >{{section.title}}

            </v-text-field>
            <h2
                v-else
                @dblclick="editSectionTitle"
            >{{section.title}}</h2>

        </v-card-text>
        <v-divider class="mx-4 py-1"></v-divider>
        <v-list
            class="overflow-y-auto mb-4"
            width="100%"
            max-height="60vh">

            <draggable
            v-model="tasks"
            draggable=".item"
            group="items"
            >
                <task
                    v-for="task in tasks"
                    :key="task.id"
                    :task="task"
                    class="item"
                    @edit="editTask"
                    @edit-fix="editFixTask"
                    @favorite="favoriteTask"
                    @check="checkTask"
                    @delete="deleteTask"
                ></task>
            </draggable>
        </v-list>
        <v-hover>
            <v-card
                @click="addTask"
                class="pa-2"
            >
                    <v-icon>mdi-plus-circle</v-icon>タスクカードを追加
            </v-card>
        </v-hover>
    </v-card>
</template>

<script>
import task from './task.vue'
import draggable from 'vuedraggable'

let todoId = 1;

export default {
    name: "taskSection",
    components: {
        task,
        draggable,
    },
    data() {
        return {
            section: {
                title: "",
                editable: true,
            },
            tasks: [
                // {
                //     id: todoId++,
                //     title: "朝ごはんを食べる",
                //     body: "プロテインも飲む",
                //     editable: false,
                //     favorite: false,
                //     check: false,
                // },
                // {
                //     id: todoId++,
                //     title: "昼ごはんを食べる",
                //     body: "中華かラーメンを食べる",
                //     editable: false,
                //     favorite: false,
                //     check: false,
                // },
                // {
                //     id: todoId++,
                //     title: "夜ごはんを食べる",
                //     body: "サラダのみにする",
                //     editable: false,
                //     favorite: false,
                //     check: false,
                // },
            ]
        }
    },
    methods: {
        addTask(){
            this.tasks.push({
                id: todoId++,
                title: "",
                body: "",
                editable: true,
                favorite: false,
                check: false,
            })
        },
        editSectionTitle() {
            this.section.editable = !this.section.editable;
        },
        editFixSectionTitle(event) {
            if(this.section.title.length > 0){
                if(event.keyCode === 13){
                    this.section.editable = !this.section.editable;
                }
            }
        },
        editTask(taskObject){
            taskObject.editable = !taskObject.editable;
        },
        editFixTask(taskObject, event){
            if(event.keyCode === 13){
                if(taskObject.title.length >0 && taskObject.body.length > 0){
                    taskObject.editable = !taskObject.editable;
                }else{
                    alert("タスクを入力して下さい");
                }
            }
        },
        favoriteTask(taskObject){
            taskObject.favorite = !taskObject.favorite;
        },
        checkTask(taskObject){
            taskObject.check = !taskObject.check;
        },
        deleteTask(taskObject){
            this.tasks = this.tasks.filter(task => task.id !== taskObject.id);
        },
    },
};
</script>
