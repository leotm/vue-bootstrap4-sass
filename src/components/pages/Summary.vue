<template>
  <div id="summary">
      <div class="blocks-merged">
        <summary-parties></summary-parties>
        <summary-property></summary-property>
        <summary-terms></summary-terms>
        <summary-obligations></summary-obligations>
        <summary-miscellaneous></summary-miscellaneous>
      </div>
      <next-button nextpage="preview"></next-button>
  </div>
</template>

<script>

  import SummaryParties from '../blocks/SummaryParties.vue';
  import SummaryProperty from '../blocks/SummaryProperty.vue';
  import SummaryTerms from '../blocks/SummaryTerms.vue';
  import SummaryObligations from '../blocks/SummaryObligations.vue';
  import SummaryMiscellaneous from '../blocks/SummaryMiscellaneous.vue';
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'summary',
    components : {
      SummaryParties,
      SummaryProperty,
      SummaryTerms,
      SummaryObligations,
      SummaryMiscellaneous,
      NextButton
    },
    data () {
      return {

      };
    }
  };

</script>
