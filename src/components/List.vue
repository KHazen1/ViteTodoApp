<script setup>
    import useTodos from "../composables/useTodos"
  const { pending, completed, changeStatus } = useTodos()
  defineProps({
    isCompleted: {
      default: false,
      type: Boolean,
    },
  })
</script>

<template>
     <div class="w-1/3">
        <h3 class="text-2xl text-center"
        :class="isCompleted ? 'text-orange-600' : 'text-purple-500'" >{{isCompleted ? "Completed" : "Pending"}}</h3>
        <ul class="pt-8 space-y-4">
          <li
           v-for="todo in isCompleted ? completed : pending" 
           :key="todo.id" 
           @click="changeStatus(todo.id)"
           :class="isCompleted ? 'text-purple-600 hover:bg-purple-400' : 'text-orange-600 hover:bg-orange-400'" 
           class="w-full px-4 py-2 font-bold text-center transition-colors duration-500 bg-gray-300 rounded-lg hover:cursor-pointer hover:text-gray-200"
          >
           {{ todo.text }}
          </li>
        </ul>
      </div>
</template>