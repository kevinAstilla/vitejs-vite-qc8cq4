<template>
  <label>word to {{ this.action }}: </label>
  <input type="text" v-model="this.word" @blur="stylize" />
</template>

<script>
export default {
  props: {
    action: String,
    newStyle: String,
    modelValue: Object,
  },
  data() {
    return {
      word: '',
      oldWord: '',
    };
  },
  methods: {
    stylize() {
      let newparagraph = this.modelValue;
      if (this.oldWord != '') {
        let oldpattern = new RegExp(
          `<span style="${this.newStyle}">${this.oldWord}</span>`,
          'gi'
        );
        newparagraph = newparagraph.replace(oldpattern, (match) => {
          return this.oldWord;
        });
      }

      if (this.word != '') {
        let pattern = new RegExp(`${this.word}`, 'gi');
        newparagraph = newparagraph.replace(pattern, (match) => {
          return `<span style="${this.newStyle}">${match}</span>`;
        });
        this.oldWord = this.word;
      }
      this.$emit('updateParagraph', newparagraph);
    },
  },
};
</script>
