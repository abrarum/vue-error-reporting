<template>
  <div class="flex md:flex-row-reverse flex-wrap">
    <!--Main Content-->
    <div class="w-full md:w-4/5 bg-gray-100">
      <div class="container bg-gray-100 pt-16 px-6">
        <span
          @click="undoAction()"
          :class="[
            opInProgress == false ? 'hidden' : '',
            'px-1.5',
            'flex',
            'justify-center',
          ]"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="40"
            height="40"
            fill="currentColor"
            class="bi bi-arrow-counterclockwise cursor-pointer transition duration-500 ease-in-out opacity-70 hover:opacity-100"
            viewBox="0 0 16 16"
          >
            <path
              fill-rule="evenodd"
              d="M8 3a5 5 0 1 1-4.546 2.914.5.5 0 0 0-.908-.417A6 6 0 1 0 8 2v1z"
            />
            <path
              d="M8 4.466V.534a.25.25 0 0 0-.41-.192L5.23 2.308a.25.25 0 0 0 0 .384l2.36 1.966A.25.25 0 0 0 8 4.466z"
            />
          </svg>
        </span>

        <div class="flex flex-col mt-8 mb-8 w-3/5 m-auto">
          <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div
              class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8"
            >
              <div
                class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
              >
                <table class="min-w-full divide-y divide-gray-200">
                  <thead class="bg-gray-50">
                    <tr>
                      <th
                        scope="col"
                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                      >
                        <span>
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="16"
                            height="16"
                            fill="currentColor"
                            class="bi bi-hash inline"
                            viewBox="0 0 16 16"
                          >
                            <path
                              d="M8.39 12.648a1.32 1.32 0 0 0-.015.18c0 .305.21.508.5.508.266 0 .492-.172.555-.477l.554-2.703h1.204c.421 0 .617-.234.617-.547 0-.312-.188-.53-.617-.53h-.985l.516-2.524h1.265c.43 0 .618-.227.618-.547 0-.313-.188-.524-.618-.524h-1.046l.476-2.304a1.06 1.06 0 0 0 .016-.164.51.51 0 0 0-.516-.516.54.54 0 0 0-.539.43l-.523 2.554H7.617l.477-2.304c.008-.04.015-.118.015-.164a.512.512 0 0 0-.523-.516.539.539 0 0 0-.531.43L6.53 5.484H5.414c-.43 0-.617.22-.617.532 0 .312.187.539.617.539h.906l-.515 2.523H4.609c-.421 0-.609.219-.609.531 0 .313.188.547.61.547h.976l-.516 2.492c-.008.04-.015.125-.015.18 0 .305.21.508.5.508.265 0 .492-.172.554-.477l.555-2.703h2.242l-.515 2.492zm-1-6.109h2.266l-.515 2.563H6.859l.532-2.563z"
                            />
                          </svg>
                        </span>

                        <span class="align-middle">Error Code</span>
                      </th>
                      <th
                        scope="col"
                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                      >
                        <span
                          ><svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="16"
                            height="16"
                            fill="currentColor"
                            class="bi bi-bug inline"
                            viewBox="0 0 16 16"
                          >
                            <path
                              d="M4.355.522a.5.5 0 0 1 .623.333l.291.956A4.979 4.979 0 0 1 8 1c1.007 0 1.946.298 2.731.811l.29-.956a.5.5 0 1 1 .957.29l-.41 1.352A4.985 4.985 0 0 1 13 6h.5a.5.5 0 0 0 .5-.5V5a.5.5 0 0 1 1 0v.5A1.5 1.5 0 0 1 13.5 7H13v1h1.5a.5.5 0 0 1 0 1H13v1h.5a1.5 1.5 0 0 1 1.5 1.5v.5a.5.5 0 1 1-1 0v-.5a.5.5 0 0 0-.5-.5H13a5 5 0 0 1-10 0h-.5a.5.5 0 0 0-.5.5v.5a.5.5 0 1 1-1 0v-.5A1.5 1.5 0 0 1 2.5 10H3V9H1.5a.5.5 0 0 1 0-1H3V7h-.5A1.5 1.5 0 0 1 1 5.5V5a.5.5 0 0 1 1 0v.5a.5.5 0 0 0 .5.5H3c0-1.364.547-2.601 1.432-3.503l-.41-1.352a.5.5 0 0 1 .333-.623zM4 7v4a4 4 0 0 0 3.5 3.97V7H4zm4.5 0v7.97A4 4 0 0 0 12 11V7H8.5zM12 6a3.989 3.989 0 0 0-1.334-2.982A3.983 3.983 0 0 0 8 2a3.983 3.983 0 0 0-2.667 1.018A3.989 3.989 0 0 0 4 6h8z"
                            /></svg
                        ></span>

                        <span class="align-middle">Error Text</span>
                      </th>
                      <th
                        scope="col"
                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                      >
                        <span>
                          <svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="16"
                            height="16"
                            fill="currentColor"
                            class="bi bi-bell inline"
                            viewBox="0 0 16 16"
                          >
                            <path
                              d="M8 16a2 2 0 0 0 2-2H6a2 2 0 0 0 2 2zM8 1.918l-.797.161A4.002 4.002 0 0 0 4 6c0 .628-.134 2.197-.459 3.742-.16.767-.376 1.566-.663 2.258h10.244c-.287-.692-.502-1.49-.663-2.258C12.134 8.197 12 6.628 12 6a4.002 4.002 0 0 0-3.203-3.92L8 1.917zM14.22 12c.223.447.481.801.78 1H1c.299-.199.557-.553.78-1C2.68 10.2 3 6.88 3 6c0-2.42 1.72-4.44 4.005-4.901a1 1 0 1 1 1.99 0A5.002 5.002 0 0 1 13 6c0 .88.32 4.2 1.22 6z"
                            />
                          </svg>
                        </span>
                        <span class="align-middle">Status</span>
                      </th>
                      <th></th>
                      <th></th>
                    </tr>
                  </thead>

                  <tbody
                    class="bg-white divide-y divide-gray-200"
                    name="lister"
                    is="transition-group"
                  >
                    <tr
                      :class="{ 'lister-item': isActive }"
                      v-for="error in filterList"
                      :key="error.index"
                    >
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="flex items-center">
                          <div class="">
                            <div class="text-sm font-medium text-gray-900">
                              {{ error.code }}
                            </div>
                          </div>
                        </div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-gray-900">
                          {{ error.text }}
                        </div>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        <span
                          :class="[
                            error.status == c_s[0]
                              ? 'bg-green-100 text-green-800'
                              : error.status == c_s[1]
                              ? 'bg-red-100 text-red-800'
                              : 'bg-gray-100 text-gray-800',
                            'px-2 inline-flex text-xs leading-5 font-semibold rounded-full',
                          ]"
                        >
                          {{ error.status }}
                        </span>
                      </td>
                      <td :class="[active_nav == 0 ? 'hidden' : '', 'px-1.5']">
                        <svg
                          v-on:click="updateData(error, c_s[0])"
                          xmlns="http://www.w3.org/2000/svg"
                          width="16"
                          height="16"
                          fill="currentColor"
                          class="bi bi-check bg-green-600 rounded-lg text-white cursor-pointer transition duration-500 ease-in-out opacity-70 hover:opacity-100"
                          viewBox="0 0 16 16"
                        >
                          <path
                            d="M10.97 4.97a.75.75 0 0 1 1.07 1.05l-3.99 4.99a.75.75 0 0 1-1.08.02L4.324 8.384a.75.75 0 1 1 1.06-1.06l2.094 2.093 3.473-4.425a.267.267 0 0 1 .02-.022z"
                          />
                        </svg>
                      </td>
                      <td :class="[active_nav == 1 ? 'hidden' : '', 'px-1.5']">
                        <svg
                          v-on:click="updateData(error, c_s[1])"
                          xmlns="http://www.w3.org/2000/svg"
                          width="16"
                          height="16"
                          fill="currentColor"
                          class="bi bi-x bg-red-600 rounded-lg text-white cursor-pointer transition duration-500 ease-in-out opacity-70 hover:opacity-100"
                          viewBox="0 0 16 16"
                        >
                          <path
                            d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"
                          />
                        </svg>
                      </td>

                      <td :class="[active_nav == 2 ? 'hidden' : '', 'px-1.5']">
                        <svg
                          v-on:click="updateData(error, c_s[2])"
                          xmlns="http://www.w3.org/2000/svg"
                          width="16"
                          height="16"
                          fill="currentColor"
                          class="bi bi-box-arrow-left text-gray-500 cursor-pointer transition duration-500 ease-in-out opacity-70 hover:opacity-100"
                          viewBox="0 0 16 16"
                        >
                          <path
                            fill-rule="evenodd"
                            d="M6 12.5a.5.5 0 0 0 .5.5h8a.5.5 0 0 0 .5-.5v-9a.5.5 0 0 0-.5-.5h-8a.5.5 0 0 0-.5.5v2a.5.5 0 0 1-1 0v-2A1.5 1.5 0 0 1 6.5 2h8A1.5 1.5 0 0 1 16 3.5v9a1.5 1.5 0 0 1-1.5 1.5h-8A1.5 1.5 0 0 1 5 12.5v-2a.5.5 0 0 1 1 0v2z"
                          />
                          <path
                            fill-rule="evenodd"
                            d="M.146 8.354a.5.5 0 0 1 0-.708l3-3a.5.5 0 1 1 .708.708L1.707 7.5H10.5a.5.5 0 0 1 0 1H1.707l2.147 2.146a.5.5 0 0 1-.708.708l-3-3z"
                          />
                        </svg>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!--Sidebar-->
      <div
        class="w-full md:w-1/5 bg-gray-900 md:bg-gray-900 px-2 text-center fixed bottom-0 md:pt-8 md:top-0 md:left-0 h-16 md:h-screen md:border-r-4 md:border-gray-600"
      >
        <div class="md:relative mx-auto lg:float-right lg:px-6">
          <ul
            class="list-reset flex flex-row md:flex-col text-center md:text-left"
          >
            <li
              v-for="(item, index) in c_s"
              :key="index"
              @click="
                isActive = true;
                active_nav = index;
                opInProgress = false;
              "
              class="mr-3 flex-1"
            >
              <a
                class="block py-1 md:py-3 pl-1 align-middle text-gray-800 no-underline hover:text-pink-500 border-b-2 border-gray-800 md:border-gray-900 hover:border-blue-500"
                :class="{ active_button: isActive && active_nav == index }"
                href="#"
              >
                <i class="fas fa-link pr-0 md:pr-3 text-pink-500"></i
                ><span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block capitalize"
                  :class="{ active_span: isActive && active_nav == index }"
                  >{{ item }}</span
                >
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      const { resolved, unresolved, backlog } = await $axios.$get(
        "http://localhost:8000/get_lists"
      );
      return {
        all_data: [resolved, unresolved, backlog],
      };
    } catch (error) {
      console.log(
        `Couldn't get error lists:\n${error}\nDid you start the API?`
      );
      console.log(
        "HINT: You can comment out the full `asyncData` method and work with mocked data for UI/UX development, if you want to."
      );
    }
  },
  mounted: function () {
    document.addEventListener("keydown", this.keyHandler);
    console.log("mounted", this.all_data);
  },
  methods: {
    keyHandler: function (event) {
      if (event.ctrlKey && event.key === "z") {
        this.undoAction();
      }
    },

    updateData: function (error, new_status) {
      this.opInProgress = true;
      this.lastAction = [error, new_status];

      console.log("updating data");
      console.log("error, new_status", error, new_status, error.index);
      //this.$set(error, "status", new_status);

      let op = this.c_s.indexOf(new_status);

      if (new_status == this.c_s[op]) {
        let temp = JSON.parse(JSON.stringify(error));
        temp.status = new_status;

        for (let i in this.all_data[this.active_nav]) {
          if (this.all_data[this.active_nav][i].index == error.index) {
            let myIndex = this.all_data[this.active_nav].indexOf(
              this.all_data[this.active_nav][i]
            );
            this.all_data[this.active_nav].splice(myIndex, 1);
            this.all_data[op].unshift(temp);
          }
        }
      }
    },
    undoAction: function () {
      console.log("inside undoAction");
      // only if the action is performed and the page is not navigated
      if (this.opInProgress) {
        let error = this.lastAction[0];
        let new_status = this.lastAction[1];

        let op = this.c_s.indexOf(new_status);

        if (error.status == this.c_s[this.active_nav]) {
          let temp = JSON.parse(JSON.stringify(error));
          temp.status = error.status;

          for (let i in this.all_data[op]) {
            if (this.all_data[op][i].index == error.index) {
              let myIndex = this.all_data[op].indexOf(this.all_data[op][i]);
              this.all_data[op].splice(myIndex, 1);
              this.all_data[this.active_nav].unshift(temp);
            }
          }
        }
        this.opInProgress = false;
      }

      //console.log("error, new_status", error, new_status)
    },
  },
  computed: {
    filterList: function () {
      console.log("inside filter list: ");
      let l = this.all_data[this.active_nav].length / 2;
      console.log("l is: ", l);
      return this.all_data[this.active_nav].slice(0, Math.ceil(l));
    },
  },
  data() {
    return {
      c_s: ["resolved", "unresolved", "backlog"],
      active_nav: 0,
      opInProgress: false,
      lastAction: [],
      isActive: true,
      activeState: [],
      all_data: [],
    };
  },
};
</script>

<style scoped>
.active_button {
  @apply block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-blue-600;
}
.active_span {
  @apply pb-1 md:pb-0 text-xs md:text-base text-white md:font-bold block md:inline-block;
}


.lister-item {
  transition: all 0.2s;
}
.lister-item > * {
  transition: all 0.2s;
  overflow: hidden;
}
.lister-enter,
.lister-leave-to {
  line-height: 0;
}
.lister-enter > *,
.lister-leave-to > * {
  padding-top: 0px !important;
  padding-bottom: 0px !important;
}
.lister-enter-to,
.lister-leave {
  line-height: 1.5;
}

</style>