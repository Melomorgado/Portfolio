<script setup lang="ts">
import { ref, computed } from "vue";
import StaticProfile from "@/components/Static.vue";

const credentialsOpen = ref(false);
const projectsOpen = ref(false);
const certificatesOpen = ref(false);
const linksOpen = ref(false);
const isLightboxOpen = ref(false);

const catMaskIndex = ref(0);
const maskCats = [
  { src: "/catmask1.jpg", label: "CLICK TO PEEL" },
  { src: "/mask2.png", label: "1 More?" },
  { src: "/mask3.png", label: "1 MORE!?" }
];

const isFaceRevealed = computed(() => catMaskIndex.value >= maskCats.length);

const playMeow = () => {
  const audio = new Audio("/meow.mp3");
  audio.volume = 0.5;
  audio.play().catch(() => {});
};

const playMeow2 = () => {
  const audio = new Audio("/meow-1.mp3");
  audio.volume = 0.5;
  audio.play().catch(() => {});
};

const playSpinSound = () => {
  const audio = new Audio("/spin.mp3");
  audio.volume = 0.5;
  audio.play().catch(() => {});
};

// Plays when the final layer is clicked and your face is revealed
const playWowSound = () => {
  const audio = new Audio("/wow.mp3");
  audio.volume = 0.6;
  audio.play().catch(() => {});
};

const advanceMask = () => {
  if (catMaskIndex.value < maskCats.length) {
    catMaskIndex.value++;

    if (isFaceRevealed.value) {
      playWowSound();
    } else {
      playMeow();
    }
  }
};

const resetMask = () => {
  catMaskIndex.value = 0;
};

const catQuotes = [
  "professional web!",
  "ppst dito ang tingin",
];
const currentCatQuote = ref(catQuotes[0]);

const cycleQuote = () => {
  currentCatQuote.value = catQuotes[Math.floor(Math.random() * catQuotes.length)];
};

const currentAchievementIndex = ref(0);
const achievements = ref([
  {
    title: "Dean's Lister 2-2025-2026",
    description: "Nakachamba ng isang sem.",
    image: "/cert1.jpg",
    tag: "CHAMBA"
  },
  {
    title: "Regional ITE Convention",
    description: "General Programming Champion",
    image: "/cert2.jpg",
    tag: "lah wala na si conde eh"
  },
  {
    title: "National CodeChum Programming Season 2",
    description: "Ranked Top 4 Group Staged and Top 16 Nationwide",
    image: "/cert3.png",
    tag: "TOP_4_GROUPSTAGE_NATIONAL"
  },
  {
    title: "Regional CpE Challenge 2025",
    description: "C Programming 1st Runner Up",
    image: "/cert4.jpg",
    tag: "ayan ihi pa kasi"
  }
]);

const currentCertificateIndex = ref(0);
const certificates = ref([
  {
    title: "Certified SO2 Passer",
    issuer: "1BESO",
    image: "/certs1.png"
  },
  {
    title: "Regional ITE Convention",
    issuer: "St. Paul University of the Philippines",
    image: "/certs2.png"
  }
]);

const currentProjectIndex = ref(0);
const projects = ref([
  {
    title: "VitaScan Kiosk",
    description: "Kiosk for basic health assessment",
    image: "/proj1.png",
    tag: "IOT / HARDWARE",
    stack: ["ESP32", "php", "Sensors"]
  },
  {
    title: "Grow a Sanction",
    description: "Sanction management system for COEASC",
    image: "/proj2.png",
    tag: "Website/Vibecoded",
    stack: ["HTML/CSS", "php", "Javascript"]
  },
]);

const contactInfo = {
  phone: "+63 935 849 7611",
  email: "roancarmelomorgado@gmail.com",
  address: "Tuguegarao City, Cagayan, Philippines"
};

const socialLinks = [
  { platform: "Phone", icon: "📞", url: `tel:${contactInfo.phone}`, display: contactInfo.phone },
  { platform: "Email", icon: "📬", url: `mailto:${contactInfo.email}`, display: contactInfo.email },
  { platform: "GitHub", icon: "💻", url: "https://github.com/Melomorgado", display: "@Melomorgado" },
  { platform: "Facebook", icon: "👥", url: "https://www.facebook.com/roan.morgado.39", display: "Roan Morgado" }
];

const lightboxData = ref({ title: "", description: "", image: "" });

