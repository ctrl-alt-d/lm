# **Pràctica: Utilitzant la PokéAPI amb JavaScript**

En aquesta pràctica aprendrem a consumir dades de la **PokéAPI** per mostrar informació sobre Pokémon a la nostra aplicació web.

---

## **Objectius**
1. Fer servir `fetch` per consumir una API REST.
2. Mostrar dades del JSON obtingut a la pàgina web.
3. Practicar amb manipulació del DOM.

---

## **Requisits previs**
- Coneixements bàsics d'HTML, CSS i JavaScript.
- Familiaritat amb promeses i el mètode `fetch`.

---

## **Passos**

### **1. Configuració inicial**

1. Crea un fitxer anomenat `index.html` amb el següent contingut:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PokéAPI Demo</title>
</head>
<body>
  <h1>Pokédex</h1>
  <div>
    <input type="text" id="pokemon-name" placeholder="Escriu el nom del Pokémon">
    <button id="search-btn">Cerca Pokémon</button>
  </div>
  <div id="pokemon-info"></div>

  <script src="script.js"></script>
</body>
</html>
```

---

### **2. Estructura del JavaScript**

1. Crea un fitxer anomenat `script.js` i afegeix el següent codi:

```javascript
document.getElementById('search-btn').addEventListener('click', () => {
  const pokemonName = document.getElementById('pokemon-name').value.toLowerCase();
  fetchPokemonData(pokemonName);
});

async function fetchPokemonData(pokemonName) {
  const pokemonInfoDiv = document.getElementById('pokemon-info');
  pokemonInfoDiv.innerHTML = `<p>Loading ...</p>`;

  try {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`);
    if (!response.ok) {
      throw new Error('Pokémon no trobat!');
    }
    const data = await response.json();
    displayPokemonData(data);
  } catch (error) {
    document.getElementById('pokemon-info').innerHTML = `<p style="color: red;">${error.message}</p>`;
  }
}

function displayPokemonData(data) {
  const pokemonInfo = `
    <h2>${data.name} (#${data.id})</h2>
    <img src="${data.sprites.front_default}" alt="${data.name}">
    <p><strong>Tipus:</strong> ${data.types.map(type => type.type.name).join(', ')}</p>
    <p><strong>Pes:</strong> ${data.weight / 10} kg</p>
    <p><strong>Alçada:</strong> ${data.height / 10} m</p>
  `;
  document.getElementById('pokemon-info').innerHTML = pokemonInfo;
}
```

---

### **3. Documenta el codi javascript**

1. Posa comentaris al codi JavaScript tot explicant que fa cada línia de codi.
2. Fes un botó 'Esborrar dades'  que esborri les dades carregades.

--

### **4. Prova la teva aplicació**

1. Obre el fitxer `index.html` en un navegador.
2. Escriu el nom d'un Pokémon (per exemple, "pikachu") al camp de text.
3. Fes clic al botó "Cerca Pokémon".
4. Observa com es mostren les dades del Pokémon a la pantalla!

---

## **Extensió (opcional)**

Prova d'afegir funcionalitats addicionals:
- Mostra també les estadístiques del Pokémon (HP, atac, defensa...).
- Afegeix una barra de càrrega mentre es consulta la informació.

---

Ara ja tens una Pokédex funcional utilitzant la PokéAPI! 🎉
