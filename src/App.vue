<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <button @click="changeLanguage">Change Language</button>
    <ul>
      <li v-for="(lang, index) in languages" :key="index">
        <a @click="changeLanguage(lang)">{{ lang }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'Welcome to My Website',
      message: 'Learn more about us...',
      languages: ['English', 'Amharic', 'Afaan Oromo'],
      selectedLanguage: 'English'
    }
  },
  methods: {
    changeLanguage(lang) {
      this.selectedLanguage = lang;
      this.title = this.languageText[lang].welcomeMessage;
      this.message = this.languageText[lang].aboutMessage;
    }
  },
  computed: {
    languageText() {
      return {
        English: {
          welcomeMessage: 'Welcome to My Website',
          aboutMessage: 'Learn more about us...'
        },
        Amharic: {
          welcomeMessage: 'እንኳን ደህና መጡ',
          aboutMessage: 'በአካባቢ ተጨማሪ ይሆናል...'
        },
        'Afaan Oromo': {
          welcomeMessage: 'Akkaataa irraa fayyadama',
          aboutMessage: 'Barsiisuuf argama...'
        }
      }
    }
  }
}
</script>

<style>
/* Add any necessary styles here */
</style>