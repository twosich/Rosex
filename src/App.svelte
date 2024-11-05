<script lang="ts">
  import Navbar from './lib/navbar.svelte';
  import Rules from './lib/rules.svelte';
 
</script>

<body class="bg-pink-600">
  <div class="p-2">
    <Navbar />
  </div>

  <div class="container mx-auto p-2">   
    <div class="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-6 lg:grid-cols-6 gap-4">
      <Rules />
    </div>
  </div>

</body>
