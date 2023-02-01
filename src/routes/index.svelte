<script>
  import { onMount } from 'svelte';
  import StarIcon from '$lib/icons/Star.svelte';
  import scratch from '$lib/use/scratch';
  import { fade, slide } from 'svelte/transition';

  let manifests = [{
    emoji: '⭐',
    name: 'Act as\n entrepreuner',
    url: 'https://www.linkedin.com/feed/update/urn:li:activity:7024172236982919168/'
  }, {
    emoji: '🗽',
    name: `Don't ask.\n Do it`,
    url: 'https://www.linkedin.com/feed/update/urn:li:activity:7026553104942645249'
  }, {
    emoji: '🔆',
    name: `Give before \n you get`,
    url: 'https://www.linkedin.com/feed/update/urn:li:activity:7026553104942645249'
  }, {
    isHidden: true,
    date: 'Feb 3',
  }, {
    isHidden: true,
    date: 'Feb 7',
  }, {
    isHidden: true,
    date: 'Feb 10',
  }, {
    isHidden: true,
    date: 'Feb 14',
  }, {
    isHidden: true,
    date: 'Feb 17',
  }, {
    isHidden: true,
    date: 'Feb 21',
  }, {
    isHidden: true,
    date: 'Feb 24',
  }, {
    isHidden: true,
    date: 'Feb 28',
  }];

  let isShown = false;

  onMount(() => {
    isShown = true;
  });

</script>

<div class="container max-w-[800px] mx-auto mt-4">
  <div class="flex justify-between items-center">
    <div>
      <h2 class="text-xl">
        Paralect
      </h2>
      
      <h1 class="text-2xl font-bold">
        Manifest ✨
      </h1>
    </div>
    <div>
      <a href="https://paralect.com" target="_blank" class="py-2 px-4 bg-black rounded-2xl text-white">
         Build with Paralect
      </a>
    </div>
  </div>

  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4 mt-8">
    {#if isShown}
      {#each manifests as manifest, i}
        <a 
          href="{manifest.url}"
          target="_blank" on:click="{(e) => { if (!manifest.url) { e.preventDefault(); }}}" in:fade={{ delay: i*50 }}
          on:mouseenter={() => manifest.isHover = true}
        >
          <div 
            class="transition-all duration-300 z-100 whitespace-pre overflow-hidden relative text-2xl text-center py-8 px-4 flex flex-col justify-center items-center aspect-square rounded-xl {manifest.isHidden ? 'bg-[#ebebeb] cursor-not-allowed' : 'text-white'} {manifest.isHover ? 'bg-black' : ''}"
            use:scratch
          >
            <div
              class="z-10 mb-2 text-3xl transition duration-300" 
              class:text-2xl={!manifest.isHover}
              class:scale-150={!manifest.isHidden && !manifest.isHover}
            >
              {manifest.emoji || '🔒'}
            </div>

            {#if manifest.date}
              <div class="z-10">
                {manifest.name || manifest.date}
              </div>
            {:else}
              {#if manifest.isHover}
                <div class="z-10" transition:slide>
                  {manifest.name}
                </div>
              {/if}
            {/if}
          </div>
        </a>
      {/each}
    {/if}
  </div>

  <div class="text-xl text-center mt-16 mb-8 text-gray-600" style="font-family: system-ui;">
    <div class="mb-2">
      <a href="https://paralect.com" target="_blank">Paralect</a> is a cozy startup studio.
    </div>
    We're on the mission to enable everyone from our community to build $1M+ startups.
  </div>
</div>

<div>
  <div class="text-center text-2xl mt-16 mb-8 font-bold">
    We build in public 🙌
  </div>

  <div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/iframe-resizer/4.3.2/iframeResizer.min.js" integrity="sha512-dnvR4Aebv5bAtJxDunq3eE8puKAJrY9GBJYl9GC6lTOEC76s1dbDfJFcL9GyzpaDW4vlI/UjR8sKbc1j6Ynx6w==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

    <iframe
      id="momentum-feed"
      style="width:100%; border: none;"
      src="https://app.mmntm.build/paralect/embed?theme=light&limit=10"
      onload="iFrameResize({'{}'}, '#momentum-feed')"
    />
  </div>

  <div class="text-center my-16">
    <a class="text-3xl bg-black p-8 text-white rounded-full" href="https://paralect.com" target="_blank">
      Build with Paralect
    </a>
  </div>
</div>