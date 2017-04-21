<template lang="html">
  <div class="toolbar">
    <i @click='addNote' class="addNote glyphicon glyphicon-plus"></i>
    <i @click='toggleFavorite' class="star glyphicon glyphicon-star" :class='{like:activeNote.favorite}'></i>
    <i @click='deleteNote' class="deleteNote glyphicon glyphicon-remove"></i>
    <div id="aa">

    </div>
  </div>
</template>

<script>

import { mapActions } from 'vuex'

export default {

  data() {
    return {

    };
  },
  created() {
    
  },
  computed:{
    activeNote(){
      return this.$store.getters.activeNote
    }
  },
  methods: {
    ...mapActions([
      'addNote',
      'deleteNote',
      'toggleFavorite'
    ])

  },
  components: {

  }
};
</script>

<style lang="scss">

  .toolbar {
    width: 80px;
    height: 100%;
    float: left;
    background-color: #30414D;
    color: #767676;
    text-align: center;
    padding: 35px 25px 25px 25px;

    i {
      display: block;
      padding: 10px 0;
      cursor: pointer;
    }
    .like {
      color:red;
    }

  }
</style>
