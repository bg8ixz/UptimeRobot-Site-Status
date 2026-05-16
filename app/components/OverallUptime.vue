<template>
  <div class="overall-uptime">
    <h2 class="title">{{ $t("overall.title") }}</h2>
    <div class="stats">
      <div class="stat-item">
        <n-text class="percent">{{ overallData.last24HoursPercent.toFixed(3) }}%</n-text>
        <n-text class="hours">{{ formatHours(24) }}</n-text>
        <n-text class="label">{{ $t("overall.last24Hours") }}</n-text>
      </div>
      <div class="stat-item">
        <n-text class="percent">{{ overallData.last7DaysPercent.toFixed(3) }}%</n-text>
        <n-text class="hours">{{ formatHours(7 * 24) }}</n-text>
        <n-text class="label">{{ $t("overall.last7Days") }}</n-text>
      </div>
      <div class="stat-item">
        <n-text class="percent">{{ overallData.last30DaysPercent.toFixed(3) }}%</n-text>
        <n-text class="hours">{{ formatHours(30 * 24) }}</n-text>
        <n-text class="label">{{ $t("overall.last30Days") }}</n-text>
      </div>
      <div class="stat-item">
        <n-text class="percent">{{ overallData.last90DaysPercent.toFixed(3) }}%</n-text>
        <n-text class="hours">{{ formatHours(90 * 24) }}</n-text>
        <n-text class="label">{{ $t("overall.last90Days") }}</n-text>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import type { SiteStatusType } from "~~/types/main";

const props = defineProps<{
  sites: SiteStatusType[];
}>();

const formatHours = (hours: number): string => {
  if (hours < 24) {
    return `${hours} hours`;
  } else if (hours === 24) {
    return "24 hours";
  } else {
    const days = hours / 24;
    return `${days} days`;
  }
};

const calculateUptime = (days: number): number => {
  if (!props.sites || props.sites.length === 0) return 100;
  
  let totalPercent = 0;
  let count = 0;
  
  props.sites.forEach((site) => {
    if (site.days && site.days.length > 0) {
      const recentDays = site.days.slice(0, days);
      const avgPercent = recentDays.reduce((sum, day) => sum + (day.percent || 0), 0) / recentDays.length;
      totalPercent += avgPercent;
      count++;
    }
  });
  
  return count > 0 ? totalPercent / count : 100;
};

const overallData = computed(() => ({
  last24HoursPercent: calculateUptime(1),
  last7DaysPercent: calculateUptime(7),
  last30DaysPercent: calculateUptime(30),
  last90DaysPercent: calculateUptime(90),
}));
</script>

<style lang="scss" scoped>
.overall-uptime {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;
  .title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 16px;
    color: var(--n-color-text-primary);
  }
  .stats {
    display: flex;
    background: var(--n-color-bg-elevated);
    border-radius: 12px;
    padding: 24px;
    gap: 16px;
    .stat-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 12px 0;
      &:not(:last-child) {
        border-right: 1px solid var(--n-color-border);
      }
      .percent {
        font-size: 24px;
        font-weight: bold;
        color: var(--n-color-text-primary);
      }
      .hours {
        font-size: 14px;
        color: var(--n-color-text-secondary);
        margin-top: 4px;
      }
      .label {
        font-size: 12px;
        color: var(--n-color-text-tertiary);
        margin-top: 2px;
      }
    }
  }
}
</style>