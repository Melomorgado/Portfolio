<script setup lang="ts">
import { ref } from "vue";

const purrCount = ref(0);
const credentials = ref(false);
const links = ref(false);
const isLightboxOpen = ref(false);

const playMeow = () => {
  const audio = new Audio('/meow.mp3');
  audio.volume = 0.5;
  audio.play().catch(() => {});
  purrCount.value++;
};

const playSpinSound = () => {
  const audio = new Audio('/spin.mp3');
  audio.volume = 0.5;
  audio.play().catch(() => {});
  purrCount.value += 2;
};

const catQuotes = [
  "Click me or I eat the CAT5 cable!",
  "ppst dito ang tingin",
];
const currentCatQuote = ref(catQuotes[0]);

const cycleQuote = () => {
  const rand = Math.floor(Math.random() * catQuotes.length);
  currentCatQuote.value = catQuotes[rand];
};

const toggleCredentials = () => {
  playMeow();
  cycleQuote();
  credentials.value = !credentials.value;
};

const toggleLink = () => {
  playMeow();
  links.value = !links.value;
};

const currentAchievementIndex = ref(0);

const achievements = ref([
  {
    title: "Dean's Lister 2-2025-2026",
    description: "Nakachamba ng isang sem.",
    image: "/cert1.jpg",
    tag: "CHAMBA",
  },
  {
    title: "Regional ITE Convention",
    description: "General Programming Champion",
    image: "/cert2.jpg",
    tag: "lah wala na si conde eh",
  },
  {
    title: "National CodeChum Programming Season 2",
    description: "Ranked Top 4 Group Staged and Top 16 Nationwide",
    image: "/cert3.png",
    tag: "TOP_4_GROUPSTAGE_NATIONAL",
  },
  {
    title: "Regional CpE Challenge 2025",
    description: "C Programming 1st Runner Up",
    image: "/cert4.jpg",
    tag: "ayan ihi pa kasi",
  },
]);

const nextAchievement = () => {
  currentAchievementIndex.value =
      (currentAchievementIndex.value + 1) % achievements.value.length;
};

const prevAchievement = () => {
  currentAchievementIndex.value =
      (currentAchievementIndex.value - 1 + achievements.value.length) %
      achievements.value.length;
};
</script>

