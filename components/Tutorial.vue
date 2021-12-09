<template>
  <div v-if="content">
    {{content.pageTitle}}
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  fetchKey: 'Home',
  async fetch() {
    await new Promise(resolve => setTimeout(resolve, 1000));
    this.page = {
      umbraco: {
        content: {
          byUrl: {
            pageTitle: 'Mocked',
            address: '',
            contentGrid: '{}',

          }
        }
      }
    }
  },
  data() {
      return {
        page: {} as any
      }
  },
  computed: {
    content(): any {
      return this.page?.umbraco?.content?.byUrl
    }
  },
})
</script>
