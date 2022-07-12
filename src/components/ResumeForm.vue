<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type"> Type of Block</label>
      <select id="type" v-model="type">
        <option value="title">Title</option>
        <option value="subtitle">subtitle</option>
        <option value="avatar">Avatar</option>
        <option value="text">Text</option>
      </select>
    </div>
    <div class="form-control">
      <label for="value">Value</label>
      <textarea id="value" rows="3" v-model="value"></textarea>
    </div>
    <button
    class="btn primary"
    :disabled="isValid"
    >Add
    </button>
  </form>
</template>

<script>
  export default {
    name: "ResumeForm",
    emits: ['block-added'],
    data() {
      return {
        type: 'title',
        value: ''
      }
    },
    computed: {
      isValid() {
        return this.value.length < 3
      },
    },
    methods: {
      submit() {
        this.$emit('block-added', {
          type: this.type,
          value: this.value,
          id: Date.now()
        })
        this.value = ''
        this.type = 'title'
      },
    },
  }
</script>

<style scoped>

</style>
