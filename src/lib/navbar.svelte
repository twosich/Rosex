<script>
    import icon from '../assets/icon.png'
    import github from '../assets/github.png'
    import Post from './ui/button.svelte'
</script>

<div class="flex flex-row p-4 bg-black rounded-3xl items-center md:flex-row flex-col">

    <div class="flex-none mb-4 md:mb-0">
      <div class="flex">
        <a href="https://rosex.vercel.app/">
          <img src={icon} alt="Icon" class="w-16 h-16"> 
      </div>
    </div>
  
    <div class="flex-1">
    </div>
  
    <div class="flex-none">
      <div class="flex items-center">
        <Post />
      </div>
    </div>
  </div>
  