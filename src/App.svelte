<script>
let inputString = "Type something here...";
let resultString = "";
let copyButtonText = "Copy to Clipboard";
$: resultString = transform(inputString);
function transform(input = "" ) {
    // Remove spaces, line breaks, and tabs
    const cleanedInput = input.replace(/\s+/g, '');

    // Remove all numbers
    const result = cleanedInput.replace(/\d+/g, '');
    return result;

}


async function handleCopy() {
    try {
      await navigator.clipboard.writeText(resultString);
      
      // Visual feedback
      var copied = true;
      copyButtonText = "Copied!";
      setTimeout(() => {
        copied = false;
        copyButtonText = "Copy to Clipboard";
      }, 2000);
    } catch (err) {
      copyButtonText = "Failed to copy!";
    }
  }


</script>

<div class="container">
  <div class="terminal-nav">
    <header class="terminal-logo">
      <div class="logo terminal-prompt">
        <a href="/" class="no-style">Toolbox </a>
      </div>
    </header>
    <nav class="terminal-menu">
      <ul vocab="https://schema.org/" typeof="BreadcrumbList">
        <li>
          <a href="/" class="menu-item"><span>Github</span></a><meta
            property="position"
          />
        </li>
      </ul>
    </nav>
  </div>
</div>
<div class="container">
  <section>
    <form action="#">
      <fieldset>
        <div class="form-group">
          <textarea
            bind:value={inputString}
            id="textarea"
            cols="30"
            rows="5"
            name="=&quot;textarea&quot;"></textarea
          >
        </div>
        <hr>
        <div class="form-group">
          <textarea
            bind:value={resultString}
            id="textarea"
            cols="30"
            rows="5"
            name="=&quot;textarea&quot;"></textarea
          >
        </div>
        <div class="form-group">
        <button on:click|preventDefault={handleCopy} class="btn btn-primary btn-block" name="submit" id="submit">{copyButtonText}</button>
      </div>
      </fieldset>
    </form>
  </section>
</div>
