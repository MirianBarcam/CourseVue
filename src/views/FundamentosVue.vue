<template>
  <div class="fundamentosVue">
    <aprender-vue></aprender-vue>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import AprenderVue from "@/components/AprenderVue.vue"; // @ is an alias to /src

@Component({
  components: {
    AprenderVue,
  },
})
export default class FundamentosVue extends Vue {}
</script>
