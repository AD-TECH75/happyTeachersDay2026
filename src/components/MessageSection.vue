<script setup>
import { useTypewriter } from "@/composables/useTypewriter";

const message = `
      Selamat Hari Guru. Semoga hari ini mengingatkan Bapak/Ibu bahwa setiap ilmu dan kasih sayang yang diberikan sangat berarti. Semoga tahun-tahun mendatang membawa lebih banyak kebahagiaan, kedamaian, tawa, dan kisah indah yang belum sempat Bapak/Ibu rasakan.
      ♡
    `;

const { typedText, targetRef } = useTypewriter(message, { speed: 25 });
</script>

<template>
  <section class="intro" id="message">
    <div class="container">
      <p class="section-label" data-aos="fade-up">untuk Anda</p>

      <h2 class="section-title" data-aos="fade-up">Selamat Hari Guru</h2>

      <p class="section-desc" data-aos="fade-up">
        Halaman kecil ini untuk seseorang yang layak menerima banyak hal baik hari ini.
      </p>

      <div class="intro-card" data-aos="fade-up" data-aos-delay="200">
        <p ref="targetRef" class="typing-text">{{ typedText }}</p>

        <p class="signature">— dari seseorang yang menghargai Anda ♡</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.intro {
  background: white;
}

.intro-card {
  margin-top: 55px;
  padding: 55px;
  border-radius: 35px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.9), rgba(255, 239, 247, 0.8));
  box-shadow: var(--shadow);
  text-align: center;
  position: relative;
  overflow: hidden;
}

.intro-card::before {
  content: "♡";
  position: absolute;
  right: -30px;
  top: -70px;
  font-size: 250px;
  color: rgba(255, 126, 182, 0.08);
  font-family: serif;
}

.typing-text {
  position: relative;
  max-width: 700px;
  margin: auto;
  min-height: 6em;
  white-space: pre-line;
  font-family: var(--font-serif);
  font-size: 30px;
  line-height: 1.6;
  color: #604c59;
}

.signature {
  position: relative;
  margin-top: 30px;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 25px;
  color: var(--pink);
}

@media (max-width: 700px) {
  .intro-card {
    padding: 35px 22px;
  }

  .typing-text {
    font-size: 24px;
  }
}
</style>