const openLightbox = (item: { title: string; description?: string; image: string; issuer?: string }) => {
  lightboxData.value = {
    title: item.title,
    description: item.description || item.issuer || "",
    image: item.image
  };
  isLightboxOpen.value = true;
};

const nextAchievement = () => {
  currentAchievementIndex.value = (currentAchievementIndex.value + 1) % achievements.value.length;
};
const prevAchievement = () => {
  currentAchievementIndex.value = (currentAchievementIndex.value - 1 + achievements.value.length) % achievements.value.length;
};

const nextProject = () => {
  currentProjectIndex.value = (currentProjectIndex.value + 1) % projects.value.length;
};
const prevProject = () => {
  currentProjectIndex.value = (currentProjectIndex.value - 1 + projects.value.length) % projects.value.length;
};

const nextCert = () => {
  currentCertificateIndex.value = (currentCertificateIndex.value + 1) % certificates.value.length;
};
const prevCert = () => {
  currentCertificateIndex.value = (currentCertificateIndex.value - 1 + certificates.value.length) % certificates.value.length;
};

const toggleCredentials = () => {
  playMeow();
  cycleQuote();
  credentialsOpen.value = !credentialsOpen.value;
};

const toggleProjects = () => {
  playSpinSound();
  projectsOpen.value = !projectsOpen.value;
};

const toggleLinks = () => {
  playMeow2();
  linksOpen.value = !linksOpen.value;
};

const toggleCertificates = () => {
  playMeow();
  certificatesOpen.value = !certificatesOpen.value;
};

const closeModals = () => {
  credentialsOpen.value = false;
  projectsOpen.value = false;
  certificatesOpen.value = false;
  linksOpen.value = false;
};
</script>

