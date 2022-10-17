<template>
  <div>
    <ring-loader :loading="isLoading" :color="'#501c94'"></ring-loader>
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import api from "@/api";
import RingLoader from "vue-spinner/src/RingLoader.vue";
import PxAssetsTable from "@/components/PxAssetsTable";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",

  components: {
    PxAssetsTable,
    RingLoader,
  },

  data() {
    return {
      isLoading: false,
      assets: [],
    };
  },

  created() {
    this.isLoading = true;
    api.getAssets()
      .then((assets) => (this.assets = assets))
      .finally(() => (this.isLoading = false));
  },
};
</script>
