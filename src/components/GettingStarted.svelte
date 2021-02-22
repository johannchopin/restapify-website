<script>
  import Terminal from './Terminal.svelte'

  const importRpfyCode = `yarn global add restapify
# OR 
npm install -g restapify`
  const instanciateRpfy = `import * as path from 'path'
import Restapify from 'restapify'

const apiFolderPath = path.resolve(__dirname, './path/to/folder')

const rpfy = new Restapify({
  rootDir: apiFolderPath
})
rpfy.run()`
</script>
<div class="row justify-content-center">
  <div class="col-md-8">
    <h2>Getting Started</h2>
    <h4 class="mt-5">Using the cli</h4>
    <p>The simplest way to use Restapify is to use his <a href="/docs#cli">cli</a> ...</p>
    <Terminal language="plaintext" content={importRpfyCode}/>
    <p>...and then serve your api folder:</p>
    <Terminal language="shell" content="restapify serve path/to/folder/" />

    <h4 class="mt-5">Using the JavaScript class</h4>

    <p>You can install restapify's class using `npm` (note that this package should be a devDependency):</p>
    <Terminal language="shell" content={importRpfyCode} />

    <p>You can then import the class and instantiate it to serve the api folder:</p>
    <Terminal language="javascript" content={instanciateRpfy} />

  </div>
</div>