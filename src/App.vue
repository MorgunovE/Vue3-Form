<template>
  <div class="container column">
    <resume-form @block-added="addBlock"></resume-form>
    <resume-view :blocks="blocks"></resume-view>
  </div>
  <div class="container">
    <AppLoader v-if="loading" />
    <ResumeComments
      v-else
      :comments="comments"
      @load-comments="loadComments"
    />
  </div>
</template>

<script>

import ResumeForm from '@/components/ResumeForm'
import ResumeView from '@/components/ResumeView'
import AppLoader from '@/components/AppLoader'
import ResumeComments from '@/components/ResumeComments'
export default {
  name: 'App',
  components: {
    ResumeComments,
    AppLoader,
    ResumeView,
    ResumeForm
  },
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    addBlock(block) {
      this.blocks.push(block)
    },
    async loadComments(){
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.loading = false
    },
  },
}
</script>

<style scoped>

</style>
