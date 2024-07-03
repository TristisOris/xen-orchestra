<!-- v1.0 -->
<template>
  <td class="cell-text">
    <div class="data typo p2-regular">
      <slot />
      <span class="info typo p4-regular">
        <slot name="secondary-label" />
      </span>
    </div>
  </td>
</template>

<script lang="ts" setup>
defineSlots<{
  default: () => any
  'secondary-label': () => any
}>()
</script>

<style lang="postcss" scoped>
.cell-text {
  padding: 0.8rem;
  border: 0.1rem solid var(--color-grey-500);
}

.data {
  display: flex;
  gap: 1.6rem;
  align-items: center;
}

.info {
  color: var(--color-grey-300);
}
</style>
