<script setup lang="ts">
import { ref } from "vue";

const credentials = ref(false);
const links = ref(false);

const toggleCredentials = () => {
  credentials.value = !credentials.value;
};

const toggleLink = () => {
  links.value = !links.value;
};
</script>

<template>
  <div class="Intro">
    <header class="header">
      Roan Carmelo G. Morgado
    </header>
    <h1>BSCpE-4A</h1>
  </div>

  <main class="Contents">
    <section class="card About-me">
      <h2 class="card-title text-2xl font-bold">About Me</h2>
      <p>I am a humble (HUMBLE!?) Computer Engineering student from CSU Carig trying to design a website</p>
      <p>I want to be a full stack developer but unfortunately I don't have a knack for designs</p>
    </section>

    <section class="card Skills">
      <h2 class="card-title text-2xl font-bold">Skills & Interest</h2>
      <p>These are my current skills</p>
      <p>
        Programming Languages: C, C++, Java, Python<br>
        Hardware Skills: PCB Design, Embedded Systems, 3D Design, to be continued
      </p>
    </section>
  </main>

  <div class="Catto" @click="toggleCredentials" title="psst Click me">
    <img class="catgif" src="/catdance.gif" alt="Dancing Cat" />
    <span class="click-hint">click me ^</span>
  </div>

  <div class="cattosad" @click="toggleLink" title="pst Click me">
    <img class="catsad" src="/cattosad.png" alt="Sad Cat" />
  </div>

  <div class="CatSpin">
    <img class="catspin" src="/spinn.gif" alt="Cat Spin" />
  </div>

  <Transition name="fade">
    <div v-if="credentials" class="credentials-popup">
      <div class="popup-header">
        <h2>Achievements !!</h2>
        <button class="close-btn" @click.stop="credentials = false">&times;</button>
      </div>
      <div class="popup-body">
        <ul>
          <li>Dean's Lister 2-2025-2026</li>
          <li>Regional ITE Convention: General Programming Champion</li>
          <li>National CodeChum Programming Season 2: Top 4</li>
          <li>Regional CpE Challenge 2025: C Programming 1st Runner Up</li>
        </ul>
      </div>
    </div>
  </Transition>

  <Transition name="fade">
    <div v-if="links" class="credentials-popup">
      <div class="popup-header">
        <h2>Links wowowowo</h2>
        <button class="close-btn" @click.stop="links = false">&times;</button>
      </div>
      <div class="popup-body">
        <ul>
          <li>Facebook: <a href="https://www.facebook.com/roan.morgado.39" target="_blank" rel="noopener noreferrer">Roan Morgado</a></li>
          <li>Email: <a href="mailto:roancarmelomorgado@gmail.com">roancarmelomorgado@gmail.com</a></li>
          <li>Github: <a href="https://github.com/Melomorgado" target="_blank" rel="noopener noreferrer">Melomorgado</a></li>
        </ul>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.Intro {
  text-align: center;
  background-color: slategray;
  padding: 1rem 0;
}

.header {
  font-size: 40px;
}

.Contents {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  max-width: 1000px;
  margin: 1rem auto 0;
  padding: 0 1.5rem 6rem;
}

@media (max-width: 768px) {
  .Contents {
    grid-template-columns: 1fr;
  }
}

.card {
  background-color: #22282f;
  border: 2px solid #3c424a;
  border-radius: 12px;
  padding: 1.75rem;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.25);
  color: aliceblue;
}

.card-title {
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1.4rem;
  border-bottom: 2px solid #4f545c;
  padding-bottom: 0.5rem;
}

.Catto {
  position: fixed;
  bottom: 0;
  left: 0;
  cursor: pointer;
  z-index: 1000;
  transition: transform 0.15s ease-in-out;
}

.CatSpin{
  position: fixed;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);
}

.catspin{
  display: block;
  width: 200px;
  height: auto;
}

.Catto:hover {
  transform: scale(1.05);
}

.catgif {
  display: block;
  width: 200px;
  height: auto;
  mix-blend-mode: multiply;
  pointer-events: none;
}

.cattosad {
  position: fixed;
  bottom: 0;
  right: 1.5rem;
  cursor: pointer;
  z-index: 1000;
  transition: transform 0.15s ease-in-out;
}

.cattosad:hover {
  transform: scale(1.05);
}

.catsad {
  display: block;
  width: 140px;
  height: auto;
  mix-blend-mode: multiply;
  pointer-events: none;
}

.click-hint {
  position: absolute;
  bottom: 10px;
  background-color: #1e2124;
  color: #fff;
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 11px;
  border: 1px solid #4f545c;
  pointer-events: none;
}

.click-hint-right {
  position: absolute;
  bottom: 10px;
  right: 10px;
  background-color: #1e2124;
  color: #fff;
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 11px;
  border: 1px solid #4f545c;
  pointer-events: none;
}

.credentials-popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 440px;
  background-color: #1e2124;
  border: 2px solid #5865f2;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  box-shadow: 0 16px 36px rgba(0, 0, 0, 0.5);
  z-index: 2000;
  color: antiquewhite;
}

.popup-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid #3c424a;
}

.popup-header h2 {
  margin: 0;
  font-size: 1.25rem;
}

.close-btn {
  background: transparent;
  border: none;
  color: #aaa;
  font-size: 1.5rem;
  cursor: pointer;
  line-height: 1;
}

.close-btn:hover {
  color: white;
}

.popup-body ul {
  margin: 1rem 0 0;
  padding-left: 1.2rem;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #cfd4dc;
}

.popup-body a {
  color: #5865f2;
  text-decoration: underline;
  font-weight: 500;
}

.popup-body a:hover {
  color: #828df8;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translate(-50%, calc(-50% + 15px));
}
</style>