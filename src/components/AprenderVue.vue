<template>
  <div class="aprenderVue">
    <!-- practica ternaria y traer dato de abajo -->
    <p>{{ pokemonName == "pikachu" ? "es pikachu" : "No es pikachu" }}</p>
    <!-- práctica de mostrar dato de abajo -->
    <p>mi pokemon favorito es: {{ pokemonName }}</p>
    <!-- práctica de v-if -->
    <p v-if="pokemonName == 'pikachu'">hola</p>
    <!-- práctica de v-if -->
    <p v-else>pos aparece el else</p>
    <ul>
      <!-- práctica de v-for -->
      <li v-for="(pokemon, index) in listadoPokemon" :key="index">
        <!-- mostrar indice apartir de 1 -->
        {{ index + 1 }}-{{ pokemon }}
      </li>
    </ul>
    <div>
      <!-- práctica de input y botones con @click-->
      <input v-model="nombrePokemonAgregar" placeholder="Agregar Pokemon" />
      <button @click="agregarPokkemon(nombrePokemonAgregar)">
        Agregar Pokemon
      </button>
    </div>
    <div>
      <input v-model="nombrePokemonEliminar" placeholder="Eliminar Pokemon" />
      <button @click="eliminarPokkemon(nombrePokemonEliminar)">
        Eliminar Pokemon
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class AprenderVue extends Vue {
  // private pokemons = this.devuelvePokemons();
  private listaPokemon = ["pikachu", "bulbasur", "pilliotto"];
  private nombrePokemonEliminar = "";
  private nombrePokemonAgregar = "";

  //  get pokemonName() {
  //     const nombrePokemons = this.devuelvePokemons();
  // //   //const nombrePokemons = ["pikachu", "bulbasur"];
  //    console.log("nombre pokemon: ", nombrePokemons[0]);
  //    return nombrePokemons[0];
  //  }
  get pokemonName() {
    return "pikachu";
  }
  // get agregarPokemon() {
  //   return this.agregarPokkemon("poncho");
  // }

  get listadoPokemon() {
    return this.listaPokemon;
  }

  private agregarPokkemon(nombrePokemonAgregar: string) {
    //comprobar si ha introducido nombre de pokemon o no, resolver con ternaria para prácticar
    nombrePokemonAgregar !== "" || undefined
      ? this.listadoPokemon.push(nombrePokemonAgregar)
      : alert("No ha introducido el nombre de ningún pokemon");
  }

  private limpiadorCampos(contenidoCampo: string) {
    contenidoCampo = "";
  }

  private eliminarPokkemon(nombrePokemonEliminar: string) {
    nombrePokemonEliminar !== "" || undefined
      ? (this.listaPokemon = this.listadoPokemon.filter(
          (e) => e !== nombrePokemonEliminar
        ))
      : alert("No ha introducido el nombre de ningún pokemon");
    nombrePokemonEliminar = "";
  }
  // private async devuelvePokemons() {
  //   try {
  //     const respuesta = await fetch("https://pokeapi.co/api/v2/pokemon");
  //     const data = await respuesta.json();

  //     const ListadoNombrePokemon = data.results.map(
  //       (pokemon: any) => pokemon.name
  //     );
  //     //filtrado con "filter"
  //     const nombresFiltrados = ListadoNombrePokemon.filter(
  //       (pokemon: string) => pokemon === "charmander"
  //     );
  //     //conseguir mismo array sin bulbasaur
  //     const listadoSinBulbasaur = ListadoNombrePokemon.filter(
  //       (pokemon: string) => pokemon !== "bulbasaur"
  //     );
  //     console.log("nombre de pokemons", ListadoNombrePokemon);
  //     console.log("nombre de pokemon filtrado", nombresFiltrados);
  //     console.log("listado sin bulbasaur", listadoSinBulbasaur);
  //     return ListadoNombrePokemon;
  //   } catch (error) {
  //     console.log("error");
  //   }
  // }
}
</script>

<style scoped></style>
