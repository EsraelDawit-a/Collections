<template>
  <div class="font-serif">

    <div class="border-4 head h-[75px] flex items-center ">
      <div class="header ml-5 py-5 ">
        <div v-if="!sidebar_opend" class="menue cursor-pointer font-bold text-xl " @click="OpenSideBar">
          <div>Menue</div>
          <div class="text-sm h-2 w-full bg-black">
            {{getGlasses}}
          </div>
        </div>
        <div v-else class="menue cursor-pointer font-bold text-xl " @click="OpenSideBar">X</div>

      </div>
    </div>

    <div :class="`${sidebar_opend ?'opendSide1 ':'sidebar'}`" @mouseleave="sidebar_opend = false">
      <div class="spect ">
        <div class=" d-men cursor-pointer group" @mouseover="spect_hovered= true" @mouseleave="spect_hovered = false">
          <div class="flex hover:bg-black hover:text-white text-lg font-bold px-5 py-5 justify-between">
            SPECTACLES
            <div>></div>

          </div>

          <div v-if="spect_hovered" class="opacity-0 cursor-pointer group-hover:opacity-100 sub_menue">
            <div class=" d-men ">
              <div @click="Change_Spect_to_Men"
                class="flex hover:bg-black hover:text-white text-lg font-bold px-5 py-5 justify-between">
                MEN
                <div>></div>
              </div>
            </div>

            <div class=" d-men ">
              <div @click="Change_Spect_to_Women"
                class="flex hover:bg-black hover:text-white text-lg font-bold px-5 py-5 justify-between">
                WOMEN
                <div>></div>
              </div>
            </div>
          </div>


        </div>
        <div class="d-men group cursor-pointer" @mouseover="glass_hovered= true" @mouseleave="glass_hovered = false">
          <div class="flex hover:bg-black hover:text-white text-lg font-bold  px-5 py-5 justify-between">
            SUNGLASES
            <div>></div>
          </div>

          <div v-if="glass_hovered" class="opacity-0 group-hover:opacity-100 sub_menue">
            <div class=" d-men ">
              <div class="flex hover:bg-black hover:text-white text-lg font-bold px-5 py-5 justify-between">
                MEN
                <div>></div>
              </div>
            </div>

            <div class=" d-men ">
              <div class="flex hover:bg-black hover:text-white text-lg font-bold px-5 py-5 justify-between">
                WOMEN
                <div>></div>
              </div>
            </div>
          </div>
        </div>
        <div class="d-men cursor-pointer ">
          <div class="flex hover:bg-black cursor-pointer hover:text-white text-lg font-bold  px-5 py-5 justify-between">
            HOME TRY ON

          </div>
        </div>
        <div class="d-men cursor-pointer ">
          <div class="flex cursor-pointer hover:bg-black hover:text-white text-lg font-bold  px-5 py-5 justify-between">
            PAIR FOR PAIR

          </div>
        </div>

      </div>

    </div>


    <div class="px-2 spectacles  grid gap-4 grid-cols-3 ">
      <div class="bor flex justify-center">
        <div class="px-20 "></div>
      </div>


      <div class="bor flex justify-center px-10">
        <div class=" py-5 font-bold text-2xl uppercase ">SPECTACLES {{default_page}}</div>

      </div>
      <div class="flex font-bold">
        <div class="bor">
          <div class=" px-10 pt-5 relative cursor-pointer" @click="ColourMenue">COLOR 
           
          </div>


        </div>

        <div class="bor">
          <div class="px-10 pt-5 cursor-pointer" @click="ShapeMenue"> SHAPE</div>
        </div>
      </div>
    </div>

    <!-- Fiter DropDowns  -->
    <div v-if="color_menue" class="color-options px-10 py-6">
      <h1 class="mb-3">Colors</h1>
      <div class="flex text-serif text-lg">
        <label class="container">
          <input v-model="colors.black" type="checkbox">
          <span class="checkmark"></span>
          black
        </label>
        <label class="container">
          <input v-model="colors.tortoise" type="checkbox">
          tortoise
        </label>
        <label class="container">
          <input v-model="colors.coloured" type="checkbox">
          <span class="checkmark"></span>
          colored
        </label>
        <label class="container">
          <input v-model="colors.crystal" type="checkbox">
          <span class="checkmark"></span>
          crystal
        </label>
        <label class="container">
          <input v-model="colors.dark" type="checkbox">
          <span class="checkmark"></span>
          dark
        </label>
        <label class="container">
          <input v-model="colors.bright" type="checkbox">
          <span class="checkmark"></span>
          bright
        </label>
      </div>

    </div>

    <div v-if="shape_menue" class=" shape color-options px-10 py-6">
      <h1 class="mb-3">Shape</h1>
      <div class="flex text-serif text-lg">

        <label class="container">
          <input v-model="shapes.square" type="checkbox">
          square
        </label>
        <label class="container">
          <input v-model="shapes.rectangle" type="checkbox">
          <span class="checkmark"></span>
          rectangle
        </label>
        <label class="container">
          <input v-model="shapes.round" type="checkbox">
          <span class="checkmark"></span>
          round
        </label>
        <label class="container">
          <input v-model="shapes.cateye" type="checkbox">
          <span class="checkmark"></span>
          cat-eye
        </label>

      </div>

    </div>

    <!-- List Cards -->

    <div v-if="!loading" class=" grid  grid-cols-3 grid-rows-3 ">
      <!-- ... -->
      <!-- <div v-if="filterd_glases.length > 0">
        <div v-for="glass in filterd_glases.glasses" :key="glass.id" class="w-[33%] cards border-black h-[500px] bg-indigo-200"
        :style="{
          'background-image': `url(${glass.glass_variants[0].media[0].url})`,
           width:'100%'
        }">

        <div class="flex justify-center  text-2xl pt-5">{{glass.name}}</div>
        <img :src="glass.glass_variants[0].media[0].url" alt="">


      </div>
      </div> -->


      <div v-for="glass in filterd_glases.glasses" :key="glass.id"
        class="w-[33%] cards border-black h-[500px] bg-indigo-200" :style="{
          'background-image': `url(${glass.glass_variants[0].media[0].url})`,
           width:'100%'
        }">

        <div class="flex justify-center  text-2xl pt-5">{{glass.name}}</div>
        <img :src="glass.glass_variants[0].media[0].url" alt="">


      </div> 
      

    </div>

    <div v-else class=" grid  grid-cols-3 gap-4 grid-rows-3 ">
      <!-- ... -->
      <SkeletonLoader/>
      <SkeletonLoader/>
      <SkeletonLoader/>
      <SkeletonLoader/>
      <SkeletonLoader/>
      <SkeletonLoader/>
     

    </div>



  </div>

