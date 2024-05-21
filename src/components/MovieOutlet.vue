<template>
  <div class="movie-outlet">
    <h4>Popular Collection</h4>
    <div v-if="errorMsg" class="errorNotice">{{ errorMsg }}</div>
    <div v-else class="movie-container">
      <div class="card" v-for="movie in listedMoviesToDisplay" :key="movie.id">
        <div v-if="movie.toggle" class="movie-overview">
          <p class="movie-title">{{ movie.title }}</p>
          <p class="overview-text">{{ movie.overview }}</p>
        </div>
        <img
          v-else
          :src="'https://image.tmdb.org/t/p/w200' + movie.poster_path"
          alt="poster"
          class="image-card"
        />
        <div class="description">
          <div class="year-and-movieType">
            <button @click="toggleBtn(movie)" class="overview">overview</button>
            <p>{{ new Date(movie.release_date).getFullYear() }}</p>
          </div>
        </div>
      </div>
    </div>
    <button v-if="showBtn" @click="moreMovieSlide" class="more-item">More Movies</button>
  </div>
</template>
<script setup>
import axios from 'axios'
import { computed, ref, onMounted } from 'vue'

const apiKey = '25814457dd63d4a85b7862eb51b3a95a'
const apiUrl = 'https://api.themoviedb.org/3'

let grabMovies = []
let movieCount = 8

const listedMoviesToDisplay = ref(grabMovies.slice(0, movieCount))
const otherMovies = ref(grabMovies.slice(movieCount))
const showBtn = computed(() => otherMovies.value.length > 0)

const toggleBtn = (movie) => {
  movie.toggle = !movie.toggle
}

const moreMovieSlide = () => {
  movieCount += 8
}

const fetchData = async () => {
  try {
    const res = await axios.get(`${apiUrl}/movie/popular?api_key=${apiKey}`)
    grabMovies = res.data.results
    listedMoviesToDisplay.value = grabMovies.slice(0, movieCount)
    otherMovies.value = grabMovies.slice(movieCount)
  } catch (error) {
    console.error('Bad request: ', error.message)
  }
}

onMounted(() => {
  fetchData()
})
</script>

<style>
.errorNotice {
  color: #fff;
  font-size: 31px;
  text-align: center;
}

.movie-overview {
  padding: 9px;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}

.movie-overview .movie-title:hover {
  color: #fff;
}

.overview {
  cursor: pointer;
  padding: 4px;
  background: red;
  outline: none;
  border: none;
  border-radius: 5px;
  color: #fff;
}

.overview:hover {
  opacity: 0.8;
}
.movie-outlet {
  background: var(--secondary-color);
  display: flex;
  padding: 2rem 0;
  align-items: center;
  flex-direction: column;
  gap: 60px;
}

.movie-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 40px;
  padding: 1rem 4rem;
}

.movie-outlet h4 {
  font-family: var(--header);
  font-size: 32px;
  color: #fff;
  text-shadow: 0 2px 9px red;
}

.movie-container .card {
  background: rgb(235, 229, 229);
  border-radius: 14px;
  position: relative;
}

.card:hover {
  background: var(--primary-color);
}

.more-item:hover {
  background: red;
  transition: 0.3s ease-in;
  color: #fff;
  transform: translateY(-8px);
}

.more-item {
  padding: 14px;
  border-radius: 13px;
  background: #fff;
  border: none;
  outline: none;
  font-weight: 600;
  font-size: 1rem;
  color: red;
  box-shadow: 0 2px 9px red;
  cursor: pointer;
}

.movie-title,
.overview-text {
  padding-bottom: 5px;
  border-bottom: 2px solid var(--secondary-color);
  font-weight: bolder;
  color: red;
  text-align: center;
}

.overview-text {
  height: 315px;
  overflow: auto;
  scroll-behavior: smooth;

  &::-webkit-scrollbar {
    width: 5px;
  }

  &::-webkit-scrollbar-track {
    background: var(--primary-color);
  }

  &::-webkit-scrollbar-thumb {
    border-radius: 12px;
    border: 2px solid red;
  }
}

.year-and-movieType {
  display: flex;
  justify-content: space-between;
}

.card .description {
  justify-content: space-between;
  align-items: center;
  position: absolute;
  background: var(--primary-color);
  width: 100%;
  padding: 13px;
  bottom: 0;
  left: 0;
  right: 0;
}
.card .description p {
  color: #fff;
  font-weight: 800;
}

.card .image-card {
  width: 100%;
  /* height: auto; */
  height: 400px;
  border-radius: 12px;
}
</style>
