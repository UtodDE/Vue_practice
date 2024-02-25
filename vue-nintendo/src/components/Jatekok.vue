<template>
    <div class="nintendo">
      <h1 class="nintendo-title">Nintendo Switch Játékok</h1>
      <ul class="game-list">
        <li v-for="game in games" :key="game.id" class="game-item">
          <router-link :to="{ name: 'jatek-adatok', params: { id: game.id }}" class="game-link">
            <div>
              <img :src="getThumbnailUrl(game.id)" alt="Game Thumbnail" class="game-thumbnail" />
              <h2 class="game-name">{{ game.cim }}</h2>
            </div>
          </router-link>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        games: [
          { id: 1, cim: 'Mario Kart 8 Deluxe', eladas:'57.01 millió', kiadas: '2017 Április 28', mufaj: 'Kart racing' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 2, cim: 'Animal Crossing: New Horizons', eladas:'43.38 millió', kiadas: '2020 Március 20', mufaj: 'Social simulation' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 3, cim: 'Super Smash Bros. Ultimate', eladas:'32.44 millió', kiadas: '2018 December 7', mufaj: 'Fighting' , fejleszto: 'Bandai Namco Studios, Sora Ltd.', kiado: 'Nintendo'},
          { id: 4, cim: 'The Legend of Zelda: Breath of the Wild', eladas:'31.15 millió', kiadas: '2017 Március 3', mufaj: 'Action-adventure' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 5, cim: 'Super Mario Odyssey', eladas:'26.95 millió', kiadas: '2017 Október 27', mufaj: 'Platformer' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 6, cim: 'Pokémon Sword and Shield', eladas:'26.02 millió', kiadas: '2019 November 15', mufaj: 'Role-playing' , fejleszto: 'Game Freak', kiado: 'The Pokémon Company, Nintendo'},
          { id: 7, cim: 'Pokémon Scarlet and Violet', eladas:'23.23 millió', kiadas: '2022 November 18', mufaj: 'Role-playing' , fejleszto: 'Game Freak', kiado: 'The Pokémon Company, Nintendo'},
          { id: 8, cim: 'Super Mario Party', eladas:'19.66 millió', kiadas: '2018 Október 5', mufaj: 'Party' , fejleszto: 'NDcube', kiado: 'Nintendo'},
          { id: 9, cim: 'The Legend of Zelda: Tears of the Kingdom', eladas:'19.50 millió', kiadas: '2023 Május 12', mufaj: 'Action-adventure' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 10, cim: 'New Super Mario Bros. U Deluxe', eladas:'16.70 millió', kiadas: '2019 Január 11', mufaj: 'Platformer' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          { id: 11, cim: 'Ring Fit Adventure', eladas:'15.38 millió', kiadas: '2019 Október 18', mufaj: 'Role-playing' , fejleszto: 'Nintendo EPD', kiado: 'Nintendo'},
          ],
    };
  },
  created() {
    const storedGames = sessionStorage.getItem('jatek-adatok');
    if (!storedGames) {
      sessionStorage.setItem('jatek-adatok', JSON.stringify(this.games));
    }
  },
  methods: {
    getThumbnailUrl(gameId) {
      return `/images/game${gameId}.jpg`;
    },
  },
};
</script>

<style scoped>

.nintendo {
  text-align: center;
  padding: 20px;
}

.nintendo-title {
  font-size: 24px;
  color: #e60012;
}

.game-list {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.game-item {
  background-color: #f7f7f7;
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.game-link {
  text-decoration: none;
}
.game-name {
  color: #ff3d00;
}
.router-link-active .game-name {
  color: #d21951;
}

.game-item:hover {
  background-color: #e60012;
  color: white;
}
.game-thumbnail {
  width: 100px;
  height: auto;
  margin-bottom: 10px;
}
</style>