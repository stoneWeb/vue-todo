<template>
  <div id="notes-list">
    <div id="list-header">
      <h2>Notes</h2>
      <div class="btn-group btn-group-justified" role="group">
        <div class="btn-group" role="group">
          <button @click="toggleShow('all')" :class="{active: show === 'all'}" class="btn btn-default" type="button">
            All Notes
          </button>
        </div>

        <div class="btn-group" role="group">
          <button @click="toggleShow('favorite')" :class="{active: show === 'favorite'}" class="btn btn-default" type="button">Favorites</button>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="list-group">
        <a
          href="#"
          v-for="note in filteredNotes"
          @click="updateActiveNote(note)"
          :class="{active: activeNote == note}"
          class="list-group-item">
          <h4 class="list-group-item-heading">
            {{note.title.trim().substring(0, 30)}}
          </h4>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
  import { updateActiveNote, updateShow } from '../vuex/actions'
  import { show, filteredNotes, activeNote } from '../vuex/getters'

  export default {
    vuex: {
      getters: {
        show,
        filteredNotes,
        activeNote
      },
      actions: {
        updateActiveNote,
        updateShow
      }
    },
    methods: {
      toggleShow (show) {
        this.updateShow(show)
      }
    }
  }
</script>
