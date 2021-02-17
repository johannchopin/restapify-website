<script context="module">
  import { getDocsAsHtml, getContentTableAsHtml, DOCS_URL } from "../docs-generation/getDocs";

  export async function preload(page) {
    const response = await this.fetch(DOCS_URL)
    const inlineMd = await response.text()
    const htmlContentTable = getContentTableAsHtml(inlineMd)
		const htmlContent = getDocsAsHtml(inlineMd)

		return { htmlContent, htmlContentTable };
	}
</script>

<script>
  import { onMount } from "svelte"
  import { initHighlightJs } from "../utils"
  import editIcon from '../assets/edit-icon.svg'

  export let htmlContent
  export let htmlContentTable
  
  const scrollToSection = () => {
    const url = window.location.href
    const id = url.substring(url.lastIndexOf('#'))

    const urlContainsId = id.startsWith('#')

    if (urlContainsId) {
      document.getElementById(id.substring(1)).scrollIntoView();
    }
  }

  onMount(() => {
    initHighlightJs()
    scrollToSection()
  })
</script>

<style lang="scss">
	#wrapper {
    height: 100%;
	}

  #sidebar {
    min-width: 20vw;
    height: 100%;
		overflow: auto;
    padding-right: 1rem;

    :global(a) {
      white-space: nowrap;
      color: black;
      text-decoration: none;

      &:focus,
      &:hover {
        text-decoration: underline;
      }
    }

    :global(a) {
      white-space: nowrap;
      color: black;
      text-decoration: none;
    }

    & > :global(ul > li) {
      margin-top: 1em;
    }

    & > :global(ul > li > a) {
      font-weight: bold;
    }

    :global(ul) {
      padding-left: 1rem;
    }

    :global(li) {
      list-style: none;
    }
  }
  #docs {
		flex-grow: 1;
    height: 100%;
		overflow: auto;
		scroll-behavior: smooth;
    max-width: 70vw;

    a.btn:hover {
      img {
        filter: invert(100%);
      }
    }

    :global(h2:not(:first-of-type)) {
      margin-top: 40vh;
      &::before {
        content: "";
        display: inline-block;
        width: 100%;
        height: 2px;
        background-color: lightgray;
        margin-bottom: 1rem;
      }
    }

    :global(ul:first-of-type) {
      display: none;
    }

    :global(blockquote p) {
      margin: 0;
    }
  }
</style>

<svelte:head>
	<title>Docs • Restapify</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.6.0/styles/zenburn.min.css" integrity="sha512-JPxjD2t82edI35nXydY/erE9jVPpqxEJ++6nYEoZEpX2TRsmp2FpZuQqZa+wBCen5U16QZOkMadGXHCfp+tUdg==" crossorigin="anonymous" />
</svelte:head>

<div class="d-flex" id="wrapper">
	<div id="sidebar" class="border-end">
    {@html htmlContentTable}
  </div>
  <section id="docs" class="position-relative p-4">
    <a 
      href="https://github.com/johannchopin/restapify/edit/main/docs/README.md" 
      class="d-flex align-items-center position-absolute top-0 end-0 mt-4 me-4 btn btn-outline-dark"
    >
      <img src={editIcon} alt="edit docs">
      <p class="m-0 ms-1">Edit on GitHub</p>
    </a>
    {@html htmlContent}
  </section>
</div>

