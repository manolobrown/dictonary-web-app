<script setup>
import Audio from "./Audio.vue";
import Noun from "./Noun.vue";
import Verb from "./Verb.vue";
const props = defineProps({ definition: Object });
</script>
<template>
  <Audio :definition="definition[0]" />
  <Noun :definition="definition[0]" />
  <Verb :definition="definition[0]" />
</template>
