<template>
  <!-- not completed -->
  <h1 class="text-3xl font-extrabold text-center lg:text-left dark:text-gray-300 py-5 text-gray-600 mb-10">
    Pre-requisite Tree
  </h1>
  <div class="w-full overflow-x-auto">
    <div class="flex justify-between text-center grid-cols-5 text-black dark:text-gray-300">
      <div class="col-span-1 z-10 sm:p-3 p-1.5 rounded-lg border-blue-300 border-2 my-auto">
        <h5 class="text-sm font-bold dark:text-white pb-2 px-2">
          Prerequisites
        </h5>
        <!-- displaying mods -->
        <div v-if="{ isOr }" class="flex-row flex space-x-2">
          <div v-for="mod in computedPreReqArr">
            <router-link :to="`/module/${mod}`">
              <div
                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-3 py-2 sm:px-5 xs:py-2.5 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800 mx-auto">
                {{ mod }}

              </div>
            </router-link>
          </div>
        </div>
        <div v-else class="flex-col flex space-y-2">
          <div v-for="mod in computedPreReqArr">
            <router-link :to="`/module/${mod}`">
              <div
                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-3 py-2 sm:px-5 xs:py-2.5 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
                {{ mod }}
              </div>
            </router-link>
          </div>
        </div>
      </div>
      <hr class="my-auto min-w-[2rem] col-span-1 w-full h-1 bg-gray-300 rounded border-0 dark:bg-gray-700" />
      <!-- this is the module currently being viewed -->
      <div class="col-span-1 z-10 sm:p-3 p-1.5 rounded-lg border-blue-300 border-2 my-auto">
        <button type="button"
          class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-3 py-2 sm:px-5 sm:py-2.5 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
          {{ moduleName }}
        </button>
      </div>
      <hr class="my-auto min-w-[2rem] col-span-1 w-full h-1 bg-gray-300 rounded border-0 dark:bg-gray-700" />

      <!-- dependency mods (requires advanced querying to retrieve information to display)-->
      <!-- should also be an array of modules to loop through -->
      <div class="col-span-1 z-10 sm:p-3 p-1.5 rounded-lg border-blue-300 border-2 my-auto">
        <h5 class="text-sm font-bold dark:text-white pb-2 px-2">
          Dependencies
        </h5>

        <div class="flex-col flex space-y-2">
          <button type="button"
            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-3 py-2 sm:px-5 sm:py-2.5 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
            <a :href="'/modules'">
              Mods
            </a>
          </button>
          <button type="button"
            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-3 py-2 sm:px-5 sm:py-2.5 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
            <a :href="'/modules'">
              Mods
            </a>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  props: {
    moduleName: {
      type: String,
      default: "None",
    },

    prerequisites: {
      type: Array,
      default: ["None"],
    },
    isOr: {
      type: Boolean,
      default: false,
    },
  },
  components: {
    Button,
  },
  computed: {
    computedPreReqArr() {
      return this.prerequisites == [] ? ["None"] : this.prerequisites;
    },
  },
};
</script>
