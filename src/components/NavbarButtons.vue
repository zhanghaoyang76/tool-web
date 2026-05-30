<script setup lang="ts">
import { IconBrandGithub, IconBrandWechat, IconInfoCircle, IconMoon, IconSun } from '@tabler/icons-vue';
import { useStyleStore } from '@/stores/style.store';

const styleStore = useStyleStore();
const { isDarkTheme } = toRefs(styleStore);
const showWechat = ref(false);
</script>

<template>
  <c-tooltip :tooltip="$t('home.nav.github')" position="bottom">
    <c-button
      circle
      variant="text"
      href="https://github.com/zhanghaoyang76/tool-web"
      target="_blank"
      rel="noopener noreferrer"
      :aria-label="$t('home.nav.githubRepository')"
    >
      <n-icon size="25" :component="IconBrandGithub" />
    </c-button>
  </c-tooltip>

  <c-tooltip tooltip="微信" position="bottom">
    <c-button circle variant="text" aria-label="微信" @click="showWechat = true">
      <n-icon size="25" :component="IconBrandWechat" />
    </c-button>
  </c-tooltip>

  <n-modal v-model:show="showWechat">
    <div class="wechat-modal">
      <h3>扫码添加微信</h3>
      <img src="/images/QR-code.jpg" alt="微信二维码" class="wechat-qr-code">
    </div>
  </n-modal>

  <c-tooltip :tooltip="$t('home.nav.about')" position="bottom">
    <c-button circle variant="text" to="/about" :aria-label="$t('home.nav.aboutLabel')">
      <n-icon size="25" :component="IconInfoCircle" />
    </c-button>
  </c-tooltip>
  <c-tooltip :tooltip="isDarkTheme ? $t('home.nav.lightMode') : $t('home.nav.darkMode')" position="bottom">
    <c-button circle variant="text" :aria-label="$t('home.nav.mode')" @click="() => styleStore.toggleDark()">
      <n-icon v-if="isDarkTheme" size="25" :component="IconSun" />
      <n-icon v-else size="25" :component="IconMoon" />
    </c-button>
  </c-tooltip>
</template>

<style lang="less" scoped>
.n-button {
  &:not(:last-child) {
    margin-right: 5px;
  }
}

.wechat-modal {
  background: #fff;
  padding: 20px;
  border-radius: 10px;
  text-align: center;

  h3 {
    margin-top: 0;
  }
}

.wechat-qr-code {
  width: 250px;
  max-width: 70vw;
}
</style>
