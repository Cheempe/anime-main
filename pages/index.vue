<template>
  <div class="main-container">
    <div class="header">
      <Navigation />
    </div>
    <div class="topAnime">
      <div class="h-10 w-full">
        <h1 class="text-2xl px-4 text-black font-bold">Популярні тайтли:</h1>
      </div>
      <TopAnime :topAnime="topAnime" />
    </div>
    <div>
      <div class="h-10 w-full">
        <h1 class="text-2xl px-4 text-black font-bold">Current Season:</h1>
      </div>
      <div class="currentSeason flex flex-wrap justify-center">
        <Card
          v-for="anime in response"
          :key="anime.mal_id"
          class="mx-auto"
          @click="goAnime(anime)"
        >
          <template #image>
            <img
              :src="anime.images.webp.image_url"
              height="266"
              :alt="anime.title"
            />
          </template>
          <template #content>
            <h2 :class="{ 'font-bold': true }">{{ anime.title }}</h2>
          </template>
          <template #episode>
            <p>Episodes: {{ anime.episodes }}</p>
          </template>
        </Card>
      </div>
    </div>
  </div>
</template>

<script setup>
const topAnime = ref(null);
const response = ref([]);

onBeforeMount(() => {
  getData();
});
onMounted(() => {
  getData();
});
async function getData() {
  try {
    const { data, error } = await useFetch(
      "https://api.jikan.moe/v4/seasons/now"
    );
    if (data.value) {
      response.value = data.value.data;
    }

    const { data: result } = await useLazyFetch(
      "https://api.jikan.moe/v4/top/anime"
    );
    if (result.value) {
      topAnime.value = result.value.data;
    }
  } catch (error) {
    console.log(error);
  }
}

const router = useRouter();
const goAnime = (anime) => {
  router.push(`/anime/${anime.mal_id}`);
};
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  flex-direction: column;
  gap: 60px;
  padding: 0px 180px;
}
</style>
