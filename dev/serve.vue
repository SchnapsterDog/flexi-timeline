<script>
import Vue from 'vue';
// Uncomment import and local "components" registration if library is not registered globally.
import { FlexiTimeline } from '@/entry.esm';

export default Vue.extend({
  name: 'ServeDev',
  components: {
   FlexiTimeline,
  }
});
</script>

<template>
  <div id="app">
    <flexi-timeline />
  </div>
</template>
