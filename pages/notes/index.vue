<template>
  <main>
    <h1>My Digital Garden Notes</h1>
    <p v-show="selectedTag">Filtered by: {{ selectedTag }} <button @click="selectedTag = ''">clear</button></p>
    <ul>
      <li v-for="note in visibleNotes" :key="note.slug">
        <nuxt-link :to="`/notes/${note.slug}`">
          <div>
            <strong>{{ note.title }}</strong>
            <span>{{ new Date(note.publishOn) }}</span>
          </div>
        </nuxt-link>
        <div>
          <button @click="selectedTag = tag" v-for="tag in note.tags" :key="tag">{{tag}}</button>
        </div>
      </li>
    </ul>
  </main>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  async asyncData({ $content }) {
    const notes = await $content("notes")
      .sortBy("publishOn", "desc")
      .fetch<any>();
    return {
      notes,
    }
  },
  data: () => ({
    selectedTag: "",
  }),
  computed: {
    visibleNotes() {
      if (!this.selectedTag) return this.notes;
      return this.notes.filter(({ tags }) => {
        if (!Array.isArray(tags)) return false;
        return tags.includes(this.selectedTag)
      });
    }
  }
});
</script>

<style scoped></style>
