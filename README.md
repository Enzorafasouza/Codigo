<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catálogo de Filmes</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Catálogo de Filmes</h1>
    <input type="text" id="search" placeholder="Pesquise um filme...">
  </header>
  <main id="movies">
    <!-- Os filmes serão exibidos aqui -->
  </main>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #222;
  color: #fff;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  background-color: #444;
}

input {
  padding: 10px;
  border: none;
  border-radius: 5px;
}

#movies {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  padding: 20px;
}

.movie {
  background-color: #333;
  padding: 10px;
  border-radius: 10px;
  text-align: center;
}
const movies = [
  { title: "O Poderoso Chefão", year: 1972 },
  { title: "Vingadores: Ultimato", year: 2019 },
  { title: "Interstellar", year: 2014 },
];

const movieContainer = document.getElementById("movies");

function displayMovies() {
  movieContainer.innerHTML = "";
  movies.forEach((movie) => {
    const movieElement = document.createElement("div");
    movieElement.classList.add("movie");
    movieElement.innerHTML = `
      <h2>${movie.title}</h2>
      <p>${movie.year}</p>
    `;
    movieContainer.appendChild(movieElement);
  });
}

document.getElementById("search").addEventListener("input", (e) => {
  const searchValue = e.target.value.toLowerCase();
  const filteredMovies = movies.filter((movie) =>
    movie.title.toLowerCase().includes(searchValue)
  );
  displayMovies(filteredMovies);
});

displayMovies();
