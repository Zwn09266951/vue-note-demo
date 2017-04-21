<template lang="html">
  <div class="notebox">
    <div class="header">
      <h1>记事本</h1>
      <div class="button " @click="all">所有</div>
      <div class="button " @click="favorites">收藏</div>
    </div>
    <ul class="main">
      <li v-for="item in notes" class="mianlist" @click="updateActiveNote(item)" v-bind:class="{active:activeNote == item}"> {{item.text}}</li>
    </ul>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  data() {
    return {
      notes: [],
      show: 'all'
    };
  },
  created() {
    this.notes = this.$store.getters.notes
  },
  computed: {
    notes(){
      if (this.show=='all'){
        return this.$store.getters.notes
      }else if(this.show=='favorites'){
        return this.$store.getters.notes.filter(note=>note.favorite)
      }
    },
    activeNote(){
      return this.$store.getters.activeNote
    }

  },
  methods: {
    ...mapActions([
      'updateActiveNote'
    ]),
    all() {
      this.notes = this.$store.getters.notes
    },
    favorites() {
      console.log(window.location.hash);
      this.notes = this.$store.getters.notes.filter(note=>note.favorite)
    }


  },
  components: {

  }
};
</script>

<style lang="scss">
.notebox {
  width: 40%;
  height: 100%;
  float: left;
  background: #F5F5F5;

  .header {
    padding: 10px 0;
    overflow: hidden;
    text-align: center;
    h1 {
      text-align: center;
      margin-top: 20px;
      margin-bottom: 20px;
      display: block;
      width: 100%;
      text-align: center;
    }
    .button {
      display: inline-block;
      padding: 2px 10px;
      border: 1px solid #666;
      border-radius: 5px;
      font-size: 12px;
      cursor: pointer;
    }
  }
  .main {
    position:relative;
    overflow:scroll;
    height: inherit;
    padding-bottom: 78px;
    li {
      background: #fff;
      margin: 10px;
      padding: 10px;
      height: 45px;
      color:#ddd;
      cursor: pointer;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }
    .active {
      background: rebeccapurple;
    }
  }

}
</style>