</template>

<script>
import axios from "axios";
import SkeletonLoader from "../components/SkeletonLoader.vue";

export default {
    // Properties returned from data() become reactive state
    // and will be exposed on `this`.
    data() {
        return {
            glasses: {},
            filterd_glases: {},
            default_page: "women",
            loading: false,
            color_menue: false,
            shape_menue: false,
            sidebar_opend: false,
            glass_hovered: false,
            spect_hovered: false,
            // Filter Variants
            colors: {
                black: false,
                tortoise: false,
                coloured: false,
                crystal: false,
                dark: false,
                bright: false
            },
            shapes: {
                "square": false,
                "rectangle": false,
                "round": false,
                "cateye": false
            }
        };
    },
    computed: {
        getGlasses() {
            this.loading = true;
            let url = `https://api.bloobloom.com/user/v1/sales_channels/website/collections/spectacles-${this.default_page}/glasses?sort[type]=collection_relations_position&sort[order]=asc&filters[lens_variant_prescriptions][]=fashion&filters[lens_variant_types][]=classic&page[limit]=12&page[number]=1&filters[frame_variant_home_trial_available]=false`;
            url = url + (this.colors.black == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=black" : "") + (this.colors.tortoise == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=tortoise" : "")
                + (this.colors.coloured == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=coloured" : "")
                + (this.colors.crystal == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=crystal" : "")
                + (this.colors.dark == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=dark" : "")
                + (this.colors.bright == true ? "&filters[glass_variant_frame_variant_colour_tag_configuration_names][]=bright" : "")
                + (this.shapes.square == true ? "&filters[glass_variant_frame_variant_frame_tag_configuration_names][]=square" : "")
                + (this.shapes.rectangle == true ? "&filters[glass_variant_frame_variant_frame_tag_configuration_names][]=rectangle" : "")
                + (this.shapes.round == true ? "&filters[glass_variant_frame_variant_frame_tag_configuration_names][]=round" : "")
                + (this.shapes.cateye == true ? "&filters[glass_variant_frame_variant_frame_tag_configuration_names][]=cat-eye" : "");
            axios
                .get(url)
                .then((response) => {
                console.log("filterd" + response.data);
                this.filterd_glases = response.data;
                this.loading = false;
            })
                .catch((err) => {
                console.log(err);
                this.loading = false;
            });
        }
    },
    // Methods are functions that mutate state and trigger updates.
    // They can be bound as event listeners in templates.
    methods: {
        LoadGlasses() {
            const url = "https://api.bloobloom.com/user/v1/sales_channels/website/collections/spectacles-women/glasses?width=960&sort[type]=collection_relations_position&sort[order]=asc&filters[lens_variant_prescriptions][]=fashion&filters[lens_variant_types][]=classic&page[limit]=12&page[number]=2&filters[frame_variant_home_trial_available]=false";
            this.loading = true;
            axios
                .get(url)
                .then((response) => {
                console.log(response.data);
                this.glasses = response.data;
                this.loading = false;
            })
                .catch((err) => {
                console.log(err);
                this.loading = false;
            });
        },
        ColourMenue() {
            this.color_menue = !this.color_menue;
        },
        ShapeMenue() {
            this.shape_menue = !this.shape_menue;
        },
        OpenSideBar() {
            this.sidebar_opend = !this.sidebar_opend;
        },
        Change_Spect_to_Men() {
            this.default_page = "men";
            this.sidebar_opend = false;
            this.spect_hovered = false;
        },
        Change_Spect_to_Women() {
            this.default_page = "women";
            this.sidebar_opend = false;
            this.spect_hovered = false;
        }
    },
    components: { SkeletonLoader }
};
</script>

<style scoped>
.sidebar {
  position: fixed;
  height: 100%;
  width: 300px;
  left: -1000px;
  background-color: #fff;
  transition: all 0.7s;
}

.opendSide1 {
  position: fixed;
  height: 100%;
  width: 300px;
  left: 0px !important;
  background-color: #fff;
  transition: all 0.7s;

}

.d-men {
  border-bottom: 1px solid rgb(102, 99, 99);
  font-family: serif;
}

.sub_menue {
  position: fixed;
  height: 100%;
  width: 300px;
  top: 70px;
  left: 300px;
  background-color: #fff;
  transition: all 0.7s;
}



.color-options {
  background-color: rgb(239, 245, 245);
  top: 0px;
  width: 100%;
}

:root {
  --form-control-color: rebeccapurple;
  --form-control-disabled: #959495;
}


.color-options h1 {
  font-size: 25px;
}

.shape {
  border-top: 1px solid black;
  transition: 0.3s ease;
}

.form-control--disabled {
  color: var(--form-control-disabled);
  cursor: not-allowed;
}

input[type="checkbox"] {
  /* Add if not using autoprefixer */
  -webkit-appearance: none;
  /* Remove most all native input styles */
  appearance: none;
  /* For iOS < 15 */
  background-color: var(--form-background);
  /* Not removed via appearance */
  margin: 0;

  font: inherit;
  color: currentColor;
  width: 1.15em;
  height: 1.15em;
  border: 0.15em solid currentColor;
  border-radius: 0.15em;
  transform: translateY(-0.075em);

  display: grid;
  place-content: center;
}

input[type="checkbox"]::before {
  content: "";
  width: 0.65em;
  height: 0.65em;
  clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
  transform: scale(0);
  transform-origin: bottom left;
  transition: 120ms transform ease-in-out;
  box-shadow: inset 1em 1em rebeccapurple;
  /* Windows High Contrast Mode */
  background-color: CanvasText;
}

input[type="checkbox"]:checked::before {
  transform: scale(1);
}

input[type="checkbox"]:focus {
  outline: max(2px, 0.15em) solid currentColor;
  outline-offset: max(2px, 0.15em);
}

input[type="checkbox"]:disabled {
  --form-control-color: var(--form-control-disabled);

  color: var(--form-control-disabled);
  cursor: not-allowed;
}



.head {
  border: black 1px solid;
}

.bor {
  border-right: black 1px solid;
}

.spectacles {
  border: black 1px solid !important;
}

.cards {
  border: 1px solid black;
  border-right: 0px;
  border-bottom: 0px;
  font-family: "Courier New", Courier, monospace;
}
</style>
