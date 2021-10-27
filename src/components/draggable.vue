<template>
    <div class="row">
        <draggable v-model="items" draggable=".item" group="items">
            <v-card v-for="item in items"
            :key="item.id"
            class="item"

            >

                <v-card-title>{{item.title}}</v-card-title>
                <v-card-text>{{item.content}}</v-card-text>
                <v-card-actions>
                    <v-btn><v-icon>mdi-pencil</v-icon></v-btn>
                    <v-btn><v-icon>mdi-star</v-icon></v-btn>
                    <v-btn><v-icon>mdi-delete</v-icon></v-btn>
                    <v-btn><v-icon>mdi-check-bold</v-icon></v-btn>
                </v-card-actions>
            </v-card>
        </draggable>


    </div>
</template>

<script>
// import Vue from 'vue'
import draggable from 'vuedraggable'

export default {
    name: "Draggable",
    components: {
        draggable,
    },
    data() {
        return {
            items: [
                {
                    id: 1,
                    title: "ITEM - 1",
                    content: "ITEM - 1 - content",
                },
                {
                    id: 2,
                    title: "ITEM - 2",
                    content: "ITEM - 2 - content",
                },
                {
                    id: 3,
                    title: "ITEM - 3",
                    content: "ITEM - 3 - content",
                },
                {
                    id: 4,
                    title: "ITEM - 4",
                    content: "ITEM - 4 - content",
                },
            ],
            items2: [
                {
                    id: 5,
                    title: "ITEM - 5",
                    content: "ITEM - 5 - content",
                },
                {
                    id: 6,
                    title: "ITEM - 6",
                    content: "ITEM - 6 - content",
                },
                {
                    id: 7,
                    title: "ITEM - 7",
                    content: "ITEM - 7 - content",
                },
                {
                    id: 8,
                    title: "ITEM - 8",
                    content: "ITEM - 8 - content",
                },
            ],
        }
    },
    methods: {
        showItems() {
        alert(this.items.map(val => { return val.id }))
        }
    }
}
</script>