<template>
  <div class="min-h-screen bg-[#121318] text-slate-100 font-mono relative selection:bg-[#f43f5e] selection:text-white pb-20">
    <StaticProfile />

    <main class="max-w-[1000px] mx-auto mt-6 px-4 space-y-6">

      <!-- 1. BIO.CAT with Profile Image, Address & Contact Details -->
      <section class="bg-[#1c1f2b] border-4 border-black rounded-lg shadow-[6px_6px_0_0_#000]">
        <div class="bg-[#2a2e40] border-b-4 border-black px-4 py-2 flex justify-between items-center">
          <span class="text-xs font-bold uppercase tracking-wider text-[#ffde59]">🐾 bio.cat</span>
          <div class="flex gap-1.5">
            <span class="w-3 h-3 rounded-full bg-[#ff5f56] border border-black inline-block"></span>
            <span class="w-3 h-3 rounded-full bg-[#ffbd2e] border border-black inline-block"></span>
            <span class="w-3 h-3 rounded-full bg-[#27c93f] border border-black inline-block"></span>
          </div>
        </div>

        <div class="p-6">
          <div class="flex flex-col sm:flex-row gap-6 items-center sm:items-start">

            <div class="shrink-0 flex flex-col items-center">
              <div class="relative w-40 h-40 rounded-lg border-4 border-black bg-black overflow-hidden shadow-[4px_4px_0_0_#000] select-none flex items-center justify-center">
                <img
                    src="/face.jpg"
                    alt="Roan Carmelo Morgado"
                    class="w-full h-full object-cover"
                    @error="(e: any) => { e.target.src = 'https://placehold.co/400x400/181a24/ffffff?text=Roan+Face'; }"
                />

                <Transition name="fade">
                  <div
                      v-if="!isFaceRevealed"
                      class="absolute inset-0 bg-[#161821] flex flex-col items-center justify-center cursor-pointer group"
                      @click="advanceMask"
                      title="Click to remove layer"
                  >
                    <img
                        :src="maskCats[catMaskIndex].src"
                        alt="Cat Mask"
                        class="w-24 h-24 object-contain transition-transform group-hover:scale-110"
                    />
                    <span class="absolute bottom-1 bg-[#ff5e7e] text-black font-black text-[9px] px-1.5 py-0.5 border border-black rounded shadow">
                      {{ maskCats[catMaskIndex].label }}
                    </span>
                  </div>
                </Transition>
              </div>

              <span class="text-[10px] text-emerald-400 mt-2 font-bold">
                {{ isFaceRevealed ? 'UNMASKED' : `LAYER ${catMaskIndex + 1}/3` }}
              </span>
              <button
                  v-if="isFaceRevealed"
                  @click="resetMask"
                  class="mt-1 text-[9px] bg-[#2a2e40] hover:bg-[#ff5e7e] hover:text-black text-slate-200 font-bold border-2 border-black px-2 py-0.5 rounded shadow cursor-pointer"
              >
                RE-MASK ↺
              </button>
            </div>

            <div class="flex-1 text-center sm:text-left">
              <h2 class="text-xl font-black text-white mb-1">HUMBLE COMPUTER ENGINEER</h2>

              <div class="text-xs text-[#70e2ff] font-bold mb-3 flex items-center justify-center sm:justify-start gap-1.5">
                <span>📍</span>
                <span>{{ contactInfo.address }}</span>
              </div>

              <p class="mb-3 text-xs text-slate-300 leading-relaxed border-l-2 border-[#ff5e7e] pl-3 italic">
                "I am a humble (HUMBLE!?) Computer Engineering student from CSU Carig trying to design a website."
              </p>
              <p class="text-xs text-slate-400 leading-relaxed mb-4">
                Aiming to become a full-stack engineer. Not artistic, just focused on reliable systems, hardware prototypes, and reactive architecture.
              </p>

              <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs bg-[#121318] p-2.5 rounded border border-black mb-4">
                <div class="flex items-center gap-1.5 text-slate-300">
                  <span class="text-[#ffde59]">📞 Phone:</span>
                  <a :href="`tel:${contactInfo.phone}`" class="text-white hover:underline">{{ contactInfo.phone }}</a>
                </div>
                <div class="flex items-center gap-1.5 text-slate-300">
                  <span class="text-[#ff5e7e]">📬 Email:</span>
                  <a :href="`mailto:${contactInfo.email}`" class="text-white hover:underline truncate">{{ contactInfo.email }}</a>
                </div>
              </div>

              <div class="pt-3 border-t-2 border-[#2b3044] flex flex-wrap justify-center sm:justify-start gap-2 text-xs">
                <span class="bg-[#282d40] border border-black px-2 py-0.5 rounded text-cyan-300">#CPE</span>
                <span class="bg-[#282d40] border border-black px-2 py-0.5 rounded text-yellow-300">#Elective2</span>
                <span class="bg-[#282d40] border border-black px-2 py-0.5 rounded text-rose-300">#CSU_Carig</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- 2. SKILLS.BIN -->
      <section class="bg-[#1c1f2b] border-4 border-black rounded-lg shadow-[6px_6px_0_0_#000]">
        <div class="bg-[#2a2e40] border-b-4 border-black px-4 py-2 flex justify-between items-center">
          <span class="text-xs font-bold uppercase tracking-wider text-[#70e2ff]">⚡ skills.bin</span>
          <span class="text-[10px] bg-black text-emerald-400 font-bold px-2 py-0.5 rounded border border-gray-700">ONLINE</span>
        </div>

        <div class="p-6">
          <h3 class="text-xs font-bold uppercase text-[#ffde59] tracking-wider mb-2">Software Stack</h3>
          <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 mb-4">
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex justify-between">
              <span class="text-rose-400 font-bold">C / C++</span>
              <span class="text-[9px] text-gray-500">[COMPETITION]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex justify-between">
              <span class="text-amber-400 font-bold">Java</span>
              <span class="text-[9px] text-gray-500">[OOP]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex justify-between">
              <span class="text-emerald-400 font-bold">Python</span>
              <span class="text-[9px] text-gray-500">[SCRIPTS | Data Handling]</span>
            </div>
            <div class="bg-[#151722] border-2 border-black p-2 rounded text-xs flex justify-between">
              <span class="text-cyan-400 font-bold">Vue / JS</span>
              <span class="text-[9px] text-gray-500">[UI]</span>
            </div>
          </div>

          <h3 class="text-xs font-bold uppercase text-[#ffde59] tracking-wider mb-2">Hardware Focus</h3>
          <ul class="text-xs text-slate-300 space-y-1 pl-1">
            <li class="flex items-center gap-1.5"><span class="text-emerald-400">▶</span> PCB Schematic & Routing</li>
            <li class="flex items-center gap-1.5"><span class="text-emerald-400">▶</span> Embedded Systems & MCU</li>
            <li class="flex items-center gap-1.5"><span class="text-emerald-400">▶</span> Sensors & Actuators</li>
          </ul>
        </div>
      </section>

      <!-- 3. Scrollable Bottom Cats Arcade -->
      <section class="bg-[#1c1f2b] border-4 border-black rounded-lg shadow-[6px_6px_0_0_#000] p-6 text-center">
        <div class="text-xs font-bold text-[#ffde59] mb-6 uppercase tracking-wider">
          🐾 Interactive Cat Terminal (Click to Trigger Modals) 🐾
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-4 gap-6 items-end justify-items-center">

          <!-- Dancing Cat: Achievements -->
          <div
              class="cursor-pointer transition-transform duration-150 hover:scale-105 active:scale-95 select-none flex flex-col items-center group"
              @click="toggleCredentials"
          >
            <div class="bg-white text-black text-[10px] font-bold py-1 px-2 rounded-lg border-2 border-black shadow-[2px_2px_0_0_#000] mb-2 truncate max-w-[130px]">
              {{ currentCatQuote }}
            </div>
            <img class="w-28 h-28 object-contain mix-blend-screen block pointer-events-none" src="/catdancee.gif" alt="Dancing Cat" />
            <span class="mt-2 bg-[#ff5e7e] text-black text-[11px] font-black px-2 py-1 rounded border-2 border-black shadow-[2px_2px_0_0_#000]">
              🏆 ACHIEVEMENTS
            </span>
          </div>

          <!-- Spinning Cat: Projects -->
          <div
              class="cursor-pointer transition-transform duration-150 hover:scale-110 active:scale-95 select-none flex flex-col items-center"
              @click="toggleProjects"
          >
            <div class="bg-black/90 border-2 border-[#ffde59] text-[#ffde59] text-[9px] font-bold px-2 py-0.5 rounded shadow-[1px_1px_0_0_#000] mb-2">
              CLICK TO SPIN!
            </div>
            <img class="w-24 h-24 object-contain block pointer-events-none drop-shadow-[0_0_10px_rgba(255,222,89,0.3)]" src="/spinn.gif" alt="Cat Spin" />
            <span class="mt-2 bg-[#ffde59] text-black text-[11px] font-black px-2 py-1 rounded border-2 border-black shadow-[2px_2px_0_0_#000]">
              🚀 PROJECTS
            </span>
          </div>

          <!-- Certificates Cat Button -->
          <div
              class="cursor-pointer transition-transform duration-150 hover:scale-105 active:scale-95 select-none flex flex-col items-center"
              @click="toggleCertificates"
          >
            <div class="bg-emerald-300 text-black text-[9px] font-bold px-2 py-0.5 rounded border border-black shadow mb-2">
              CERTIFICATES!
            </div>
            <img class="w-24 h-24 object-contain mix-blend-screen block pointer-events-none" src="/pogicat.png" alt="Certs Cat" />
            <span class="mt-2 bg-emerald-400 text-black text-[11px] font-black px-2 py-1 rounded border-2 border-black shadow-[2px_2px_0_0_#000]">
              📜 CERTIFICATES
            </span>
          </div>

          <!-- Sad Cat: Links / Contact Info -->
          <div
              class="cursor-pointer transition-transform duration-150 hover:scale-105 active:scale-95 select-none flex flex-col items-center group"
              @click="toggleLinks"
          >
            <div class="bg-[#70e2ff] text-black text-[10px] font-bold py-1 px-2 rounded-lg border-2 border-black shadow-[2px_2px_0_0_#000] mb-2">
              Contacts & links...
            </div>
            <img class="w-24 h-24 object-contain mix-blend-screen block pointer-events-none" src="/cattosad.png" alt="Sad Cat" />
            <span class="mt-2 bg-[#70e2ff] text-black text-[11px] font-black px-2 py-1 rounded border-2 border-black shadow-[2px_2px_0_0_#000]">
              🌐 CONTACT INFO
            </span>
          </div>

        </div>
      </section>

    </main>

    <!-- Modals Backdrop -->
    <Transition name="fade-backdrop">
      <div
          v-if="credentialsOpen || projectsOpen || certificatesOpen || linksOpen"
          class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 transition-opacity"
          @click="closeModals"
      ></div>
    </Transition>

    <!-- Modal 1: Achievements -->
    <Transition name="fade-popup">
      <div
          v-if="credentialsOpen"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[92%] max-w-[500px] max-h-[90dvh] flex flex-col bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-[#ff5e7e] text-black border-b-4 border-black px-3.5 py-2 flex justify-between items-center font-black shrink-0">
          <div class="flex items-center gap-1.5 text-xs sm:text-sm tracking-wider">
            <span>🏆</span> ACHIEVEMENTS_VAULT.EXE
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-6 h-6 sm:w-7 sm:h-7 flex items-center justify-center font-black text-xs sm:text-sm cursor-pointer"
              @click.stop="credentialsOpen = false"
          >
            ✕
          </button>
        </div>

        <div class="p-4 overflow-y-auto overflow-x-hidden">
          <div class="relative bg-black border-4 border-black rounded-md overflow-hidden shadow-[4px_4px_0_0_#000]">
            <div class="relative overflow-hidden cursor-zoom-in group" @click="openLightbox(achievements[currentAchievementIndex])">
              <img
                  :src="achievements[currentAchievementIndex].image"
                  :alt="achievements[currentAchievementIndex].title"
                  class="w-full h-52 sm:h-60 object-cover block transition-transform duration-200 group-hover:scale-105"
                  @error="(e: any) => { e.target.src = 'https://placehold.co/600x400/181a24/ff5e7e?text=Photo+Pending+Upload'; }"
              />
              <div class="absolute top-2 right-2 bg-black/80 text-[#ffde59] text-[9px] sm:text-[10px] font-bold px-1.5 py-0.5 rounded border border-black shadow">
                {{ achievements[currentAchievementIndex].tag }}
              </div>
              <div class="absolute bottom-2 right-2 bg-[#ff5e7e] text-black font-black text-[10px] px-2 py-0.5 rounded border-2 border-black opacity-0 group-hover:opacity-100 transition-opacity">
                🔍 TAP TO ENLARGE
              </div>
            </div>

            <div class="p-3 bg-[#1e2130] border-t-2 border-black">
              <h3 class="text-sm sm:text-base font-black text-[#ffde59] m-0">{{ achievements[currentAchievementIndex].title }}</h3>
              <p class="text-xs text-slate-300 mt-1 m-0">{{ achievements[currentAchievementIndex].description }}</p>
            </div>
          </div>

          <div class="flex justify-between items-center mt-4">
            <button
                class="bg-[#2a2e40] hover:bg-[#ff5e7e] hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="prevAchievement"
            >
              ◀ PREV
            </button>
            <div class="flex gap-1.5 items-center">
              <button
                  v-for="(_, index) in achievements"
                  :key="index"
                  class="w-2.5 h-2.5 sm:w-3 sm:h-3 rounded-full border-2 border-black cursor-pointer p-0"
                  :class="currentAchievementIndex === index ? 'bg-[#ffde59] scale-125' : 'bg-gray-700'"
                  @click="currentAchievementIndex = index"
              ></button>
            </div>
            <button
                class="bg-[#2a2e40] hover:bg-[#ff5e7e] hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="nextAchievement"
            >
              NEXT ▶
            </button>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Modal 2: Projects -->
    <Transition name="fade-popup">
      <div
          v-if="projectsOpen"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[92%] max-w-[500px] max-h-[90dvh] flex flex-col bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-[#ffde59] text-black border-b-4 border-black px-3.5 py-2 flex justify-between items-center font-black shrink-0">
          <div class="flex items-center gap-1.5 text-xs sm:text-sm tracking-wider">
            <span>💻</span> PROJECTS_LIST.BIN
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-6 h-6 sm:w-7 sm:h-7 flex items-center justify-center font-black text-xs sm:text-sm cursor-pointer"
              @click.stop="projectsOpen = false"
          >
            ✕
          </button>
        </div>

        <div class="p-4 overflow-y-auto overflow-x-hidden">
          <div class="relative bg-black border-4 border-black rounded-md overflow-hidden shadow-[4px_4px_0_0_#000]">
            <div class="relative overflow-hidden cursor-zoom-in group" @click="openLightbox(projects[currentProjectIndex])">
              <img
                  :src="projects[currentProjectIndex].image"
                  :alt="projects[currentProjectIndex].title"
                  class="w-full h-52 sm:h-60 object-cover block transition-transform duration-200 group-hover:scale-105"
                  @error="(e: any) => { e.target.src = 'https://placehold.co/600x400/181a24/ffde59?text=Project+Screenshot'; }"
              />
              <div class="absolute top-2 right-2 bg-black/80 text-emerald-400 text-[9px] sm:text-[10px] font-bold px-1.5 py-0.5 rounded border border-black shadow">
                {{ projects[currentProjectIndex].tag }}
              </div>
              <div class="absolute bottom-2 right-2 bg-[#ffde59] text-black font-black text-[10px] px-2 py-0.5 rounded border-2 border-black opacity-0 group-hover:opacity-100 transition-opacity">
                🔍 TAP TO ENLARGE
              </div>
            </div>

            <div class="p-3 bg-[#1e2130] border-t-2 border-black">
              <h3 class="text-sm sm:text-base font-black text-[#ffde59] m-0">{{ projects[currentProjectIndex].title }}</h3>
              <p class="text-xs text-slate-300 mt-1 m-0">{{ projects[currentProjectIndex].description }}</p>

              <div class="flex flex-wrap gap-1 mt-2">
                <span
                    v-for="(tech, tIndex) in projects[currentProjectIndex].stack"
                    :key="tIndex"
                    class="bg-[#121318] text-cyan-300 border border-black text-[9px] sm:text-[10px] font-bold px-1.5 py-0.2 rounded"
                >
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>

          <div class="flex justify-between items-center mt-4">
            <button
                class="bg-[#2a2e40] hover:bg-[#ffde59] hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="prevProject"
            >
              ◀ PREV
            </button>
            <div class="flex gap-1.5 items-center">
              <button
                  v-for="(_, index) in projects"
                  :key="index"
                  class="w-2.5 h-2.5 sm:w-3 sm:h-3 rounded-full border-2 border-black cursor-pointer p-0"
                  :class="currentProjectIndex === index ? 'bg-[#ffde59] scale-125' : 'bg-gray-700'"
                  @click="currentProjectIndex = index"
              ></button>
            </div>
            <button
                class="bg-[#2a2e40] hover:bg-[#ffde59] hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="nextProject"
            >
              NEXT ▶
            </button>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Modal 3: Certificates -->
    <Transition name="fade-popup">
      <div
          v-if="certificatesOpen"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[92%] max-w-[500px] max-h-[90dvh] flex flex-col bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-emerald-400 text-black border-b-4 border-black px-3.5 py-2 flex justify-between items-center font-black shrink-0">
          <div class="flex items-center gap-1.5 text-xs sm:text-sm tracking-wider">
            <span>📜</span> CERTIFICATES.VIEW
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-6 h-6 sm:w-7 sm:h-7 flex items-center justify-center font-black text-xs sm:text-sm cursor-pointer"
              @click.stop="certificatesOpen = false"
          >
            ✕
          </button>
        </div>

        <div class="p-4 overflow-y-auto overflow-x-hidden">
          <div class="relative bg-black border-4 border-black rounded-md overflow-hidden shadow-[4px_4px_0_0_#000]">
            <div class="relative overflow-hidden cursor-zoom-in group" @click="openLightbox(certificates[currentCertificateIndex])">
              <img
                  :src="certificates[currentCertificateIndex].image"
                  :alt="certificates[currentCertificateIndex].title"
                  class="w-full h-52 sm:h-60 object-cover block transition-transform duration-200 group-hover:scale-105"
                  @error="(e: any) => { e.target.src = 'https://placehold.co/600x400/181a24/10b981?text=Certificate+Preview'; }"
              />
              <div class="absolute bottom-2 right-2 bg-emerald-400 text-black font-black text-[10px] px-2 py-0.5 rounded border-2 border-black opacity-0 group-hover:opacity-100 transition-opacity">
                🔍 TAP TO ENLARGE
              </div>
            </div>

            <div class="p-3 bg-[#1e2130] border-t-2 border-black">
              <h3 class="text-sm sm:text-base font-black text-emerald-400 m-0">{{ certificates[currentCertificateIndex].title }}</h3>
              <p class="text-xs text-slate-300 mt-1 m-0">Issued by: {{ certificates[currentCertificateIndex].issuer }}</p>
            </div>
          </div>

          <div class="flex justify-between items-center mt-4">
            <button
                class="bg-[#2a2e40] hover:bg-emerald-400 hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="prevCert"
            >
              ◀ PREV
            </button>
            <div class="flex gap-1.5 items-center">
              <button
                  v-for="(_, index) in certificates"
                  :key="index"
                  class="w-2.5 h-2.5 sm:w-3 sm:h-3 rounded-full border-2 border-black cursor-pointer p-0"
                  :class="currentCertificateIndex === index ? 'bg-emerald-400 scale-125' : 'bg-gray-700'"
                  @click="currentCertificateIndex = index"
              ></button>
            </div>
            <button
                class="bg-[#2a2e40] hover:bg-emerald-400 hover:text-black text-white font-black border-2 border-black px-3 py-1 rounded shadow-[2px_2px_0_0_#000] text-xs cursor-pointer"
                @click="nextCert"
            >
              NEXT ▶
            </button>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Modal 4: Contact & Social Info -->
    <Transition name="fade-popup">
      <div
          v-if="linksOpen"
          class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[92%] max-w-[440px] max-h-[90dvh] flex flex-col bg-[#181a24] border-4 border-black rounded-lg shadow-[8px_8px_0_0_#000] z-50 text-slate-100 p-0 overflow-hidden"
      >
        <div class="bg-[#70e2ff] text-black border-b-4 border-black px-3.5 py-2 flex justify-between items-center font-black shrink-0">
          <div class="flex items-center gap-1.5 text-xs sm:text-sm tracking-wider">
            <span>🌐</span> CONTACT_DIRECTORY.SYS
          </div>
          <button
              class="bg-black text-white hover:bg-white hover:text-black border-2 border-black w-6 h-6 sm:w-7 sm:h-7 flex items-center justify-center font-black text-xs sm:text-sm cursor-pointer"
              @click.stop="linksOpen = false"
          >
            ✕
          </button>
        </div>

        <div class="p-4 sm:p-5 overflow-y-auto overflow-x-hidden">
          <div class="text-[11px] text-slate-400 mb-3 pb-1.5 border-b border-gray-700">
            DIRECT CONTACT INFO & SOCIALS:
          </div>

          <div class="mb-3 p-2 bg-[#121318] border border-black rounded text-xs flex items-center gap-2">
            <span>📍 Address:</span>
            <span class="text-[#ffde59] font-bold">{{ contactInfo.address }}</span>
          </div>

          <div class="space-y-2.5">
            <a
                v-for="(item, index) in socialLinks"
                :key="index"
                :href="item.url"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center justify-between p-2.5 bg-[#11131c] hover:bg-[#252a3d] border-2 border-black rounded shadow-[2px_2px_0_0_#000] text-xs sm:text-sm transition group"
            >
              <div class="flex items-center gap-2 text-white font-bold">
                <span>{{ item.icon }}</span> {{ item.platform }}
              </div>
              <span class="text-[11px] sm:text-xs text-[#70e2ff] font-mono group-hover:underline truncate max-w-[190px]">{{ item.display }} ↗</span>
            </a>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Shared Fullscreen Lightbox -->
    <Transition name="fade-lightbox">
      <div
          v-if="isLightboxOpen"
          class="fixed inset-0 z-[70] flex flex-col items-center justify-center bg-black/95 backdrop-blur-md p-4 overflow-y-auto"
          @click="isLightboxOpen = false"
      >
        <button
            class="fixed top-4 right-5 text-white hover:text-[#ff5e7e] font-black text-3xl sm:text-4xl bg-transparent border-none cursor-pointer z-10"
            @click.stop="isLightboxOpen = false"
        >
          ✕
        </button>

        <div class="max-w-[95vw] max-h-[90dvh] flex flex-col items-center my-auto overflow-y-auto p-2" @click.stop>
          <img
              :src="lightboxData.image"
              :alt="lightboxData.title"
              class="max-w-full max-h-[65dvh] sm:max-h-[75dvh] object-contain rounded-lg border-4 border-black shadow-[6px_6px_0_0_#ffde59]"
              @error="(e: any) => { e.target.src = 'https://placehold.co/800x600/181a24/ffffff?text=Image+Missing'; }"
          />
          <div class="mt-3 text-center bg-[#1e2029] border-2 border-black px-3 py-1.5 rounded shadow-[2px_2px_0_0_#000] max-w-full">
            <h3 class="text-sm sm:text-base font-black text-[#ffde59]">{{ lightboxData.title }}</h3>
            <p class="text-xs text-slate-300 mt-0.5">{{ lightboxData.description }}</p>
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
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scale(0.95);
}

.fade-popup-enter-active,
.fade-popup-leave-active {
  transition: opacity 0.15s ease, transform 0.15s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.fade-popup-enter-from,
.fade-popup-leave-to {
  opacity: 0;
  transform: translate(-50%, -50%) scale(0.95);
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