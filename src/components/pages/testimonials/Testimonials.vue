<template>
  <div>
    <Header />
    <div class="main-page bg-custom-bg1 pt-5 pb-12 text-xl text-custom-blue4">
      <!-- page title start-->
      <h1
        class="my-5 text-center font-body text-2xl font-normal uppercase text-custom-primary md:text-pTitle"
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
                class="m-1 h-10 w-10 bg-custom-blue2 text-white hover:bg-custom-blue3"
              >
                {{ number }}
              </button>
              <span class="mx-1 text-3xl">...</span>
              <button
                class="m-1 h-10 w-10 bg-custom-blue2 text-white hover:bg-custom-blue3"
              >
                11
              </button>
              <button
                class="m-1 h-10 w-16 bg-custom-blue2 text-white hover:bg-custom-blue3"
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
                class="mt-10 w-96 border-custom-blue2 bg-custom-lightyellow py-4 px-8"
              >
                <span class="font-bold">RAVE REVIEWS</span
                ><button
                  class="float-right bg-custom-blue2 px-5 py-0.5 text-white hover:bg-custom-blue3"
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
          <section>
            <div
              class="group group group relative mt-32 ml-96 mb-96 inline-block"
            >
              <i class="fas fa-bell pb-2 text-2xl"></i>
              <div
                class="absolute -ml-48 hidden w-96 rounded bg-custom-lightcream p-5 group-hover:block"
              >
                <a href="#">
                  <div
                    v-for="(item, i) in 2"
                    :key="i"
                    class="my-4 rounded bg-custom-lightergreen p-2 shadow-md"
                  >
                    <p class="text-xl">
                      " Lorem ipsum dolor sit amet consectetur, adipisicing
                      elit. Dicta, ipsum sit amet consectetur adipisicing elit
                      ... "
                    </p>
                    <img
                      class="float-left mt-3 mr-3 h-16 w-16 rounded-full"
                      src="assets/Lori-Picture.jpg"
                      alt="user-image"
                    />
                    <p class="mt-5 text-xl font-bold">- Lori Webb.</p>
                    <p>DVC Sales Client 2020</p>
                  </div>
                </a>
                <a class="inline-block font-bold" href="#">Read More ...</a>
              </div>
            </div>
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
                  <div class="border-custom-blue2 py-4 px-8 text-custom-blue5">
                    <span class="font-bold">RAVE REVIEWS</span
                    ><button
                      class="float-right bg-custom-blue2 px-5 py-0.5 text-white hover:bg-custom-blue3"
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
