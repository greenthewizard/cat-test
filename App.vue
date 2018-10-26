<template>
    <div id="app">
        <h1>Cat Village</h1>
        <ul id="resources">
            <li class="resource" v-for="r in resources" :key="r.name">
                {{ r.name }}: {{ r.total }}
            </li>
        </ul>
        <h2>Village</h2>
        <draggable element="ul" class="cat-list" v-model="catList" :options="{group: 'cats', sort: false}">
            <li class="cat" v-for="cat in catList" :key="cat.name">
                {{ cat.name }}
            </li>
        </draggable>
        <ul id="locations">
            <li class="location" v-for="loc in locations" :key="loc.name">
                <h2>{{ loc.name }}</h2>
                <draggable element="ul" class="cat-list" v-model="loc.catList" :options="{group: 'cats', sort: false}">
                    <li v-for="cat in loc.catList" :key="cat.name">
                        {{ cat.name }}
                    </li>
                </draggable>
            </li>
        </ul>
    </div>
</template>

<script>
import draggable from 'vuedraggable';

export default {
    components: {
        draggable
    },
    data: () => {
        return {
            resources: [
                {
                    name: "wood",
                    total: 4
                },
                {
                    name: "stone",
                    total: 2
                },
                {
                    name: "chow",
                    total: 3
                }
            ],
            catList: [
                {
                    name: "Fluffykins"
                },
                {
                    name: "Batcat"
                }
            ],
            locations: [
                {
                    name: "Wilderness",
                    catList: []
                },
                {
                    name: "Lumbermill",
                    catList: []
                }
            ]
        }
    }
}
</script>

<style lang="sass">
body
    background: #efefef
    color: #2b2b2b
.cat-list
    width: 100px
    height: 100px
    background: #e2e2e2
.location, .cat-list
    list-style: none
</style>
