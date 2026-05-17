<template>
  <footer id="footer">
    <n-flex class="link" align="center">
      <n-button
        v-for="(item, key, index) in linkData"
        :key="index"
        :focusable="false"
        quaternary
        circle
        @click="jumpLink(item)"
      >
        <template #icon>
          <Icon :name="`icon:${key}`" />
        </template>
      </n-button>
    </n-flex>
    <n-flex :size="4" class="text" align="center" vertical>
      <n-p depth="3">
        <n-text depth="3" @click="jumpLink(linkData.github)">
          SiteStatus
        </n-text>
        Version {{ version }}
      </n-p>
      <n-p depth="3">
        {{ $t("footer.basedOn") }}
        <n-text depth="3" @click="jumpLink('https://uptimerobot.com/')">
          {{ $t("uptimeRobot") }}
        </n-text>
        {{ $t("footer.interface") }} |
        {{ $t("footer.checkFrequency") }}
        {{ $t("footer.fiveMinutes") }}
      </n-p>
      <n-p depth="3">
        Copyright &copy; 2025 - {{ new Date().getFullYear() }}
        <n-text depth="3" @click="jumpLink(linkData.home)"> BG8IXZ </n-text>
        <n-text
          v-if="siteIcp"
          depth="3"
          @click="jumpLink('https://beian.miit.gov.cn/')"
        >
          | {{ siteIcp }}
        </n-text>
      </n-p>
    </n-flex>
  </footer>
</template>

<script setup lang="ts">
const { public: configPublic } = useRuntimeConfig();
const { siteIcp, version, githubUrl, homeUrl, email } = configPublic;

const defaultLinkData = {
  github: "https://github.com/bg8ixz/UptimeRobot-Site-Status",
  home: "https://www.imkee.com",
  email: "mailto:bg8ixz@foxmail.com",
};

const linkData = {
  github: githubUrl || defaultLinkData.github,
  home: homeUrl || defaultLinkData.home,
  email: email || defaultLinkData.email,
};
</script>

<style lang="scss" scoped>
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px 20px 20px;
  margin-top: auto;
  z-index: 100;
  .text {
    margin-top: 12px;
    .n-p,
    .n-text {
      margin: 0;
      font-size: 13px;
      line-height: 26px;
    }
    .n-text {
      font-weight: bold;
      cursor: pointer;
      &:hover {
        color: var(--normal-color);
      }
    }
  }
}
</style>
