<template>
  <div>
    <h1 class="text-center font-bold text-2xl my-10">Conditional image transformations in Nuxt.Js</h1>
    <div v-for="(image,key) in images" :key="key" class="m-10">
      <h2 class="font-semibold text-lg mt-5">{{image.credit}}</h2>
      <div class="grid grid-cols-4">
        <div class="p-3 flex flex-col justify-end">
          <cld-image :publicId="image.publicId">
            <cld-transformation height="500" crop="fit" />
            <cld-transformation if="iw_gt_4300" />
            <cld-transformation effect="cartoonify" />
            <cld-transformation if="end" />
          </cld-image>
          <p class="mt-5 text-center text-sm">Cartoonify if inital width is greater than 4300px</p>
        </div>
        <div class="p-3 flex flex-col justify-end">
          <cld-image :publicId="image.publicId">
            <cld-transformation height="500" crop="fit" />
            <cld-transformation if="ih_gt_3000" />
            <cld-transformation effect="oil_paint" />
            <cld-transformation if="end" />
          </cld-image>
          <p class="mt-5 text-center text-sm">Oil paint if inital height is greater than 3000px</p>
        </div>
        <div class="p-3 flex flex-col justify-end">
          <cld-image :publicId="image.publicId">
            <cld-transformation height="500" crop="fit" />
            <cld-transformation if="ar_lt_1.0" />
            <cld-transformation background="auto" height="800" width="400" crop="pad" />
            <cld-transformation if="else" />
            <cld-transformation background="auto" height="400" width="800" crop="pad" />
            <cld-transformation if="end" />
          </cld-image>
          <p class="mt-5 text-center text-sm">Pad horizontally or vertically if aspect ratio is less or greater than 1.0</p>
        </div>
        <div class="p-3 flex flex-col justify-end">
          <cld-image :publicId="image.publicId">
            <cld-transformation height="500" crop="fit" />
            <cld-transformation if="fc_gte_1" />
            <cld-transformation gravity="face" height="400" width="400" crop="thumb" />
            <cld-transformation effect="vignette" />
            <cld-transformation if="end" />
          </cld-image>
          <p class="mt-5 text-center text-sm">If face is detected, crop around it and apply vignette</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      images: [
        {
          publicId: "nuxtjs-conditional-image-transformations/pexels-micheilecom-_-visual-stories-11573079.jpg",
          credit:"Photo by micheile.com || visual stories from Pexels"
        },
        {
          publicId: "nuxtjs-conditional-image-transformations/pexels-anastasiia-goncharova-11659832.jpg",
          credit:"Photo by Danil Lysov from Pexels"
        },
        {
          publicId: "nuxtjs-conditional-image-transformations/pexels-megan-ruth-11494641.jpg",
          credit:"Photo by Anastasiia Goncharova from Pexels"
        },
        {
          publicId: "nuxtjs-conditional-image-transformations/pexels-danil-lysov-11741441.jpg",
          credit:"Photo by Anastasiia Goncharova from Pexels"
        },
      ]
    }
  }
}
</script>
