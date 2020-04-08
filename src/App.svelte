<script>
  import { v4 } from "uuid";

  let uuid = v4();
  let buttonText = "Copy";

  let timeout;

  const resetButtonText = () => {
    buttonText = "Copy";
  };

  const handleCopy = async e => {
    e.preventDefault();
    try {
      await navigator.clipboard.writeText(uuid);
      buttonText = "Copied to Clipboard";

      timeout = setTimeout(resetButtonText, 1000);
    } catch (error) {
      console.log(error);
    }
  };

  const handleRefresh = e => {
    e.preventDefault();
    uuid = v4();
    resetButtonText();
  };
</script>

<main>
  <h1>UUID v4</h1>
  <p>{uuid}</p>
  <button type="button" on:click={handleRefresh}>Refresh</button>
  <button type="button" on:click={handleCopy}>{buttonText}</button>
</main>
