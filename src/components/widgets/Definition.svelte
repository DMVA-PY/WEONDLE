<script context="module" lang="ts">
  const cache = new Map<string, Promise<DictionaryEntry>>();
</script>

<script lang="ts">
  export let word: string;
  /** The maximum number of alternate definitions to provide */
  // Import your static word list
  import { words } from "../../utils"; // Assuming the word list is stored in utils.ts

  // Function to get word data from the static dictionary
  function getWordData(word: string): DictionaryEntry | null {
    const foundWord = words.words.find((w) => w.word === word);
    return foundWord || null;
  }
</script>

<div class="def">
  {#if getWordData(word)}
    <!-- If word is found in the static dictionary -->
    <h2>{word}</h2>
    <em>Descripción</em>
    <ol>
      <li>{getWordData(word).definition}</li>
    </ol>
  {:else}
    <!-- If word is not found, show the catch fallback -->
    <div>
      La palabra era <strong>{word}</strong>. gillipodle (No se encontró una
      definición estática)
    </div>
  {/if}
</div>

<style>
  h2 {
    display: inline-block;
    margin-right: 1rem;
    margin-bottom: 0.8rem;
  }
  ol {
    padding-left: 1.5rem;
  }
  li {
    margin-bottom: 0.5rem;
  }
  li::first-letter {
    text-transform: uppercase;
  }
  li::marker {
    color: var(--fg-secondary);
  }
</style>
