<template>
  <div id="preview">
    <preview-content></preview-content>
    <div class="bottom-action">
        <a href="" @click.prevent="goToDownloadUrl" class="asta-btn">
          Continue &amp; download
          <i class="fa fa-arrow-right"></i>
        </a>
        <br>
        <button class="asta-btn back-btn" @click="back">
          <span class="fa fa-arrow-left"></span> Back
        </button>
    </div>
  </div>
</template>

<script>

  import Vue from "vue";
  import PreviewContent from '../blocks/PreviewContent.vue';

  export default {
    name: 'preview',
    components: {
      PreviewContent
    },

    methods: {
      back() {
          this.$router.push({ name: 'summary' });
      },
      goToDownloadUrl() {
        let uuid = Vue.ls.get('uuid');
        Vue.ls.remove('uuid');

        window.location.href= this.$store.state.thankYouPage+'/'+uuid;
      },
    },
    activated() {
        let validPages = this.$store.getters.getValidPages;

        if (validPages.length < 6) {
            this.$router.push({ name: 'summary' });
        }
    }
  };

</script>
