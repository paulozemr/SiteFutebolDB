<template>
  <header class="menu-superior">
    <div class="menu-esquerdo">
      <span>
        <RouterLink class="botao" to="/">Home</RouterLink>
      </span>
      <span>|</span>
      <span>
        <RouterLink class="botao" to="/times">Times</RouterLink>
      </span>
      <span>|</span>
      <span>
        <RouterLink class="botao" to="/jogadores">Jogadores</RouterLink>
      </span>
    </div>
    <div class="menu-direito">
      <span>Sair</span>
    </div>
  </header>
</template>

<style>
header span {
  padding: 0 20px;
}

.menu-superior {
  justify-content: space-between;
  text-decoration: none;
  color: white;
}

.menu-esquerdo .botao {
  text-decoration: none;
  color: white;
}
</style>
