<script lang="ts">
  import { Highlight } from "svelte-highlight";
  import { json, javascript, shell, plaintext } from "svelte-highlight/languages";

  export let content: string
  export let language: string = ''

  let className = ''
  const languages = {
    json,
    javascript,
    shell,
    plaintext
  }

  export {className as class}
</script>

<style lang="scss">

  .editor {
    overflow: hidden;

    .editor-toolbar {
      border: solid 1px #1E1E1E;
      border-radius: 5px 5px 0 0; 

      div {
        height: 12px;
        width: 12px;
        border: solid 1px #1E1E1E;
      }
    }

    code {
      border-radius: 0 0 5px 5px;
    }
  }

    .editor :global(pre) {
      padding: 0;
      width: 100%;
      border-radius: 0 0 5px 5px;
    }

    .editor :global(code) {
      display: inline-block;
      width: 100%;
      padding: 0;
    }
</style>

<div class={`editor d-flex flex-column ${className}`}>
  <div class="editor-toolbar d-flex ps-2 py-1 bg-light">
    <div class="rounded-circle mx-1 bg-danger"> </div>
    <div class="rounded-circle mx-1 bg-warning"> </div>
    <div class="rounded-circle mx-1 bg-success"> </div>
  </div>
  <Highlight class="p-3 mb-0" language="{languages[language]}" code={content} />
</div>