<script context="module">
  // export async function load({fetch}) {
  //   const res = await fetch("https://jsonplaceholder.typicode.com/posts")
  //   const data = await res.json()

  //   if(res.ok){
  //     return {
  //       props:{
  //         data
  //       }
  //     }
  //   }

  //   return {
  //     status: res.status,
  //     error: new Error('Could not fetch the guides')
  //   }
  // }
</script>

<script>
  export let guides = [];
  fetch("https://jsonplaceholder.typicode.com/posts")
    .then((response) => response.json())
    .then((data) => (guides = data));
</script>

<div class="guides">
  <ul>
    {#each guides as guide}
      <li>
        <a sveltekit:prefetch href={`/guides/${guide.id}`}>{guide.title}</a>
      </li>
    {/each}
  </ul>
</div>

<style>
  .guides {
    margin-top: 20px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  a {
    display: inline-block;
    margin-top: 10px;
    padding: 10px;
    border: 1px dotted rgba(255, 255, 255, 0.2);
  }
</style>
