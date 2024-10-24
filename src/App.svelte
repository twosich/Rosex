<script>
  import Navbar from './lib/navbar.svelte';
  import Rules from './lib/rules.svelte';
  import { onMount, onDestroy } from 'svelte';
  import axios from 'axios';

  let imageLinks = [];
  let newImageUrl = '';
  let interval;

  // Función para obtener las imágenes
  const fetchImages = async () => {
    try {
      const response = await axios.get('https://rosexdart.globeapp.dev/webhook');
      imageLinks = response.data.image_links; // Asigna la lista de imágenes
    } catch (error) {
      console.error('Error al obtener imágenes:', error);
    }
  };

  // Función para agregar una nueva imagen
  const addImage = async () => {
    if (!newImageUrl) return;

    try {
      await axios.post('https://rosexdart.globeapp.dev/webhook', {
        attachments: [{ url: newImageUrl, content_type: 'image/jpeg' }]
      });
      newImageUrl = ''; // Limpia el campo de entrada
      fetchImages(); // Refresca la lista de imágenes
    } catch (error) {
      console.error('Error al agregar imagen:', error);
    }
  };

  // Obtén imágenes al montar el componente
  onMount(() => {
    fetchImages(); // Obtén imágenes al inicio
    interval = setInterval(fetchImages, 5000); // Consulta cada 5 segundos
  });

  // Limpia el intervalo al destruir el componente
  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<body class="bg-pink-600">
  <div class="p-2">
    <Navbar />
  </div>

  <div class="container mx-auto p-2">   
    <div class="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-6 lg:grid-cols-6 gap-4">
      <Rules />
      {#each imageLinks as imageLink}
        <div class="relative rounded-lg bg-black">
          <img src={imageLink} alt="Post" class="transition-all duration-300 hover:scale-105 w-full h-auto object-cover rounded-lg">
        </div>
      {/each}
    </div>
  </div>

</body>
