

<template>
  <div class="contenedor" id="contenedor">
      <nav>
        <router-link to="/">Home</router-link> |
        <router-link to="/reglasjuego">Reglas del Juego</router-link> |

        <router-link to="/crear">Crear</router-link> |
        <router-link to="/editar">Editar</router-link> |
        <router-link to="/listar">Listar</router-link>
      </nav>
  
      <router-view/>
  </div>
  
</template>