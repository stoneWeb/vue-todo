<template>
  <div id="toolbar">
    <span @click="newNote">添加</span>
    <span @click="toggleFavorite" :class="{starred: activeNote.favorite}">喜欢</span>
    <span @click="deleteNote">删除</span>
  </div>
</template>
<script>
  import { newNote, deleteNote, toggleFavorite } from '../vuex/actions'
  import { activeNote } from '../vuex/getters'

  export default {
    vuex: {
      getters: {
        activeNote
      },
      actions: {
        newNote,
        deleteNote,
        toggleFavorite
      }
    }
  }
</script>

<style>
  #toolbar{
    position: absolute;
    top: 0;
    left: 0;
    width: 80px;
    height: 100%;
    background-color: #30414D;
    color: #767676;
    padding: 35px 25px 25px 25px;
  }
  #toolbar .starred{
    color: #F7AE4F
  }
  #toolbar span{
    font-size: 13px;
    margin-bottom: 35px;
    cursor: pointer;
    line-height: 80px;
    display: block;
  }
</style>
