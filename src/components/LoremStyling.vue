<script>
import WordStyleUpdate from './WordStyleUpdate.vue';
export default {
  components: { WordStyleUpdate },
  data() {
    return {
      paragraphhtml:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas aliquam odio ut sapien mollis hendrerit. Fusce in lectus ex. In hac habitasse platea dictumst. Duis aliquam sed arcu at sagittis. Pellentesque suscipit elit a elit dignissim, ornare mattis libero convallis. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque in dictum augue, nec consectetur enim. Pellentesque quis quam ultricies, volutpat nulla sit amet, egestas est. Praesent accumsan ante non dui sollicitudin convallis. Etiam facilisis finibus lectus, euismod gravida ipsum ultricies at.',
    };
  },
  methods: {
    updateParagraph(newParagraph) {
      this.paragraphhtml = newParagraph;
    },
  },
};
</script>

<template>
  <WordStyleUpdate
    v-model="this.paragraphhtml"
    action="underline"
    new-style="text-decoration: underline"
    @updateParagraph="updateParagraph($event)"
  />
  <br />
  <WordStyleUpdate
    v-model="this.paragraphhtml"
    action="bold"
    new-style="font-weight: bold"
    @updateParagraph="updateParagraph($event)"
  />
  <br />
  <WordStyleUpdate
    v-model="this.paragraphhtml"
    action="red"
    new-style="color: red"
    @updateParagraph="updateParagraph($event)"
  />
  <br />

  <div v-html="this.paragraphhtml"></div>
</template>
