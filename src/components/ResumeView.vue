<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'resume-' + block.type"
        v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>
      Add first block to see result
    </h3>
  </div>
</template>

<script>
  import ResumeAvatar from '@/components/parts/ResumeAvatar'
  import ResumeSubtitle from '@/components/parts/ResumeSubtitle'
  import ResumeText from '@/components/parts/ResumeText'
  import ResumeTitle from '@/components/parts/ResumeTitle'
  
  export default {
    name: "ResumeView",
    props: ['blocks'],
    components: {
      ResumeAvatar,
      ResumeSubtitle,
      ResumeText,
      ResumeTitle
    },
  }
</script>

<style scoped>

</style>
