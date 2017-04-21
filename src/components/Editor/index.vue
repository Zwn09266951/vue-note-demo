<template lang="html">
  <div class="editor">
    <textarea name="name" v-bind:value="activeNoteText" v-on:input="editNote"></textarea>
  </div>

</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  data() {
    return {
      noteinf: ''
    };
  },
  created() {
    this.noteinf = this.$store.getters.notes.text
  },
  computed: {
    activeNoteText(){
      return this.$store.getters.activeNote.text
    }
  },
  methods: {
    ...mapActions([
      'editNote'
    ])
  },
  components: {}
};
</script>

<style lang="scss">
.editor {
  float: left;
  background: #000;
  width: 30%;
  opacity: .5;
  textarea {
    width: 100%;
    display: block;
  }
  .aa {
    width: 100%;
  }

}
</style>
