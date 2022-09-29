<script>
  import { page } from "$app/stores";
  import { error, redirect } from "@sveltejs/kit";
  import { onMount } from "svelte";

  const id = $page.params.id;

  let guide;
  onMount(() => {
    fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        guide = data;
        console.log(guide);
        let markup = `<h2>${guide.title}</h2>
  <p>${guide.body}</p>`;

        if (JSON.stringify(guide) == JSON.stringify({})) {
          ///redirect(301, "/guides");
          document.location.href = "/guides";
        } else {
          document
            .querySelector(".guide")
            .insertAdjacentHTML("beforeend", markup);
        }
      });
  });
  // fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
  //   .then((response) => {
  //     return response.json();
  //   })
  //   .then((data) => {
  //     guide = data;
  //     console.log(guide);
  //     let markup = `<h2>${guide.title}</h2>
  // <p>${guide.body}</p>`;

  //     document.querySelector(".guide").insertAdjacentHTML("beforeend", markup);
  //   });

  // export let guides;
  // foo();
  // let foo = async () => {
  //   let obj;

  //   const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);

  //   obj = await res.json();
  //   return obj;
  // };

  // console.log(guides);
</script>

<!-- <script>
  export let guide;
</script> -->

<div class="guide">
  <!-- <h2>{guide.title}</h2>
  <p>{guide.body}</p> -->
</div>

<style>
  .guide {
    margin-top: 40px;
    padding: 10px;
    border: 1px dotted rgba(255, 255, 255, 0.2);
  }
</style>
