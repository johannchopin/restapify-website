<script lang="ts">
  export let content: string
  export let language: string = ''

  let className = ''

  export {className as class}
</script>

<style lang="scss">
  pre {
    width: 300px;

    code {
      display: inline-block;
      width: 100%;
    }
  }

  .editor {
    width: fit-content;
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
</style>

<div class={`editor d-flex flex-column ${className}`}>
  <div class="editor-toolbar d-flex ps-2 py-1 bg-light">
    <div class="rounded-circle mx-1 bg-danger"> </div>
    <div class="rounded-circle mx-1 bg-warning"> </div>
    <div class="rounded-circle mx-1 bg-success"> </div>
  </div>
  <pre>
    <code class={`${language} p-3`}>{content}</code>
  </pre>
</div>