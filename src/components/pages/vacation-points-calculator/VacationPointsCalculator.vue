<template>
  <div>
    <Header />
    <div class="main-page bg-custom-bg1 pt-5 pb-12 text-xl text-custom-blue4">
      <!-- page title start-->
      <h1
        class="my-5 text-center font-body text-2xl font-normal uppercase text-custom-primary md:text-pTitle"
      >
        DISNEY VACATION POINTS CALCULATOR
      </h1>
      <!-- page title end-->
      <div class="flex justify-center">
        <div class="left-sidebar-menu hidden w-1/6 lg:block"></div>
        <div class="page-content-body w-11/12 lg:w-4/6">
          <!-- main content start  -->
          <!-- date picker start -->
          <section>
            <div class="mx-auto w-full lg:w-96 xl:w-35rem">
              <form class="rounded px-5 py-3" @submit.prevent>
                <div class="mb-4">
                  <span
                    class="mb-2 block text-left text-3xl text-custom-orange2"
                    >TRAVEL DATES</span
                  >
                  <DatePicker
                    v-model="range"
                    mode="date"
                    :masks="masks"
                    is-range
                  >
                    <template v-slot="{ inputValue, inputEvents, isDragging }">
                      <div
                        class="flex flex-col items-center justify-start sm:flex-row"
                      >
                        <div class="relative flex-grow">
                          <svg
                            class="pointer-events-none absolute mx-2 h-full w-4 text-gray-600"
                            fill="none"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                          >
                            <path
                              d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
                            ></path>
                          </svg>
                          <input
                            class="w-full flex-grow rounded border bg-white py-1 pl-8 pr-2"
                            :class="
                              isDragging ? 'text-gray-600' : 'text-gray-900'
                            "
                            :value="inputValue.start"
                            v-on="inputEvents.start"
                          />
                        </div>
                        <span class="m-2 flex-shrink-0">
                          <svg
                            class="h-4 w-4 stroke-current text-gray-600"
                            viewBox="0 0 24 24"
                          >
                            <path
                              stroke-linecap="round"
                              stroke-linejoin="round"
                              stroke-width="2"
                              d="M14 5l7 7m0 0l-7 7m7-7H3"
                            />
                          </svg>
                        </span>
                        <div class="relative flex-grow">
                          <svg
                            class="pointer-events-none absolute mx-2 h-full w-4 text-gray-600"
                            fill="none"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                          >
                            <path
                              d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
                            ></path>
                          </svg>
                          <input
                            class="w-full flex-grow rounded border bg-white py-1 pl-8 pr-2"
                            :class="
                              isDragging ? 'text-gray-600' : 'text-gray-900'
                            "
                            :value="inputValue.end"
                            v-on="inputEvents.end"
                          />
                        </div>
                      </div>
                    </template>
                  </DatePicker>
                </div>
              </form>
            </div>
          </section>
          <!-- date picker end -->
          <div></div>
          <!-- main content end -->
        </div>
        <div class="right-sidebar hidden w-1/6 lg:block"></div>
      </div>
    </div>
  </div>
</template>
<script>
import Header from "../../layout/header/Header";
import DatePicker from "v-calendar/lib/components/date-picker.umd";
export default {
  components: { Header, DatePicker },
  data() {
    return {
      range: {},
      masks: {
        input: "DD-MM-YYYY",
      },
    };
  },
};
</script>
