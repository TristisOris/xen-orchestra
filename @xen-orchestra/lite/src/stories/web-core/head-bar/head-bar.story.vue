<template>
  <ComponentStory
    v-slot="{ properties, settings }"
    :params="[
      slot().help('Meant to display the label of the object'),
      slot('icon').help('Meant to receive an ObjectIcon or UiIcon component'),
      slot('status').help('Meant to display the status of the object, e.g., migration progress for a VM'),
      slot('actions').help('Meant to receive UiButton or ButtonIcon components that will trigger actions'),
      setting('default').preset('Pool name').widget(),
      setting('showDemoButtons').widget(boolean()),
      setting('showStatusSlotDemoContent').widget(boolean()),
    ]"
  >
    <HeadBar v-bind="properties">
      {{ settings.default }}
      <template #icon>
        <UiIcon :icon="faCity" class="icon" />
      </template>
      <template v-if="settings.showStatusSlotDemoContent" #status>
        <UiSpinner class="spinner" />
        migrating... (34%)
      </template>
      <template v-if="settings.showDemoButtons" #actions>
        <UiButton size="small" :left-icon="faPlus">New VM</UiButton>
        <UiButton size="small" :left-icon="faPowerOff">Change state</UiButton>
      </template>
    </HeadBar>
  </ComponentStory>
</template>

<script lang="ts" setup>
import ComponentStory from '@/components/component-story/ComponentStory.vue'
import { setting, slot } from '@/libs/story/story-param'
import { boolean } from '@/libs/story/story-widget'
import UiButton from '@core/components/button/UiButton.vue'
import HeadBar from '@core/components/head-bar/HeadBar.vue'
import UiIcon from '@core/components/icon/UiIcon.vue'
import UiSpinner from '@core/components/UiSpinner.vue'
import { faCity, faPlus, faPowerOff } from '@fortawesome/free-solid-svg-icons'
</script>

<style lang="scss" scoped>
.spinner {
  font-size: 2rem;
  color: var(--color-purple-base);
}
</style>
