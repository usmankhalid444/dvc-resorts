<template>
  <div>
    <Header />
    <div class="main-page bg-custom-bg1 text-custom-blue4 pt-5 pb-12 text-xl">
      <!-- page title start-->
      <h1
        class="md:text-pTitle text-custom-primary font-body my-5 text-center text-2xl font-normal uppercase"
      >
        Testimonials
      </h1>
      <!-- page title end-->
      <div class="flex justify-center">
        <div class="left-sidebar-menu hidden w-1/6 lg:block"></div>
        <div class="page-content-body w-11/12 lg:w-4/6">
          <!-- main content start  -->
          <section>
            <div
              v-for="(testimonial, i) in testimonials"
              :key="i"
              class="mt-10 border-b-2 pb-8"
            >
              <p class="text-2xl">"{{ testimonial.comment }}"</p>
              <img
                v-if="testimonial.img_src.length >= 1"
                class="float-left mt-5 mr-3 h-20 w-20 rounded-full"
                :src="testimonial.img_src"
                alt="user-image"
              />
              <p class="mt-8 text-2xl font-bold">- {{ testimonial.name }}.</p>
              <p>DVC Sales Client {{ testimonial.year }}</p>
            </div>
            <div class="mt-5">
              <button
                v-for="(number, i) in 10"
                :key="i"
                class="bg-custom-blue2 hover:bg-custom-blue3 m-1 h-10 w-10 text-white"
              >
                {{ number }}
              </button>
              <span class="mx-1 text-3xl">...</span>
              <button
                class="bg-custom-blue2 hover:bg-custom-blue3 m-1 h-10 w-10 text-white"
              >
                11
              </button>
              <button
                class="bg-custom-blue2 hover:bg-custom-blue3 m-1 h-10 w-16 text-white"
              >
                Next >
              </button>
            </div>
          </section>
          <section>
            <VueSlickCarousel :autoplay="true" :arrows="false" :dots="true">
              <div
                v-for="(testimonial, i) in testimonials"
                :key="i"
                class="bg-custom-lightyellow border-custom-blue2 mt-10 w-96 py-4 px-8"
              >
                <span class="font-bold">RAVE REVIEWS</span
                ><button
                  class="bg-custom-blue2 hover:bg-custom-blue3 float-right px-5 py-0.5 text-white"
                >
                  View More
                </button>
                <p class="mt-4">
                  {{ testimonial.comment }}
                </p>
                <img
                  v-if="testimonial.img_src.length >= 1"
                  class="float-left mt-5 mr-3 h-20 w-20 rounded-full"
                  :src="testimonial.img_src"
                  alt="user-image"
                />
                <p class="mt-8 text-2xl font-bold">- {{ testimonial.name }}.</p>
                <p>DVC Sales Client {{ testimonial.year }}</p>
              </div>
            </VueSlickCarousel>
          </section>
          <!-- main content end -->
        </div>
        <div class="right-sidebar hidden w-1/6 lg:block">
          <div class="pl-5">
            <div
              class="rounded-md bg-gradient-to-b from-blue-50 to-blue-100 pb-10 shadow-md"
            >
              <VueSlickCarousel
                :autoplay="true"
                :arrows="false"
                :dots="true"
                :adaptiveHeight="true"
              >
                <div v-for="(testimonial, i) in testimonials" :key="i">
                  <div class="border-custom-blue2 text-custom-blue5 py-4 px-8">
                    <span class="font-bold">RAVE REVIEWS</span
                    ><button
                      class="bg-custom-blue2 hover:bg-custom-blue3 float-right px-5 py-0.5 text-white"
                    >
                      View More
                    </button>
                    <p class="mt-4">{{ testimonial.comment }}</p>
                    <img
                      v-if="testimonial.img_src.length >= 1"
                      class="float-left mt-5 mr-3 h-20 w-20 rounded-full"
                      :src="testimonial.img_src"
                      alt="user-image"
                    />
                    <p class="mt-8 text-2xl font-bold">
                      - {{ testimonial.name }}.
                    </p>
                    <p>DVC Sales Client {{ testimonial.year }}</p>
                    <br />
                    <hr class="border border-gray-300" />
                    <!-- <p class="border border-black"></p> -->
                  </div>
                </div>
              </VueSlickCarousel>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Header from "../../layout/header/Header";
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
export default {
  components: { Header, VueSlickCarousel },
  data() {
    return {
      testimonials: [
        {
          img_src: "assets/Lori-Picture.jpg",
          name: "Lori Webb",
          year: 2022,
          comment:
            "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natm ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natm ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natus nisi, nobis tempore facilis provident, voluptas quibusdam iusto aspernatur ea optio soluta deserunt velit.",
        },
        {
          img_src: "",
          name: "Lori Webb",
          year: 2022,
          comment:
            "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natus nisi, nobis tempore facilis provident, voluptas quibusdam iusto aspernatur ea optio soluta deserunt velit.",
        },
        {
          img_src: "assets/Lori-Picture.jpg",
          name: "Lori Webb",
          year: 2022,
          comment:
            "Lorem ipsum, dolor sit amem ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natm ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natt consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natus nisi, nobis tempore facilis provident, voluptas quibusdam iusto aspernatur ea optio soluta deserunt velit.",
        },
        {
          img_src: "",
          name: "Lori Webb",
          year: 2022,
          comment:
            "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fuga culpa error libero rerum. Sed atque natus nisi, nobis tempore facilis provident, voluptas quibusdam iusto aspernatur ea optio soluta deserunt velit.",
        },
      ],
    };
  },
};
</script>
