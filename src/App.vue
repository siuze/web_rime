<script setup lang="ts">
import { NConfigProvider, NH1, darkTheme, useOsTheme } from 'naive-ui'
import { MyLayout, MyHeader, MyFooter } from '@libreservice/my-widget'
import MyPwa from './components/MyPwa.vue'
import MyFont from './components/MyFont.vue'
import { homepage, projectpage } from '../package.json'

const osThemeRef = useOsTheme()
</script>

<template>
  <my-pwa />
  <my-font />
  <n-config-provider :theme="osThemeRef === 'dark' ? darkTheme : null">
    <my-layout>
      <template #header>
        <my-header
          icon="./ShanRenMaLTS.svg"
          :homepage="homepage"
        />
      </template>
      <template #content>
        <div style="cursor: pointer; text-align: center; margin-top: 16px">
          <n-h1>山人码LTS 输入体验</n-h1>
        </div>
        <router-view v-slot="{ Component }">
          <keep-alive>
            <component :is="Component" />
          </keep-alive>
        </router-view>
        <p style="padding: 20px;">
          <b>使用提示：</b><br>
          1. 请等待资源加载，资源加载完成后输入框上方的方案选择下拉框内会出现【山人码LTS】字样。<br><br>
          <b>2. 若在键入编码时无法触发山人码LTS，只显示系统正使用的输入法候选项，请按下Shift或同功能的按键以切换到En西文键盘模式，而后点击输入框上方【En】字样的按钮，切换回中文模式，再次尝试输入即可。</b><br><br>
          3. 为减轻资源加载负担，体验页面所示为包含核心词库、支持完整词组输入规则、拼音反查的山人码LTS方案，不含扩展词库、中英混输等功能。<br><br>
          4. 本页面为静态页面，网页加载时方案词典将一并加载到本地执行，无任何数据收集行为，加载资源（含rime相关二进制词库码表）大小约35MB 。<br><br>
          5. 网页将首先获取在线字体资源SunmanPUA以供私用区汉字的显示（下载文件大小约109KB），而后逐个使用尝试调用后备字体TH-Sy-P0, TH-Sy-P16, TH-Sy-P2, TH-Tshyn-P2, TH-Tshyn-P1, TH-Tshyn-P0, TH-Tshyn-P16, HanaMin来显示生僻文字，如若您的本地系统中已经安装上述字体，将直接调用本地字体显示，免去下载网络字体带来的资源浪费。如果您的系统中未安装相关字体使得某些生僻字无法渲染，页面将在线获取并加载最后一道后备字体TH-Feon，下载该字体大约需要10MB。<br><br>
          6. 对于网络质量差造成的词典资源加载失败，可以在输入框上方的方案选择下拉框内再次选中山人码LTS，这会重新尝试加载资源。<br>
        </p>
      </template>
      <template #footer>
        <p class="my-footer">
          使用开源项目<a href="https://github.com/LibreService/my_rime">my_rime</a>进行网页构建，原作者<a href="https://github.com/eagleoflqj">@Qijia Liu</a>，在此致谢。
        </p>
        <my-footer
          class="my-footer"
          :homepage="projectpage"
          commit="__COMMIT__"
          build-date="__BUILD_DATE__"
          copyright="2022-2023 siuze"
        />
      </template>
    </my-layout>
  </n-config-provider>
</template>
