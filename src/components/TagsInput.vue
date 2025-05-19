<template>
    <div v-for="(tag, index) in tags">
        {{ tag }}
        <a @click.prevent="removeTag(index)" href="#">&times;</a>
    </div>
    <hr />

    {{ newTag }}

    <input 
        type="text" 
        v-model.trim="newTag"
        @keydown.enter="addNewTag"
        @keydown.delete="removeLastTag"
        @keydown.tab.prevent="addNewTag"
        :class="{ 'tag-exits': isTagExits }"
    />
</template>

<script>
export default {
    data: () => ({
        tags: ["vue", "react", "angular"],
        newTag: ""
    }),
    watch: {
        newTag (newVal) {
            if (newVal.indexOf(",") > -1) {
                this.newTag = this.newTag.slice(0, -1)
                this.addNewTag()
            }
        }
    },
    computed: {
        isTagExits () {
            return this.tags.includes(this.newTag)
        }
    },
    methods: {
        addNewTag () {
            if (this.newTag && !this.isTagExits) {
                this.tags.push(this.newTag)
                this.newTag = ""
            }
        },
        removeTag (index) {
            this.tags.splice(index, 1)
        },
        removeLastTag () {
            if (this.newTag.length === 0) {
                this.removeTag(this.tags.length - 1)
            }
        }
    }
};
</script>

<style scoped>
.tag-exits {
    color: red;
    text-decoration: line-through;
}
</style>