<script setup>
import { watch, onBeforeUnmount } from "vue";

const props = defineProps({
  open: { type: Boolean, default: false },
});

const emit = defineEmits(["close"]);

function onKeydown(e) {
  if (e.key === "Escape") emit("close");
}

watch(
  () => props.open,
  (isOpen) => {
    document.body.style.overflow = isOpen ? "hidden" : "";
    if (isOpen) document.addEventListener("keydown", onKeydown);
    else document.removeEventListener("keydown", onKeydown);
  },
);

onBeforeUnmount(() => {
  document.body.style.overflow = "";
  document.removeEventListener("keydown", onKeydown);
});
</script>

<template>
  <Teleport to="body">
    <div
      class="modal"
      :class="{ active: open }"
      role="dialog"
      aria-modal="true"
      aria-labelledby="letterTitle"
      :aria-hidden="!open"
      @click.self="emit('close')"
    >
      <div class="letter">
        <button class="close" type="button" aria-label="Tutup surat" @click="emit('close')">
          ×
        </button>

        <h3 id="letterTitle">Untuk Bapak/Ibu Guru,</h3>

        <p>Selamat Hari Guru. ♡</p>

        <p>
          Hari ini adalah tentang Bapak/Ibu. Tentang bagaimana seorang guru, yang mungkin tidak selalu menyadarinya, mampu memberi warna dan cahaya bagi kehidupan murid-muridnya.
        </p>

        <p>
          Semoga setiap hari Bapak/Ibu dipenuhi alasan untuk tersenyum, hal-hal yang menghangatkan hati, dan momen indah yang membuat Bapak/Ibu merasa bahwa mengajar itu benar-benar berarti.
        </p>

        <p>
          Jika ada hari ketika semuanya terasa berat, ingatlah bahwa Bapak/Ibu tidak selalu harus kuat. Beristirahatlah. Bapak/Ibu tetap berharga, bahkan ketika sedang tidak melakukan apa pun.
        </p>

        <p>Terima kasih telah menjadi guru yang sabar, tulus, dan penuh dedikasi. Terima kasih telah hadir dan berjasa dalam kehidupan kami.</p>

        <p>
          Semoga setiap doa baik yang Bapak/Ibu simpan dalam hati perlahan menemukan jalannya kembali kepada Bapak/Ibu.
        </p>

        <p class="letter-sign">Selamat Hari Guru. ♡</p>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
.modal {
  position: fixed;
  inset: 0;
  z-index: 5000;
  background: rgba(49, 35, 48, 0.5);
  backdrop-filter: blur(10px);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  opacity: 0;
  visibility: hidden;
  transition: 0.4s ease;
}

.modal.active {
  opacity: 1;
  visibility: visible;
}

.letter {
  width: min(650px, 100%);
  max-height: 85vh;
  overflow-y: auto;
  background: #fffdf8;
  border-radius: 8px;
  padding: 55px;
  position: relative;
  box-shadow: 0 30px 100px rgba(0, 0, 0, 0.2);
  transform: translateY(30px) scale(0.96);
  transition: 0.4s ease;
}

.modal.active .letter {
  transform: translateY(0) scale(1);
}

.close {
  position: absolute;
  right: 18px;
  top: 15px;
  border: none;
  background: transparent;
  font-size: 24px;
  color: #8b7883;
  cursor: pointer;
}

.letter h3 {
  font-family: var(--font-serif);
  font-size: 40px;
  margin-bottom: 25px;
  color: var(--pink);
}

.letter p {
  font-family: var(--font-serif);
  font-size: 21px;
  line-height: 1.8;
  color: #5f4e58;
  margin-bottom: 20px;
}

.letter-sign {
  margin-top: 30px;
  font-family: var(--font-serif);
  font-size: 27px !important;
  color: var(--purple-dark) !important;
  font-style: italic;
}

@media (max-width: 700px) {
  .letter {
    padding: 40px 25px;
  }

  .letter h3 {
    font-size: 34px;
  }

  .letter p {
    font-size: 19px;
  }
}
</style>
