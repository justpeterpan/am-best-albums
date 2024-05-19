<script lang="ts" setup>
const { data: albums } = useFetch('/a')
useHead({
  bodyAttrs: {
    class:
      'bg-amber-50 h-screen m-4 pb-4 flex flex-row justify-center text-neutral-600',
  },
  title: 'AM 100 Best Albums',
  meta: [{ charset: 'utf-8' }],
  htmlAttrs: { lang: 'en' },
  link: [
    { rel: 'icon', type: 'image/png', href: '/favicon.png' },
    { rel: 'apple-touch-icon', type: 'image/png', href: '/favicon.png' },
  ],
})
</script>

<template>
  <div class="flex flex-col gap-4 divide-y divide-dotted divide-black pb-8">
    <div
      v-for="album of albums"
      :key="album.title"
      class="flex flex-col sm:flex-row pt-4 gap-4 sm:justify-between"
    >
      <NuxtImg
        fit="cover"
        :src="album.cover"
        :alt="album.title + 'cover'"
        loading="lazy"
        class="size-24 shadow-md rounded-sm"
      />
      <div class="flex flex-col sm:justify-center sm:items-end sm:text-right">
        <h2 class="font-extrabold text-2xl">{{ album.artist }}</h2>
        <NuxtLink
          :to="album.url"
          class="bg-amber-200 max-w-fit font-thin text-xl italic hover:underline decoration-dotted decoration-neutral-600"
        >
          {{ album.title }}
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
