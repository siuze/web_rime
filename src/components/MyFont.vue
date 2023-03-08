<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue'

const UbuntuFont = 'Noto Sans CJK SC'
const WindowsFont = 'Microsoft YaHei'
const macOSFont = 'PingFang SC'
const fallbackFont = 'SunmanPUA, TH-Sy-P0, TH-Sy-P16, TH-Sy-P2, TH-Tshyn-P2, TH-Tshyn-P1, TH-Tshyn-P0, TH-Tshyn-P16, HanaMin, TH-Feon'
const style = document.createElement('style')
style.innerHTML = `
  @font-face {
    font-family: 'SunmanPUA';
    font-display: swap;
    src: url('./SunmanPUA.woff2') format("woff2")
  },
  @font-face {
    font-family: 'TH-Feon';
    font-display: swap;
    src: url('./TH-Feon.woff2') format("woff2")
  }`
onMounted(() => {
  const { body } = document
  body.appendChild(style)
  body.style.fontFamily = [
    getComputedStyle(body).fontFamily,
    UbuntuFont,
    WindowsFont,
    macOSFont,
    fallbackFont
  ].join(', ')
})

onUnmounted(() => {
  document.body.removeChild(style)
  document.body.style.fontFamily = ''
})
</script>
