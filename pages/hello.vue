<template>
  <article>
    <h1>{{ page.title }}</h1>
    <nuxt-content :document="page" />
    {{ rawContent }}
  </article>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const page = await $content('hello').fetch()

    return {
      page
    }
  },

  data: () => ({
    rawContent: ''
  })

  // async created () {
  //   const fileUrl = `_content/${this.page.path}${this.page.extension}`
  //   this.rawContent = await fetch(fileUrl).then(res => res.text())
  //   // console.log('file', file)
  // }
}
</script>
