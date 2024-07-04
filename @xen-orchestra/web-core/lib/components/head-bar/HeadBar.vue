<!-- v1.0 -->
<template>
  <div class="head-bar">
    <div class="label-wrapper">
      <span class="icon">
        <slot name="icon" />
      </span>
      <h4 v-tooltip class="typo h4-medium label">
        <slot />
      </h4>
    </div>
    <div class="status typo c3-regular">
      <slot name="status" />
    </div>
    <div class="actions">
      <slot name="actions" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { vTooltip } from '@core/directives/tooltip.directive'

defineSlots<{
  default: () => any
  icon: () => any
  status: () => any
  actions: () => any
}>()
</script>

<style lang="postcss" scoped>
.head-bar {
  padding: 0.8rem 1.6rem;
  display: flex;
  gap: 4.8rem;
  align-items: center;
  border-bottom: 0.1rem solid var(--color-grey-500);
  background-color: var(--background-color-primary);
}

.label-wrapper {
  display: flex;
  gap: 1.6rem;
  align-items: center;
  min-width: 0;
}

.label {
  color: var(--color-grey-100);
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.icon {
  font-size: 2.4rem;
}

.status {
  color: var(--color-grey-200);
  display: flex;
  align-items: center;
  gap: 1.6rem;
}

.actions {
  margin-inline-start: auto;
  display: flex;
  align-items: center;
  gap: 0.8rem;
}
</style>
