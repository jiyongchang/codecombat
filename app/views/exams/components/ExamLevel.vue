<template>
  <div class="exam-level">
    <a
      :href="levelLink"
      target="_blank"
    >{{ $t('exams.level_num', { num: index }) }}</a>
  </div>
</template>

<script>
export default {
  name: 'ExamLevel',
  props: {
    level: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    language: {
      type: String,
      required: true,
    },
  },
  computed: {
    levelLink () {
      return `/play/level/${this.level.slug}?course=${this.level.courseId}&course-instance=${this.level.instanceId}&codeLanguage=${this.language}`
    },
  },
  methods: {
    makeTitle (slug) {
      const words = slug.split('-')
      for (let i = 0; i < words.length; i++) {
        const word = words[i]
        words[i] = word.charAt(0).toUpperCase() + word.slice(1)
      }
      return words.join(' ')
    },
  },
}
</script>

<style>

</style>