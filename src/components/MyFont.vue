<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue'

const UbuntuFont = 'Noto Sans CJK SC'
const WindowsFont = 'Microsoft YaHei'
const macOSFont = 'PingFang SC'
const fallbackFont = 'SunmanPUA, TH-Tshyn-P2, TH-Tshyn-P1, TH-Tshyn-P0, TH-Tshyn-P16, HanaMin'

onMounted(() => {
  const { body } = document
  body.style.fontFamily = [
    getComputedStyle(body).fontFamily,
    UbuntuFont,
    WindowsFont,
    macOSFont,
    fallbackFont
  ].join(', ')
})

onUnmounted(() => {
  document.body.style.fontFamily = ''
})
</script>
