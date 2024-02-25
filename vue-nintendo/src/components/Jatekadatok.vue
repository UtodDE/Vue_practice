<template>
    <div class="game-details">
      <h1 class="nintendo-title">Adatok</h1>
      <div class="game-details-header">
        <img :src="getImageUrl(selectedGame.id)" alt="Game Image" class="game-image" />
        <table v-if="selectedGame" class="game-table">
          <tr>
            <th>Cím</th>
            <th>Eladott példányszám</th>
            <th>Kiadás éve</th>
            <th>Műfaj</th>
            <th>Fejlesztő</th>
            <th>Kiadó</th>
          </tr>
          <tr>
            <td>{{ selectedGame.cim }}</td>
            <td>{{ selectedGame.eladas }}</td>
            <td>{{ selectedGame.kiadas }}</td>
            <td>{{ selectedGame.mufaj }}</td>
            <td>{{ selectedGame.fejleszto }}</td>
            <td>{{ selectedGame.kiado }}</td>
          </tr>
        </table>
      </div>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        selectedGame: null,
        gameImages: {
        1: 'game1.jpg',
        2: 'game2.jpg',
        3: 'game3.jpg',
        4: 'game4.jpg',
        5: 'game5.jpg',
        6: 'game6.jpg',
        7: 'game7.jpg',
        8: 'game8.jpg',
        9: 'game9.jpg',
        10: 'game10.jpg',
        11: 'game11.jpg',
        }
      };
    },
    created() {
      const storedGames = sessionStorage.getItem('jatek-adatok');
      if (storedGames) {
        const games = JSON.parse(storedGames);
        const gameId = this.$route.params.id;
        this.selectedGame = games.find(game => game.id == gameId);
      }
    },
    methods: {
    getImageUrl(gameId) {
      return `/images/${this.gameImages[gameId]}`;
      },
    },
  }
  
</script>

<style scoped>
.game-details {
  text-align: center;
  padding: 20px;
}

.nintendo-title {
  font-size: 24px;
  color: #e60012;
}

.game-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

.game-table th, .game-table td {
  border: 1px solid #e60012;
  padding: 10px;
}

.game-table th {
  background-color: #f7f7f7;
}

.game-table td {
  background-color: #fff;
}

.game-table td:first-child {
  font-weight: bold;
}
.game-details-header {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.game-image {
  max-width: 300px;
  max-height: 300px;
  margin-right: 20px;
  border-radius: 5px;
}

</style>