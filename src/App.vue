<template>
  <div id="app">
    <section id="section1" class="background-section" :style="section1Style">
      <header>
        <h1>Wochenende an der Jade 2024</h1>
      </header>
      <div class="content">
        <p>Die Klausuren sind endlich durch, und das bedeutet nur eins: Es ist Zeit für eine kranke Semesterabschlussfeier! Sommer, Sonne, und eine Umgebung, die besser nicht sein könnte – direkt an der Nordsee. Und das Beste? Das Wochenende an der Jade findet direkt vor unserer Haustür statt. Also einfach Vollgas</p>
        <button @click="scrollTo('section2')" class="scroll-button">Mehr erfahren ↓</button>
      </div>
    </section>

    <section id="section2" class="background-section" :style="section2Style">
      <div class="content">
        <div v-for="(info, index) in partyInfo" :key="index" class="info-section">
          <h3>{{ info.title }}</h3>
          <p>{{ info.details }}</p>
        </div>
        <button @click="scrollTo('section1')" class="scroll-button">Zurück nach oben ↑</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      partyInfo: [
        { title: 'Datum & Zeit', details: '5. Juli 2024, 12:00 Uhr - Open End' },
        { title: 'Dresscode', details: 'Lässige Sommerkleidung' },
        { title: 'Aktivitäten', details: 'Wocheende an der Jade mit Afterparty bei uns' },
        { title: 'Essen & Getränke', details: 'Bier, Bier und Bier ' },
      ],
    };
  },
  computed: {
    section1Style() {
      return {
        'background-image': `url(${require('@/assets/background.jpeg')})`,
        'background-size': 'cover',
        'background-position': 'center',
        'height': '100vh',
      };
    },
    section2Style() {
      return {
        'background-image': `url(${require('@/assets/feuerwerk.jpeg')})`,
        'background-size': 'cover',
        'background-position': 'top',
        'height': '100vh',
      };
    }
  },
  methods: {
    scrollTo(sectionId) {
      const section = document.getElementById(sectionId);
      section.scrollIntoView({ behavior: 'smooth' });
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Roboto:wght@400;700&display=swap');

body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
}

#app {
  text-align: center;
}

.background-section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  color: white;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

header {
  position: fixed;
  top: 20px;
  width: 80%;
  border-radius: 10px;
  font-size: 30px;
  background-color: rgba(0, 150, 136, 0.8);
  color: white;
  padding: 20px;
  font-family: 'Pacifico', cursive;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

header h1 {
  margin: 0;
}

.content {
  max-width: 600px;
  padding: 20px;
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  font-size: 20px;
}

.content h2, .content h3 {
  margin-top: 0;
}

.info-section {
  margin-bottom: 20px;
}

.scroll-button {
  background-color: #009688;
  border: none;
  padding: 10px 20px;
  color: white;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.scroll-button:hover {
  background-color: #00796b;
}

/* Media Queries for responsive design */
@media (max-width: 600px) {
  header {
    width: 90%;
    font-size: 24px;
    padding: 15px;
  }

  .content {
    font-size: 18px;
    padding: 15px;
  }

  .scroll-button {
    padding: 8px 16px;
    font-size: 14px;
  }
}
</style>

