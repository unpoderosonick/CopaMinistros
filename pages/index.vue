<template>
  <div class="min-h-screen p-8 bg-gray-100 text-[#333333]">
    <h1 class="mb-10 text-4xl font-bold text-center">Copa Ministros del Dota</h1>
    <!--  Puntos acumulados -->
    <div>
      <h2 class="mb-5 text-2xl font-bold">Puntos Acumulados</h2>
    </div>
    <div class="">
      <div class="flex items-center justify-center ">
        <div
          class="p-5 transition duration-300 bg-white border-t-4 border-red-400 rounded-lg shadow-sm lg:flex lg:w-2/3 hover:border-red-500 hover:shadow-md">
          <div>
          </div>
          <div class="lg:p-5 lg:w-1/2">

            <div v-for="(player, index) in listBestPlayers" :key="acumulado" class="p-2">
              <div class="flex ">
                <div class="w-1/2 text-left lg:w-2/4 ">
                  <p class="text-base ">{{ index + 1 }}. {{ player.participante }}</p>
                </div>
                <div class="w-1/4 text-right">
                  <p class="">{{ player.points }} pts</p>
                </div>
                <div class="w-1/4 text-center">
                  <p class="text-center">{{ player.won + " - " + player.lost + " - " + player.total }} </p>
                </div>
              </div>
            </div>
          </div>

          <div class="flex justify-center lg:w-1/2">
            <div class="w-auto lg:pr-0">
              <div class="flex justify-center pt-2 pb-2">
                <img src="https://fineproxy.org/wp-content/uploads/2023/08/Dota-2-logo.png">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--  FIN acumulados -->

    <!-- Fase de Grupos en Tarjetas -->
    <h2 class="pt-5 mb-5 text-2xl font-bold">Fase de Grupos</h2>
    <div class="grid grid-cols-1 gap-6 mb-12 md:grid-cols-2 lg:grid-cols-4 ">
      <div v-for="grupo in grupos" :key="grupo.nombre"
        class="overflow-hidden transition duration-300 bg-white border-t-4 border-teal-400 rounded-lg shadow-sm hover:shadow-md">
        <div class="p-5">
          <h3 class="mb-4 text-xl font-semibold">{{ grupo.nombre }}</h3>
          <ul class="space-y-2 list-none">
            <li v-for="enfrentamiento in grupo.enfrentamientos" :key="enfrentamiento.id"
              class="flex items-center justify-between p-2 rounded">
              <div class="flex-1 pr-2 text-right">
                <span :class="{ 'font-bold': enfrentamiento.ganador === enfrentamiento.participante1 }">
                  {{ enfrentamiento.participante1 }}
                </span>
              </div>
              <div class="px-2">vs</div>
              <div class="flex-1 pl-2">
                <span :class="{ 'font-bold': enfrentamiento.ganador === enfrentamiento.participante2 }">
                  {{ enfrentamiento.participante2 }}
                </span>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>

useSeoMeta({
  title: 'Copa Ministros del Dota',
  description: 'Campeonato interno de pro players',
  ogImage: 'https://fineproxy.org/wp-content/uploads/2023/08/Dota-2-logo.png',

})

useHead(() => ({
  title: 'Copa Ministros del Dota',
  meta: [
    {
      hid: 'og:title',
      property: 'og:title',
      content: 'Copa Ministros del Dota',
    },
    {
      hid: 'og:image',
      property: 'og:image',
      content: 'https://fineproxy.org/wp-content/uploads/2023/08/Dota-2-logo.png',
    },
  ],
}));

