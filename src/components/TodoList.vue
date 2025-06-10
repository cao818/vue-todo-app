<script setup>
import { ref, onMounted, watch, computed } from 'vue'
import draggable from 'vuedraggable'
import { ElInput, ElButton, ElButtonGroup, ElCheckbox, ElIcon } from 'element-plus'
import { Delete } from '@element-plus/icons-vue'

const newTodo = ref('')
const todos = ref([])
const STORAGE_KEY = 'my-todo-list'

const filter = ref('all')
const filterNames = {
  all: '全部',
  active: '未完成',
  completed: '已完成',
}

const generateId = () => Date.now() + Math.random().toString(16).slice(2)

onMounted(() => {
  try {
    const saved = localStorage.getItem(STORAGE_KEY)
    if (saved) {
      const parsed = JSON.parse(saved)
      if (Array.isArray(parsed)) {
        todos.value = parsed
      }
    }
  } catch (err) {
    console.error('解析本地任务失败', err)
  }
})

watch(
  todos,
  (newTodos) => {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(newTodos))
  },
  { deep: true }
)

const addTodo = () => {
  const value = newTodo.value.trim()
  if (value) {
    todos.value.push({
      id: generateId(),
      text: value,
      done: false,
    })
    newTodo.value = ''
  }
}

const removeTodo = (id) => {
  const idx = todos.value.findIndex(t => t.id === id)
  if (idx !== -1) todos.value.splice(idx, 1)
}

const saveTodos = () => {
  // 触发watch保存localStorage
}

const filteredTodos = computed(() => {
  if (filter.value === 'active') {
    return todos.value.filter(t => !t.done)
  } else if (filter.value === 'completed') {
    return todos.value.filter(t => t.done)
  }
  return todos.value
})

const shouldShow = (todo) => {
  if (filter.value === 'all') return true
  if (filter.value === 'active') return !todo.done
  if (filter.value === 'completed') return todo.done
  return true
}
</script>

<template>
  <div class="todo-container">
    <h2>Todo List</h2>

    <el-input
      v-model="newTodo"
      placeholder="添加新任务"
      @keyup.enter.native="addTodo"
      style="width: 300px; margin-bottom: 16px;"
      clearable
    >
      <template #append>
        <el-button type="primary" @click="addTodo">添加</el-button>
      </template>
    </el-input>

    <el-button-group style="margin-bottom: 16px;">
      <el-button
        v-for="type in ['all', 'active', 'completed']"
        :key="type"
        :type="filter === type ? 'primary' : 'default'"
        @click="filter = type"
      >
        {{ filterNames[type] }}
      </el-button>
    </el-button-group>

    <draggable
      v-model="todos"
      tag="ul"
      class="todo-list"
      item-key="id"
      :animation="200"
      handle=".drag-handle"
      :disabled="filter !== 'all'"
    >
      <template #item="{ element }">
        <li v-if="shouldShow(element)" class="todo-item">
          <span class="drag-handle" title="拖动排序">⠿</span>

          <el-checkbox v-model="element.done" @change="saveTodos">
            <span :class="{ done: element.done }">{{ element.text }}</span>
          </el-checkbox>

          <el-button
            type="text"
            circle
            @click="removeTodo(element.id)"
            aria-label="删除任务"
          >
            <el-icon><Delete /></el-icon>
          </el-button>
        </li>
      </template>
    </draggable>
  </div>
</template>

<style scoped>
.todo-container {
  max-width: 400px;
  margin: 0 auto;
  font-family: 'Arial', sans-serif;
}

.todo-list {
  list-style: none;
  padding: 0;
  margin: 0 auto;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgb(0 0 0 / 0.1);
  overflow: hidden;
}

.todo-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  border-bottom: 1px solid #f0f0f0;
  transition: background-color 0.25s ease;
}

.todo-list li:last-child {
  border-bottom: none;
}

.todo-list li:hover {
  background-color: #f9f9f9;
}

.todo-item {
  display: flex;
  align-items: center;
  gap: 12px;
  flex: 1;
}

.drag-handle {
  cursor: grab;
  font-size: 1.5rem;
  color: #bbb;
  user-select: none;
  padding-right: 8px;
  transition: color 0.2s ease;
}

.drag-handle:hover {
  color: #409eff;
}

.done {
  text-decoration: line-through;
  color: #999;
  transition: color 0.3s ease;
}

.el-button--text {
  color: #f56c6c;
  transition: color 0.3s ease;
}

.el-button--text:hover {
  color: #f44336;
}
</style>
