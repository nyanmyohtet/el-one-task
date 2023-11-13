<script setup lang="ts">
import { ref } from 'vue'
// import { useMessage } from 'naive-ui';
import { MdAdd, MdRemove } from '@vicons/ionicons4'

// const message = useMessage()
const textInput = ref('')
const taskList = ref([])

const onSubmit = () => {
  if (textInput.value.length > 0) {
    taskList.value.push(textInput.value)
    textInput.value = ''
  }
}

const removeTask = (index: any) => {
  taskList.value.splice(index, 1)
}
</script>

<template>
  <div>
    <n-layout style="height: 340px; position: relative">
      <n-layout-content position="absolute">
        <n-card size="small" :bordered="false">
          <n-list hoverable>
            <n-list-item v-for="(task, index) in taskList">
              <n-thing :title="task"></n-thing>
              <template #suffix>
                <n-button size="large" @click="removeTask(index)">
                  <template #icon><n-icon><md-remove /></n-icon></template>
                </n-button>
              </template>
            </n-list-item>
          </n-list>
        </n-card>
      </n-layout-content>
      <n-layout-footer bordered position="absolute" style="height: 65px; padding: 0 10px">
        <n-form :style="{ maxWidth: '341px' }">
          <n-form-item>
            <n-input v-model:value="textInput" type="text" size="large" placeholder="New Task" />
            <n-button size="large" style="margin-left: 12px" @click="onSubmit">
              <template #icon>
                <n-icon><md-add /></n-icon>
              </template>
            </n-button>
          </n-form-item>
        </n-form>
      </n-layout-footer>
    </n-layout>
  </div>
</template>

<style scoped>
.n-form-item {
  --n-label-height: 14px !important;
}
</style>
