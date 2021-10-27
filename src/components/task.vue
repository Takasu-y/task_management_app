<template>
    <v-list-item
        min-height="100">
        <v-card
            elevation="10"
            min-width="100%"
            :key="task.id"
            class="task mb-1 pa-2"
            >
                <v-card
                    v-if="task.editable"
                >
                    <v-text-field
                        placeholder="タイトルを入力して下さい"
                        v-model="task.title"
                        filled
                        @keydown.enter="$emit('edit-fix', task, $event)"
                    >
                        {{task.title}}
                    </v-text-field>
                    <v-text-field
                        placeholder="内容を入力して下さい"
                        v-model="task.body"
                        filled
                        @keydown.enter="$emit('edit-fix', task, $event)"
                    >
                        {{task.body}}
                    </v-text-field>
                </v-card>

                <v-card
                    v-else
                    @dblclick="$emit('edit', task)"
                >
                    <v-card-title>{{task.title}}</v-card-title>
                    <v-card-text>{{task.body}}</v-card-text>
                </v-card>
                <v-card-actions class="d-flex justify-end">
                    <v-icon @click="$emit('edit', task)">mdi-pencil</v-icon>
                    <v-icon @click="$emit('favorite', task)" :class="{ 'lime--text': task.favorite}">mdi-star</v-icon>
                    <v-icon @click="$emit('check', task)" :class="{ 'teal--text': task.check}">mdi-check-bold</v-icon>
                    <v-icon @click="$emit('delete', task)">mdi-delete</v-icon>
                </v-card-actions>
            </v-card>
    </v-list-item>
</template>

<script>

export default {
    name: "task",
    props: {
        task: {
            type: Object, //データ型
            required: true, //データ渡し必須
        },
        favorite: {
            type: Boolean,
            required: true,

        },
        check: {
            type: Boolean,
            required: true,
        },
    },
};
</script>