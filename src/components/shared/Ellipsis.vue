<script setup lang="ts">
const props = withDefaults(defineProps<{
  content: string
  type?: 'text' | 'tags'
  placement?: 'top' | 'top-start' | 'top-end' | 'bottom' | 'bottom-start' | 'bottom-end'
  | 'left' | 'left-start' | 'left-end' | 'right' | 'right-start' | 'right-end'
  maxWidth?: number
  lineClamp?: number
}>(), {
  type: 'text',
  maxWidth: 150,
  lineClamp: 1,
  placement: 'top-start',
})

const disabledTooltip = ref(true)

const lineClampContent = ref(`line-clamp-${props.lineClamp}`)
function mouseEnter(event) {
  if (event.target.offsetWidth < event.target.scrollWidth)
    disabledTooltip.value = false

  else if (event.target.offsetHeight < event.target.scrollHeight)
    disabledTooltip.value = false
  else disabledTooltip.value = true
}
</script>

<template>
  <el-tooltip
    :disabled="disabledTooltip"
    :placement="placement"
  >
    <el-tag
      v-if="type === 'tags'"
      style="margin: 0 3px 5px 3px"
      type="info"
      v-bind="$attrs"
    >
      <div class="max-w-120px truncate" @mouseenter="mouseEnter">
        {{ content }}
      </div>
    </el-tag>
    <div v-else v-bind="$attrs" :class="lineClampContent" @mouseenter="mouseEnter">
      {{ content }}
    </div>
    <template #content>
      <div class="scroll-custom-app max-h-200px max-w-240px overflow-auto">
        {{ content }}
      </div>
    </template>
  </el-tooltip>
</template>
