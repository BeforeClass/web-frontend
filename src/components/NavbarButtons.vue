<template>
  <router-link :to="linkRoute">
    <div
      class="block py-2 pr-4 pl-3 text-gray-700 rounded hover:bg-gray-200 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-gray-400 md:dark:hover:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
    >
      {{ linkName }}
    </div>
  </router-link>
</template>

<script>
export default {
  props: {
    linkRoute: String,
    linkName: String,
  },
};
</script>