const grupos = [
  {
    nombre: 'Grupo A',
    enfrentamientos: [
      { id: 1, participante1: 'Ecsom', participante2: 'Edward', ganador: '' },
      { id: 2, participante1: 'Ecsom', participante2: 'Zed', ganador: '' },
      { id: 3, participante1: 'Ecsom', participante2: 'Neva', ganador: '' },
      { id: 4, participante1: 'Ecsom', participante2: 'Jahdiel', ganador: '' },
      { id: 5, participante1: 'Edward', participante2: 'Zed', ganador: '' },
      { id: 6, participante1: 'Edward', participante2: 'Neva', ganador: '' },
      { id: 7, participante1: 'Edward', participante2: 'Jahdiel', ganador: '' },
      { id: 8, participante1: 'Zed', participante2: 'Neva', ganador: '' },
      { id: 9, participante1: 'Zed', participante2: 'Jahdiel', ganador: 'Zed' },
      { id: 10, participante1: 'Neva', participante2: 'Jahdiel', ganador: '' },
    ],
  },
  {
    nombre: 'Grupo B',
    enfrentamientos: [
      { id: 11, participante1: 'Don Bicho', participante2: 'Marcux', ganador: 'Marcux' },
      { id: 12, participante1: 'Don Bicho', participante2: 'Raoul', ganador: '' },
      { id: 13, participante1: 'Don Bicho', participante2: 'Rguz', ganador: '' },
      { id: 14, participante1: 'Don Bicho', participante2: 'Juaya', ganador: 'Juaya' },
      { id: 15, participante1: 'Marcux', participante2: 'Raoul', ganador: 'Raoul' },
      { id: 16, participante1: 'Marcux', participante2: 'Rguz', ganador: '' },
      { id: 17, participante1: 'Marcux', participante2: 'Juaya', ganador: 'Marcux' },
      { id: 18, participante1: 'Raoul', participante2: 'Rguz', ganador: '' },
      { id: 19, participante1: 'Raoul', participante2: 'Juaya', ganador: 'Raoul' },
      { id: 20, participante1: 'Rguz', participante2: 'Juaya', ganador: 'Juaya' },
    ],
  },
  {
    nombre: 'Grupo C',
    enfrentamientos: [
      { id: 21, participante1: 'Ronaldo', participante2: 'Rugery', ganador: 'Ronaldo' },
      { id: 22, participante1: 'Ronaldo', participante2: 'Sebas', ganador: 'Sebas' },
      { id: 23, participante1: 'Ronaldo', participante2: 'Viceps', ganador: '' },
      { id: 24, participante1: 'Ronaldo', participante2: 'Wilder', ganador: '' },
      { id: 25, participante1: 'Rugery', participante2: 'Sebas', ganador: '' },
      { id: 26, participante1: 'Rugery', participante2: 'Viceps', ganador: '' },
      { id: 27, participante1: 'Rugery', participante2: 'Wilder', ganador: '' },
      { id: 28, participante1: 'Sebas', participante2: 'Viceps', ganador: '' },
      { id: 29, participante1: 'Sebas', participante2: 'Wilder', ganador: '' },
      { id: 30, participante1: 'Viceps', participante2: 'Wilder', ganador: '' },
    ],
  },
  {
    nombre: 'Grupo D',
    enfrentamientos: [
      { id: 31, participante1: 'Rednag', participante2: 'Enriqo', ganador: 'Enriqo' },
      { id: 32, participante1: 'Rednag', participante2: 'Pipoca', ganador: '' },
      { id: 33, participante1: 'Rednag', participante2: 'Rolfy', ganador: '' },
      { id: 34, participante1: 'Rednag', participante2: 'Gary', ganador: 'Gary' },
      { id: 35, participante1: 'Enriqo', participante2: 'Pipoca', ganador: 'Pipoca' },
      { id: 36, participante1: 'Enriqo', participante2: 'Rolfy', ganador: 'Rolfy' },
      { id: 37, participante1: 'Enriqo', participante2: 'Gary', ganador: 'Enriqo' },
      { id: 38, participante1: 'Pipoca', participante2: 'Rolfy', ganador: 'Pipoca' },
      { id: 39, participante1: 'Pipoca', participante2: 'Gary', ganador: '' },
      { id: 40, participante1: 'Rolfy', participante2: 'Gary', ganador: 'Rolfy' },
    ],
  },

];

const processMatches = computed(() => {
  const points = {};
  const won = {};
  const lost = {};
  const total = {};

  // return points, won, lost and total base on the result of the matches
  grupos.forEach(grupo => {
    grupo.enfrentamientos.forEach(({ participante1, participante2, ganador }) => {
      if (!points[participante1]) points[participante1] = 0;
      if (!points[participante2]) points[participante2] = 0;
      if (!won[participante1]) won[participante1] = 0;
      if (!won[participante2]) won[participante2] = 0;
      if (!lost[participante1]) lost[participante1] = 0;
      if (!lost[participante2]) lost[participante2] = 0;
      if (ganador === participante1) {
        points[participante1] += 3;
        won[participante1] += 1;
        lost[participante2] += 1;
      } else if (ganador === participante2) {
        points[participante2] += 3;
        won[participante2] += 1;
        lost[participante1] += 1;
      }
      total[participante1] = won[participante1] + lost[participante1];
      total[participante2] = won[participante2] + lost[participante2];
    });
  });

  const result = Object.keys(points).map(participante => ({
    participante,
    points: points[participante],
    won: won[participante],
    lost: lost[participante],
    total: total[participante]
  }));

  return result;
});

const listBestPlayers = computed(() => {
  const numberPlayers = 5;
  const bestPlayers = processMatches.value
    .sort((a, b) => {
      if (a.points === b.points) {
        return b.total - a.total; // Sort by number of matches
      }
      return b.points - a.points;
    })
    .slice(0, numberPlayers);

  return bestPlayers;
});

</script>
