<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My Website</a>
      <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-bs-toggle="dropdown" aria-expanded="false">
          {{ selectedLanguage }}
        </button>
        <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <li v-for="(lang, index) in languages" :key="index">
            <a class="dropdown-item" @click="changeLanguage(lang)">{{ lang }}</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div class="container mt-5">
    <h1>{{ getText('welcomeMessage') }}</h1>
    <p>{{ getText('aboutMessage') }}</p>
    <!-- Add more elements with language-specific text as needed -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedLanguage: 'English',
      languages: ['English', 'Amharic', 'Afaan Oromo'],
      languageText: {
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
    };
  },
  methods: {
    changeLanguage(language) {
      this.selectedLanguage = language;
    },
    getText(key) {
      return this.languageText[this.selectedLanguage][key];
    }
  }
};
</script>

<style scoped>
.dropdown {
  position: fixed;
  top: 10px; /* Adjust top position as needed */
  right: 10px; /* Adjust right position as needed */
  z-index: 1000; /* Ensure it's above other content */
}
</style>
