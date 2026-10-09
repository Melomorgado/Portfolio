<script setup lang="ts">
// Static profile view layer
</script>

<template>
  <div>
    <div class="fixed inset-0 pointer-events-none opacity-[0.03] bg-[radial-gradient(#fff_1px,transparent_1px)] [background-size:16px_16px]"></div>

    <!-- Header with Download CV button -->
    <header class="border-b-4 border-black bg-[#1e2029] p-3 shadow-[0_4px_0_0_#000] sticky top-0 z-30">
      <div class="max-w-[1000px] mx-auto flex justify-between items-center gap-3">
        <div class="flex items-center gap-3">
          <span class="text-2xl">🐱</span>
          <div>
            <div class="text-lg sm:text-2xl font-black tracking-wider text-[#ffde59] uppercase drop-shadow-[2px_2px_0_#000]">
              Roan Carmelo G. Morgado
            </div>
            <div class="text-xs text-[#a0a5b5] flex items-center gap-2">
              <span class="bg-[#2a2d3d] text-emerald-400 px-1.5 py-0.5 rounded font-bold border border-black text-[10px]">PORTFOLIO</span>
              <span>BSCpE-4A | CSU CARIG</span>
            </div>
          </div>
        </div>

        <!-- Download CV Button -->
        <a
            href="/cv.pdf"
            download="Roan_Morgado_CV.pdf"
            class="flex items-center gap-2 bg-[#ff5e7e] hover:bg-[#ff7a95] active:translate-x-0.5 active:translate-y-0.5 text-black font-black text-xs sm:text-sm px-3.5 py-2 border-2 border-black rounded shadow-[3px_3px_0_0_#000] transition select-none decoration-transparent"
        >
          <span>📄</span>
          <span>DOWNLOAD CV</span>
        </a>
      </div>
    </header>
  </div>
</template>