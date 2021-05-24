<template>
  <div>
    <nav class="flex items-center justify-between bg-blue-900 p-6">
      <div class="flex items-center flex-shrink-0 mr-6 text-white text-xl">
        Bush Labs
      </div>
    </nav>

    <div class="mt-5 mx-16 px-2">
      <p>
        This is a list of the anime shows I have watched or am currently
        watching. I use
        <a
          href="https://kitsu.io"
          class="text-blue-600 hover:underline hover:text-blue-900"
          >Kitsu</a
        >
        to track my shows and all information below is provided through their
        API.
      </p>
    </div>
    <div class="mt-5 mx-16 px-2">
      <p v-if="$fetchState.pending">Grabbing anime info...</p>
      <p v-else-if="$fetchState.error">Ack! Something went wrong.</p>
      <ul v-else>
        <li v-for="anime in animes" :key="anime.data">
          <h2
            v-if="anime.data.attributes.titles.en"
            class="text-2xl text-gray-800 mb-3"
          >
            {{ anime.data.attributes.titles.en }}
          </h2>
          <h2
            v-else-if="anime.data.attributes.titles"
            class="text-2xl text-gray-800 mb-3"
          >
            {{ anime.data.attributes.titles.en_us }}
          </h2>
          <div class="flex mb-8">
            <img
              :src="anime.data.attributes.posterImage.tiny"
              :alt="anime.data.attributes.canonicalTitle"
              class="mr-4"
            />
            <p>{{ anime.data.attributes.synopsis }}</p>
          </div>
          <!-- <pre>{{ anime }}</pre> -->
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  async fetch() {
    this.animes = await fetch(
      'https://kitsu.io/api/edge/users/1095462/library-entries'
    )
      .then((res) => {
        if (res.ok) {
          return res.json()
        }
        throw new Error(res.status)
      })
      .then((entries) => {
        return Promise.all(
          entries.data.map((entry) => {
            const anime = fetch(entry.relationships.anime.links.related).then(
              (response) => {
                if (response.ok) {
                  return response.json()
                }
                throw new Error(response.status)
              }
            )
            return anime
          })
        )
      })
      .then((data) => {
        return JSON.parse(JSON.stringify(data))
      })
      .catch((error) => {
        console.log('There was a problem', error)
      })
  },
  data() {
    return {
      animes: [],
    }
  },
}
</script>