<template>
  <div class="min-h-screen bg-[#121318] text-slate-100 font-mono relative overflow-x-hidden selection:bg-[#f43f5e] selection:text-white pb-36">
    <div class="fixed inset-0 pointer-events-none opacity-[0.03] bg-[radial-gradient(#fff_1px,transparent_1px)] [background-size:16px_16px]"></div>

    <header class="border-b-4 border-black bg-[#1e2029] p-3 shadow-[0_4px_0_0_#000] sticky top-0 z-30">
      <div class="max-w-[1000px] mx-auto flex flex-wrap justify-between items-center gap-3">
        <div class="flex items-center gap-3">
          <span class="text-2xl filter drop-shadow">🐱</span>
          <div>
            <div class="text-xl md:text-2xl font-black tracking-wider text-[#ffde59] uppercase drop-shadow-[2px_2px_0_#000]">
              Roan Carmelo G. Morgado
            </div>
            <div class="text-xs text-[#a0a5b5] flex items-center gap-2">
              <span class="bg-[#2a2d3d] text-emerald-400 px-1.5 py-0.5 rounded font-bold border border-black text-[10px]">PORTFOLIO</span>
              <span>BSCpE-4A | CSU CARIG</span>
            </div>
          </div>
        </div>

        <div class="flex items-center gap-2 bg-[#161821] border-2 border-black px-3 py-1.5 shadow-[3px_3px_0_0_#000] rounded">
          <span class="text-xs text-slate-400">MEOW_COUNT:</span>
          <span class="text-[#ff5e7e] font-black text-sm">{{ purrCount }} 🐾</span>
        </div>
      </div>
    </header>

    <main class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-[1000px] mx-auto mt-8 px-5">
      <section class="relative bg-[#1c1f2b] border-4 border-black rounded-lg shadow-[6px_6px_0_0_#000] transition-transform hover:-translate-y-1">
        <div class="absolute -top-3 left-4 w-4 h-4 bg-[#ff5e7e] border-t-2 border-l-2 border-black rotate-45 z-0"></div>
        <div class="absolute -top-3 left-10 w-4 h-4 bg-[#ff5e7e] border-t-2 border-r-2 border-black rotate-45 z-0"></div>

        <div class="bg-[#2a2e40] border-b-4 border-black px-4 py-2 flex justify-between items-center relative z-10">
          <span class="text-xs font-bold uppercase tracking-wider text-[#ffde59] flex items-center gap-1.5">
            <span>🐾</span> bio.cat
          </span>
          <div class="flex gap-1.5">
            <span class="w-3 h-3 rounded-full bg-[#ff5f56] border border-black inline-block"></span>
            <span class="w-3 h-3 rounded-full bg-[#ffbd2e] border border-black inline-block"></span>
            <span class="w-3 h-3 rounded-full bg-[#27c93f] border border-black inline-block"></span>
          </div>
        </div>

        <div class="p-6">
          <h2 class="text-xl font-black text-white mb-3 flex items-center gap-2">
            <span>HUMBLE COMPUTER ENGINEER</span>
          </h2>
          <p class="mb-3 text-sm text-slate-300 leading-relaxed border-l-2 border-[#ff5e7e] pl-3 italic">
            "I am a humble (HUMBLE!?) Computer Engineering student from CSU Carig trying to design a website."
          </p>
          <p class="text-sm text-slate-400 leading-relaxed">
            Aiming to become a full-stack engineer. Not artistic, just pure autistic.
          </p>

          <div class="mt-5 pt-3 border-t-2 border-[#2b3044] flex flex-wrap gap-2 text-xs">
            <span class="bg-[#282d40] border border-black px-2 py-1 rounded text-cyan-300">#CPE</span>
            <span class="bg-[#282d40] border border-black px-2 py-1 rounded text-yellow-300">#Elective2</span>
            <span class="bg-[#282d40] border border-black px-2 py-1 rounded text-rose-300">#CSU_Carig</span>
          </div>
        </div>
      </section>

      <section class="relative bg-[#1c1f2b] border-4 border-black rounded-lg shadow-[6px_6px_0_0_#000] transition-transform hover:-translate-y-1">
        <div class="absolute -top-3 right-10 w-4 h-4 bg-[#5865f2] border-t-2 border-l-2 border-black rotate-45 z-0"></div>
        <div class="absolute -top-3 right-4 w-4 h-4 bg-[#5865f2] border-t-2 border-r-2 border-black rotate-45 z-0"></div>

        <div class="bg-[#2a2e40] border-b-4 border-black px-4 py-2 flex justify-between items-center relative z-10">
          <span class="text-xs font-bold uppercase tracking-wider text-[#70e2ff] flex items-center gap-1.5">
            <span>⚡</span> skills.bin
          </span>
          <span class="text-[10px] bg-black text-emerald-400 font-bold px-2 py-0.5 rounded border border-gray-700">STATUS: ACTIVE</span>
        </div>

        <div class="p-6">
          <h3 class="text-sm font-bold uppercase text-[#ffde59] tracking-wider mb-2 flex items-center gap-1">
            <span>🐾</span> Languages & Software
          </h3>
          <div class="grid grid-cols-2 gap-2 mb-5">
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex items-center gap-2">
              <span class="text-rose-400 font-bold">C / C++</span>
              <span class="text-[10px] text-gray-500 ml-auto">[LOW-LEVEL]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex items-center gap-2">
              <span class="text-amber-400 font-bold">Java</span>
              <span class="text-[10px] text-gray-500 ml-auto">[OOP]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex items-center gap-2">
              <span class="text-emerald-400 font-bold">Python</span>
              <span class="text-[10px] text-gray-500 ml-auto">[SCRIPTS]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex items-center gap-2">
              <span class="text-cyan-400 font-bold">Vue / JS</span>
              <span class="text-[10px] text-gray-500 ml-auto">[WEB]</span>
            </div>
          </div>

          <h3 class="text-sm font-bold uppercase text-[#ffde59] tracking-wider mb-2 flex items-center gap-1">
            <span>🐾</span> Hardware Engineering
          </h3>
          <ul class="text-xs text-slate-300 space-y-1.5 pl-1">
            <li class="flex items-center gap-2">
              <span class="text-emerald-400">▶</span> PCB Schematic & Routing
            </li>
            <li class="flex items-center gap-2">
              <span class="text-emerald-400">▶</span> Embedded Microcontroller Systems
            </li>
            <li class="flex items-center gap-2">
              <span class="text-emerald-400">▶</span> 3D Modeling & Prototyping
            </li>
          </ul>
        </div>
      </section>
    </main>

    <div
        class="fixed bottom-0 left-2 md:left-6 cursor-pointer z-40 transition-transform duration-150 hover:scale-105 select-none group"
        @click="toggleCredentials"
        title="Click me for Achievements!"
    >
      <div class="absolute -top-12 left-8 bg-white text-black text-xs font-bold py-1.5 px-3 rounded-xl border-2 border-black shadow-[3px_3px_0_0_#000] whitespace-nowrap pointer-events-none transition-all group-hover:-translate-y-1">
        {{ currentCatQuote }}
        <div class="absolute -bottom-2 left-4 w-3 h-3 bg-white border-b-2 border-r-2 border-black rotate-45"></div>
      </div>

      <img class="w-[180px] md:w-[210px] h-auto mix-blend-screen pointer-events-none block" src="/catdancee.gif" alt="Dancing Cat" />
      <span class="absolute bottom-3 left-4 bg-[#ff5e7e] text-black text-[11px] font-black px-2 py-0.5 rounded border-2 border-black shadow-[2px_2px_0_0_#000] pointer-events-none">
        🏆 ACHIEVEMENTS ^
      </span>
    </div>

    <div
        class="fixed bottom-3 left-1/2 -translate-x-1/2 cursor-pointer z-40 transition-transform duration-150 hover:scale-110 active:scale-95 select-none flex flex-col items-center"
        @click="playSpinSound"
        title="Bother the spin cat!"
    >
      <div class="bg-black/80 border-2 border-[#ffde59] text-[#ffde59] text-[10px] font-bold px-2 py-0.5 rounded shadow-[2px_2px_0_0_#000] mb-1">
        SPIN MEOW 🌀
      </div>
      <img class="w-[150px] md:w-[180px] h-auto block pointer-events-none drop-shadow-[0_0_15px_rgba(255,222,89,0.3)]" src="/spinn.gif" alt="Cat Spin" />
    </div>

    <div
        class="fixed bottom-0 right-2 md:right-6 cursor-pointer z-40 transition-transform duration-150 hover:scale-105 select-none group"
        @click="toggleLink"
        title="Click me for Social Links!"
    >
      <div class="absolute -top-10 right-4 bg-[#70e2ff] text-black text-xs font-bold py-1 px-3 rounded-lg border-2 border-black shadow-[3px_3px_0_0_#000] pointer-events-none">
        Need coffee & links...
        <div class="absolute -bottom-1.5 right-6 w-2.5 h-2.5 bg-[#70e2ff] border-b-2 border-r-2 border-black rotate-45"></div>
      </div>
      <img class="w-[130px] md:w-[150px] h-auto mix-blend-screen pointer-events-none block drop-shadow-[0_4px_8px_rgba(0,0,0,0.8)]" src="/cattosad.png" alt="Sad Cat" />
      <span class="absolute bottom-3 right-4 bg-[#70e2ff] text-black text-[11px] font-black px-2 py-0.5 rounded border-2 border-black shadow-[2px_2px_0_0_#000] pointer-events-none">
        LINKS / CONTACT ^
      </span>
    </div>

    <Transition name="fade-backdrop">
      <div
          v-if="credentials || links"
          class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 transition-opacity"
          @click="credentials = false; links = false"
      ></div>
    </Transition>

    <Transition name="fade-popup">
      <div
          v-if="credentials"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[92%] max-w-[540px] bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-[#ff5e7e] text-black border-b-4 border-black px-4 py-2.5 flex justify-between items-center font-black">
          <div class="flex items-center gap-2 text-sm tracking-wider">
            <span>🏆</span> ACHIEVEMENTS_VAULT.EXE
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-7 h-7 flex items-center justify-center font-black text-sm cursor-pointer transition shadow-[2px_2px_0_0_#000]"
              @click.stop="credentials = false"
          >
            ✕
          </button>
        </div>

        <div class="p-5">
          <div class="relative bg-black border-4 border-black rounded-md overflow-hidden shadow-[4px_4px_0_0_#000]">
            <div class="relative overflow-hidden cursor-zoom-in group" @click="isLightboxOpen = true">
              <img
                  :src="achievements[currentAchievementIndex].image"
                  :alt="achievements[currentAchievementIndex].title"
                  class="w-full h-64 object-cover block transition-transform duration-200 group-hover:scale-105"
                  @error="(e: any) => { e.target.src = 'https://placehold.co/600x400/181a24/ff5e7e?text=Photo+Pending+Upload'; }"
              />
              <div class="absolute top-2 right-2 bg-black/80 text-[#ffde59] text-[10px] font-bold px-2 py-1 rounded border border-black shadow">
                {{ achievements[currentAchievementIndex].tag }}
              </div>
              <div class="absolute bottom-2 right-2 bg-[#ff5e7e] text-black font-black text-[11px] px-2.5 py-1 rounded border-2 border-black shadow-[2px_2px_0_0_#000] opacity-0 group-hover:opacity-100 transition-opacity">
                🔍 CLICK TO ENLARGE
              </div>
            </div>

            <div class="p-3 bg-[#1e2130] border-t-2 border-black">
              <h3 class="text-base font-black text-[#ffde59] m-0">
                {{ achievements[currentAchievementIndex].title }}
              </h3>
              <p class="text-xs text-slate-300 mt-1 m-0">
                {{ achievements[currentAchievementIndex].description }}
              </p>
            </div>
          </div>

          <div class="flex justify-between items-center mt-4">
            <button
                class="bg-[#2a2e40] hover:bg-[#ff5e7e] hover:text-black text-white font-black border-2 border-black px-4 py-1.5 rounded shadow-[3px_3px_0_0_#000] text-sm cursor-pointer transition select-none flex items-center gap-1 active:translate-x-0.5 active:translate-y-0.5"
                @click="prevAchievement"
            >
              ◀ PREV
            </button>

            <div class="flex gap-2 items-center">
              <button
                  v-for="(_, index) in achievements"
                  :key="index"
                  class="w-3.5 h-3.5 rounded-full border-2 border-black transition-all cursor-pointer p-0"
                  :class="currentAchievementIndex === index ? 'bg-[#ffde59] scale-125' : 'bg-gray-700 hover:bg-gray-500'"
                  @click="currentAchievementIndex = index"
              ></button>
            </div>

            <button
                class="bg-[#2a2e40] hover:bg-[#ff5e7e] hover:text-black text-white font-black border-2 border-black px-4 py-1.5 rounded shadow-[3px_3px_0_0_#000] text-sm cursor-pointer transition select-none flex items-center gap-1 active:translate-x-0.5 active:translate-y-0.5"
                @click="nextAchievement"
            >
              NEXT ▶
            </button>
          </div>
        </div>
      </div>
    </Transition>

    <Transition name="fade-popup">
      <div
          v-if="links"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[90%] max-w-[460px] bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-[#70e2ff] text-black border-b-4 border-black px-4 py-2.5 flex justify-between items-center font-black">
          <div class="flex items-center gap-2 text-sm tracking-wider">
            <span>🌐</span> COMM_LINKS.SYS
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-7 h-7 flex items-center justify-center font-black text-sm cursor-pointer transition shadow-[2px_2px_0_0_#000]"
              @click.stop="links = false"
          >
            ✕
          </button>
        </div>

        <div class="p-6">
          <div class="text-xs text-slate-400 mb-4 pb-2 border-b border-gray-700">
            CONNECT TO DEVELOPER GATEWAY:
          </div>

          <div class="space-y-3">
            <a
                href="https://github.com/Melomorgado"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center justify-between p-3 bg-[#11131c] hover:bg-[#252a3d] border-2 border-black rounded shadow-[3px_3px_0_0_#000] text-sm transition group"
            >
              <div class="flex items-center gap-2 text-white font-bold">
                <span>💻</span> GitHub
              </div>
              <span class="text-xs text-[#70e2ff] font-mono group-hover:underline">@Melomorgado ↗</span>
            </a>

            <a
                href="mailto:roancarmelomorgado@gmail.com"
                class="flex items-center justify-between p-3 bg-[#11131c] hover:bg-[#252a3d] border-2 border-black rounded shadow-[3px_3px_0_0_#000] text-sm transition group"
            >
              <div class="flex items-center gap-2 text-white font-bold">
                <span>📬</span> Email
              </div>
              <span class="text-xs text-[#ff5e7e] font-mono group-hover:underline">roancarmelomorgado@gmail.com ↗</span>
            </a>

            <a
                href="https://www.facebook.com/roan.morgado.39"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center justify-between p-3 bg-[#11131c] hover:bg-[#252a3d] border-2 border-black rounded shadow-[3px_3px_0_0_#000] text-sm transition group"
            >
              <div class="flex items-center gap-2 text-white font-bold">
                <span>👥</span> Facebook
              </div>
              <span class="text-xs text-blue-400 font-mono group-hover:underline">Roan Morgado ↗</span>
            </a>
          </div>
        </div>
      </div>
    </Transition>

    <Transition name="fade-lightbox">
      <div
          v-if="isLightboxOpen"
          class="fixed inset-0 z-[70] flex flex-col items-center justify-center bg-black/95 backdrop-blur-md p-4"
          @click="isLightboxOpen = false"
      >
        <button
            class="absolute top-4 right-6 text-white hover:text-[#ff5e7e] font-black text-4xl bg-transparent border-none cursor-pointer z-10"
            @click.stop="isLightboxOpen = false"
        >
          ✕
        </button>

        <div class="max-w-[90vw] max-h-[85vh] flex flex-col items-center" @click.stop>
          <img
              :src="achievements[currentAchievementIndex].image"
              :alt="achievements[currentAchievementIndex].title"
              class="max-w-full max-h-[75vh] object-contain rounded-lg border-4 border-black shadow-[8px_8px_0_0_#ffde59]"
              @error="(e: any) => { e.target.src = 'https://placehold.co/800x600/181a24/ff5e7e?text=Photo+Pending+Upload'; }"
          />
          <div class="mt-4 text-center bg-[#1e2029] border-2 border-black px-4 py-2 rounded shadow-[3px_3px_0_0_#000]">
            <h3 class="text-base font-black text-[#ffde59]">
              {{ achievements[currentAchievementIndex].title }}
            </h3>
            <p class="text-xs text-slate-300 mt-1">
              {{ achievements[currentAchievementIndex].description }}
            </p>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<style>
html, body {
  cursor: url('/cursor.png') 0 0, auto !important;
}

a,
button,
[role="button"],
.cursor-pointer,
.cursor-zoom-in {
  cursor: url('/cursor-pointer.png') 0 0, pointer !important;
}
</style>

<style scoped>
.fade-popup-enter-active,
.fade-popup-leave-active {
  transition: opacity 0.15s ease, transform 0.15s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.fade-popup-enter-from,
.fade-popup-leave-to {
  opacity: 0;
  transform: translate(-50%, -45%) scale(0.95);
}

.fade-backdrop-enter-active,
.fade-backdrop-leave-active,
.fade-lightbox-enter-active,
.fade-lightbox-leave-active {
  transition: opacity 0.2s ease;
}

.fade-backdrop-enter-from,
.fade-backdrop-leave-to,
.fade-lightbox-enter-from,
.fade-lightbox-leave-to {
  opacity: 0;
}
</style>