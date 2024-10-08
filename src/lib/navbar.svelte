<script>
    import icon from '../assets/icon.png';
    import github from '../assets/github.png'
    import Post from './ui/button.svelte'
</script>

<div class="flex flex-row p-4 bg-black rounded-3xl">

  <div class="flex-none">
    <div class="flex">
        <a href="https://rosex.vercel.app/">
            <img src={icon} alt="Icon" class="size-16">    
        </a>  
    </div>
   </div>

    <div class="flex-1">
    </div>

    <div class="flex-none">
        <Post />
    </div>
</div>