<template>
  <div id="note-editor">
    <div class="from-group">
      <input
       type="text"
       name="title"
       class="title form-control"
       placeholder="请输入标题"
       @input="updateNote"
       v-model="currentNote.title">
      <textarea
        v-model="currentNote.content"
        name="content"
        class="form-control"
        row="3"
        placeholder="请输入正文"
        @input="updateNote"
      ></textarea>
    </div>
  </div>
</template>

<script>
import { editNote } from '../vuex/actions'
import { activeNote } from '../vuex/getters'

export default {
  vuex: {
    getters: {
      activeNote
    },
    actions: {
      editNote
    }
  },
  computed: {
    currentNote: activeNote
  },
  methods: {
    updateNote () {
      this.editNote(this.currentNote)
    }
  }
}
</script>

<style lang="css">
</style>
