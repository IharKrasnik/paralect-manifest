<script>
  import StarIcon from '$lib/icons/Star.svelte';

  let manifests = [{
    emoji: '⭐',
    name: 'Act as\n entrepreuner'
  }, {
    emoji: '🗽',
    name: `Don't ask.\n Do it`
  }, {
    emoji: '🔆',
    name: `Give before \n you get`
  }, {
    isHidden: true,
    date: 'Jan 31',
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
  }]
</script>

<div>
  <h2 class="text-xl">
    Paralect
  </h2>
  
  <h1 class="text-2xl font-bold">
    Manifest ✨
  </h1>

  <div class="grid grid-cols-4 gap-4 mt-8">
    {#each manifests as manifest}
      <div class="z-10 whitespace-pre overflow-hidden relative text-2xl text-center py-8 px-4 flex flex-col justify-center items-center bg-[#ebebeb] aspect-square rounded-xl {manifest.isHidden ? '' : 'text-white'}">
        {#if !manifest.isHidden}
          <div class="absolute z-0">
            <StarIcon />
          </div>
        {/if}
        <div class="z-10">
          {manifest.emoji || '🔒'}
        </div>
        <div class="z-10">
          {manifest.name || manifest.date}
        </div>
      </div>
    {/each}
  </div>
</div>