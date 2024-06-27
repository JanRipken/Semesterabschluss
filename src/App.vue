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
        <button @click="scrollTo('section3')" class="scroll-button">Zeitleiste ansehen ↓</button>
      </div>
    </section>

    <section id="section3" class="background-section" :style="section3Style">
      <div class="content">
        <h2>Programmablauf</h2>
        <ul class="timeline">
          <li v-for="(event, index) in timeline" :key="index" class="timeline-item">
            <h3>{{ event.time }}</h3>
            <p>{{ event.activity }}</p>
          </li>
        </ul>
        <button @click="scrollTo('section2')" class="scroll-button">Zurück nach oben ↑</button>
        <button @click="scrollTo('section4')" class="scroll-button">Anreiseinformationen ↓</button>
      </div>
    </section>

    <section id="section4" class="background-section" :style="section4Style">
      <div class="content">
        <h2>Ort & Anreise</h2>
        <div class="map-container">
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d602.282562854184!2d8.110818534503748!3d53.517629804975385!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47b6930947ae5291%3A0x9d72643092521aa7!2sMoor%20Beauty!5e1!3m2!1sde!2sde!4v1719472841141!5m2!1sde!2sde" width="700" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
        <button @click="scrollTo('section3')" class="scroll-button">Zurück zur Zeitleiste ↑</button>
        <button @click="scrollTo('section5')" class="scroll-button">Zur Umfrage ↓</button>
      </div>
    </section>

    <section id="section5" class="background-section" :style="section5Style">
      <div class="content">
        <h2>Teilnahmebestätigung</h2>
        <div class="form-container">
          <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSd1vwXNNb1fHw3AMecxyLP4QKFvARw69hBAd8Z8jOQDBiCOxQ/viewform?embedded=true" width="640" height="466" frameborder="0" marginheight="0" marginwidth="0">Wird geladen…</iframe>
        </div>
        <button @click="scrollTo('section4')" class="scroll-button">Zurück zur Karte ↑</button>
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
        { title: 'Datum & Zeit', details: '5. Juli 2024, 13:00 Uhr - Open End' },
        { title: 'Dresscode', details: 'Lässige Sommerkleidung' },
        { title: 'Aktivitäten', details: 'Besuch des Wochenende an der Jade' },
        { title: 'Der Plan', details: 'Vortrinken und Afterparty bei uns' },
        { title: 'Info', details: 'Wir stellen nur Bier, Charly und ein paar Kleinigkeiten. Solltet ihr etwas anderes wollen, bringt es bitte selbst mit.' },
      ],
      timeline: [
        { time: '13:00 Uhr', activity: 'Treffen bei uns' },
        { time: '16:00 Uhr', activity: 'Besuch des Wocheende an der Jade' },
        { time: 'ab 21:00 Uhr', activity: 'Afterparty' },
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
    },
    section3Style() {
      return {
        'background-image': `url(${require('@/assets/hafen.jpeg')})`,
        'background-size': 'cover',
        'background-position': 'center',
        'height': '100vh',
      };
    },
    section4Style() {
      return {
        'background-image': `url(${require('@/assets/schiffe.jpeg')})`,
        'background-size': 'cover',
        'background-position': 'center',
        'height': '100vh',
      };
    },
    section5Style() {
      return {
        'background-image': `url(${require('@/assets/ende.jpeg')})`,
        'background-size': 'cover',
        'background-position': 'center',
        'height': '100vh',
      };
    },
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
  width: 80vw;
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
  margin: 5px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.scroll-button:hover {
  background-color: #00796b;
}

.timeline {
  list-style: none;
  padding: 0;
}

.timeline-item {
  background-color: rgba(0, 150, 136, 0.8);
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 10px;
}

.map-container {
  width: 100%;
  height: 450px;
  margin-bottom: 20px;
}

.form-container {
  width: 100%;
  height: calc(50vh - 60px); /* subtract header height if applicable */
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

iframe {
  width: 100%;
  height: 100%;
  border: 0;
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

  .map-container {
    height: 300px;
  }
}
</style>

