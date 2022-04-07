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
                    class="mb-2 inline text-left text-3xl text-custom-orange2"
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
              <p class="text-center text-2xl text-custom-green1">
                ( 2 Nights )
              </p>
            </div>
          </section>
          <!-- date picker end -->
          <!-- room points start -->
          <section>
            <div
              class="custom-scrollbar relative mx-auto mt-5 h-96 w-full xl:w-11/12"
              :class="range.start == '' ? 'overflow-hidden' : 'overflow-x-auto'"
            >
              <table class="w-full text-xl">
                <thead class="sticky top-0">
                  <tr class="bg-custom-blue4 text-white">
                    <th class="pl-5 text-left">RESORT</th>
                    <th class="text-left">VIEW</th>
                    <th class="text-left">STUDIO</th>
                    <th class="text-left">ONE BEDROOM</th>
                    <th class="text-left">TWO BEDROOM</th>
                    <th class="text-left">THREE BEDROOM</th>
                    <th class="text-left">OTHER</th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="(resort, i) in resort_points"
                    :key="i"
                    class="group odd:bg-custom-lightcream hover:bg-custom-lightergreen"
                  >
                    <td class="pl-5">
                      <p>{{ resort.name }}</p>
                      <button
                        class="my-2 hidden rounded bg-custom-green1 py-0.5 px-1 text-white group-hover:block"
                      >
                        Point Chart
                      </button>
                    </td>
                    <td>
                      <p v-for="(view, i) in resort.view" :key="i">
                        {{ view }}
                      </p>
                    </td>
                    <td>
                      <p v-for="(studio, i) in resort.studio" :key="i">
                        {{ studio }}
                      </p>
                    </td>
                    <td>
                      <p v-for="(one_bed, i) in resort.one_bedroom" :key="i">
                        {{ one_bed }}
                      </p>
                    </td>
                    <td>
                      <p v-for="(two_bed, i) in resort.two_bedroom" :key="i">
                        {{ two_bed }}
                      </p>
                    </td>
                    <td>
                      <p
                        v-for="(three_bed, i) in resort.three_bedroom"
                        :key="i"
                      >
                        {{ three_bed }}
                      </p>
                    </td>
                    <td>
                      <p v-for="(other, i) in resort.other" :key="i">
                        {{ other }}
                      </p>
                    </td>
                  </tr>
                </tbody>
              </table>
              <div v-if="range.start == ''">
                <div
                  class="absolute top-0 h-35rem w-full bg-gray-400 text-center opacity-40"
                ></div>
                <div class="absolute top-0 w-full text-center">
                  <span
                    class="mt-32 inline-block rounded bg-custom-lightcream px-5 py-1 text-5xl"
                  >
                    Select date above
                  </span>
                </div>
              </div>
            </div>
          </section>
          <!-- room points end -->
          <!-- point chart start -->
          <section>
            <div
              class="custom-scrollbar mx-auto mt-8 mb-14 w-full overflow-auto"
            >
              <p class="text-center text-3xl">Animal Kingdom - 2022</p>
              <table class="mt-5 w-full">
                <thead>
                  <tr class="bg-custom-blue3 text-white">
                    <th>Dates</th>
                    <th class="w-1/12">Days</th>
                    <th class="border-l border-r-2 border-white" colspan="4">
                      Studio
                    </th>
                    <th class="border-l border-r-2 border-white" colspan="4">
                      One Bedroom
                    </th>
                    <th class="border-l border-r-2 border-white" colspan="4">
                      Two Bedrrom
                    </th>
                    <th class="border-l border-r-2 border-white" colspan="2">
                      Grand Villa
                    </th>
                  </tr>
                  <tr class="bg-custom-blue2 text-white">
                    <th class="w-12 bg-custom-blue3 px-1 font-normal"></th>
                    <th class="w-12 bg-custom-blue3 px-1 font-normal"></th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Value
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Standard
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Savana
                    </th>
                    <th
                      class="w-12 border border-r-2 border-white px-1 font-normal"
                    >
                      Club
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Value
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Standard
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Savana
                    </th>
                    <th
                      class="w-12 border border-r-2 border-white px-1 font-normal"
                    >
                      Club
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Value
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Standard
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Savana
                    </th>
                    <th
                      class="w-12 border border-r-2 border-white px-1 font-normal"
                    >
                      Club
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Standard
                    </th>
                    <th class="w-12 border border-white px-1 font-normal">
                      Savana
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr class="even:bg-custom-lightcream">
                    <td class="px-1 text-center" rowspan="3">
                      <div class="text-lg">
                        <p>Jan 31</p>
                        <p>Dec 14</p>
                        <p>Dec 14</p>
                      </div>
                    </td>
                    <td class="px-1 text-center">Sun - Thu</td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                  </tr>
                  <tr class="even:bg-custom-lightcream">
                    <td class="px-1 text-center">Fri - Sat</td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td
                      class="border border-r-2 border-custom-blue2 px-1 text-center"
                    >
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                    <td class="border border-custom-blue2 px-1 text-center">
                      10
                    </td>
                  </tr>
                  <tr class="even:bg-custom-lightcream">
                    <td class="px-1 text-center">Weekly Total</td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-r-2 border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-r-2 border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-r-2 border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                    <td
                      class="border border-white bg-custom-blue2 px-1 text-center text-white"
                    >
                      10
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
            <div class="mt-8">
              <button
                v-for="(year, i) in years"
                :key="i"
                @click="selected_year = year"
                class="m-3 rounded border border-custom-blue2 px-8 py-1"
                :class="
                  selected_year === year
                    ? 'bg-custom-blue2 text-white'
                    : 'bg-custom-lightcream'
                "
              >
                {{ year }}
              </button>
              <button
                @click="show_weekly_total = !show_weekly_total"
                class="m-3 rounded border border-custom-blue2 bg-custom-blue2 px-5 py-1 text-white md:float-right"
              >
                Show Weekly Total
              </button>
            </div>
          </section>
          <!-- point chart send -->
          <section>
            <div class="mx-auto mt-5 w-11/12">
              <p class="text-center text-2xl text-custom-orange3 md:text-3xl">
                HOW TO USE THE VACATION POINT CALCULATOR
              </p>
              <div class="mt-5 space-y-3 text-xl md:text-2xl">
                <p>
                  This is our Vacation Point Calculator. The purpose of this
                  tool is to assist buyers as they determine the right size
                  membership for their family.
                </p>
                <p>
                  There are Point Charts for each of the 15 Resorts, and the
                  points per night will vary, depending on several factors. A
                  two bedroom villa will naturally require more points per night
                  than a deluxe studio. Do you typically travel during peak or
                  off season? The number of points for each of the Disney
                  Vacation Club Resorts will appear as you input the different
                  dates and room sizes.
                </p>
                <p>
                  As always, please let us know if you have any questions. We
                  look forward to assisting you in any way we can!
                </p>
              </div>
            </div>
          </section>

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
      range: {
        start: "",
        end: "",
      },
      masks: {
        input: "DD-MM-YYYY",
      },
      resort_points: [
        {
          name: "Animal Kingdom",
          view: ["Value", "Standard", "Savana", "Club"],
          studio: [22, 32, 38, 46],
          one_bedroom: [46, 60, 72, 94],
          two_bedroom: [60, 76, 98, 126],
          three_bedroom: ["-", 180, 198, "-"],
          other: ["", "", "", ""],
        },
        {
          name: "Aulani",
          view: ["Standard", "Island", "Poolside", "Ocean"],
          studio: [22, 32, 38, 46],
          one_bedroom: [46, 80, 72, 94],
          two_bedroom: [90, 76, 98, 126],
          three_bedroom: ["-", 182, 198, "-"],
          other: ["Hotel 34", "-", "-", "-"],
        },
        {
          name: "Bay Lake Tower",
          view: ["Standard", "Lake", "Majic"],
          studio: [22, 32, 38],
          one_bedroom: [46, 72, 94],
          two_bedroom: [76, 98, 126],
          three_bedroom: ["-", 198, "-"],
          other: ["", "", ""],
        },
        {
          name: "Beach Club",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "BoarkWalk",
          view: ["Standard", "Prefereed"],
          studio: [22, 32],
          one_bedroom: [72, 94],
          two_bedroom: [90, 126],
          three_bedroom: [182, 198],
          other: ["", ""],
        },
        {
          name: "Boulder Ridge",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "Copper Creek",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "Grand CA",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "Grand Floradian",
          view: ["Standard", "Prefereed"],
          studio: [22, 32],
          one_bedroom: [72, 94],
          two_bedroom: [90, 126],
          three_bedroom: [182, 198],
          other: ["", ""],
        },
        {
          name: "Hilton Head",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "Old Key West",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: [""],
        },
        {
          name: "Polynesian",
          view: ["Standard", "Prefereed"],
          studio: [22, 32],
          one_bedroom: [72, 94],
          two_bedroom: [90, 126],
          three_bedroom: [182, 198],
          other: ["", ""],
        },
        {
          name: "Riviera",
          view: ["Standard", "Prefereed"],
          studio: [22, 32],
          one_bedroom: [72, 94],
          two_bedroom: [90, 126],
          three_bedroom: [182, 198],
          other: ["Tower 36", "-"],
        },
        {
          name: "Saratoga Springs",
          view: ["Standard", "Prefereed"],
          studio: [22, 32],
          one_bedroom: [72, 94],
          two_bedroom: [90, 126],
          three_bedroom: [182, 198],
          other: ["Tree 82", "-"],
        },
        {
          name: "Vero Beach",
          view: ["Standard"],
          studio: [38],
          one_bedroom: [46],
          two_bedroom: [126],
          three_bedroom: ["-"],
          other: ["Inn 30 / 38"],
        },
      ],
      // seasons: {
      //   room: [
      //     {
      //       name: "Studio",
      //       views: [
      //         {
      //           name: "Value",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Standard",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Savana",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Club",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //       ],
      //     },
      //     {
      //       name: "Studio",
      //       type: [
      //         {
      //           name: "Value",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Standard",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Savana",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Club",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //       ],
      //     },
      //     {
      //       name: "One Bedroom",
      //       type: [
      //         {
      //           name: "Value",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Standard",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Savana",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Club",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //       ],
      //     },
      //     {
      //       name: "Two Bedroom",
      //       type: [
      //         {
      //           name: "Value",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Standard",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Savana",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Club",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //       ],
      //     },
      //     {
      //       name: "Grand Villa",
      //       type: [
      //         {
      //           name: "Value",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Standard",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Savana",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //         {
      //           name: "Club",
      //           dates: [
      //             "Feb 1 - 15",
      //             "Jun 11 - Aug 31",
      //             "Oct 1 - Nov 22",
      //             "Nov 26 - Nov 30",
      //           ],
      //           days: "Sun - Thu",
      //           weekly: 50,
      //           weekend: 28,
      //           total: 47,
      //         },
      //       ],
      //     },
      //   ],
      // },

      years: [2019, 2020, 2021, 2022],
      selected_year: 2022,
    };
  },
  methods: {
    usman() {
      console.log(this.range);
    },
  },
};
</script>
<style>
/* width */
.custom-scrollbar::-webkit-scrollbar {
  width: 7px;
}

/* Track */
.custom-scrollbar::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #1f4e79;
  border-radius: 10px;
}

/* Handle on hover */
.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #337ab7;
}
</style>
