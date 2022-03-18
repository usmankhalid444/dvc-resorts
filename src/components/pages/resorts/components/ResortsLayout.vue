<template>
  <div>
    <Header />
    <div class="main-page body-font-size bg-custom-bg1 text-custom-blue4 pb-10">
      <!-- page title-->
      <div class="flex justify-center">
        <div class="left-sidebar-menu hidden w-1/6 lg:block"></div>
        <div class="page-content-body w-11/12 lg:w-4/6">
          <!-- main content start  -->
          <ResortsMenu />
          <slot></slot>
          <!-- main content end -->
        </div>
        <div class="right-sidebar hidden w-1/6 lg:block">
          <div class="relative">
            <button
              v-if="!feedback"
              @click="feedback = !feedback"
              class="bg-custom-orange4 absolute -right-9 top-9 float-right rotate-90 transform cursor-pointer px-5 text-2xl text-white"
            >
              Feedback
            </button>
            <div
              class="border-custom-darkblue bg-custom-lightcream absolute right-0 w-72 transform border px-5 py-3 transition-all duration-700 ease-in-out"
              :class="feedback ? '-translate-x-0' : 'translate-x-full'"
            >
              <i
                @click="feedback = false"
                class="fas fa-window-close float-right block cursor-pointer text-3xl text-red-500"
              ></i>
              <br />
              <p
                class="text-custom-orange4 border-b-2 border-gray-300 pb-2 text-center text-3xl font-bold"
              >
                FEEDBACK
              </p>
              <div class="mt-3">
                <star-rating
                  :increment="0.5"
                  star-size="30"
                  active-color="#337ab7"
                  inactive-color="#FFFFFF"
                  border-color="#6ba3d4"
                  border-width="1"
                  rating="4.5"
                  text-class="ml-10"
                  :show-rating="false"
                />
              </div>
              <p class="my-4 text-2xl">
                What can we do to improve our business?
              </p>
              <textarea
                class="border p-4"
                rows="4"
                placeholder="type your comments here."
              ></textarea>
              <p class="border-b-2 border-gray-300 pb-2 text-2xl">
                Thanks for your feedback.
              </p>
              <div class="mt-4 mb-4 text-center">
                <button
                  class="bg-custom-blue2 hover:bg-custom-blue3 rounded px-5 py-1 text-white"
                >
                  Submit
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Header from "../../../layout/header/Header";
import ResortsMenu from "../components/ResortsMenu";
import StarRating from "vue-star-rating";
export default {
  components: { Header, ResortsMenu, StarRating },
  data() {
    return {
      feedback: false,
    };
  },
};
</script>
