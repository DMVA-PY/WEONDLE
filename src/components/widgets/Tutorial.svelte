<script lang="ts">
	import { COLS, ROWS } from "../../utils";

	import { Tile } from "../board";
	export let visible: boolean;
</script>

<h3>COMO JUGAR WEONDLE</h3>
<div>Adivina la palabra en {ROWS} intentos.</div>
<div>Cada intento debe ser una palabra válida de {COLS}.</div>
<div>
	Después de cada intento, el color de las casillas cambiará para mostrar qué tan cerca estuvo tu intento de la palabra.
</div>

<div class:complete={visible} class="examples">
	<div><strong>Ejemplos</strong></div>
	<div class="row">
		<Tile value="W" state="🟩" />
		<Tile value="E" state="🔳" />
		<Tile value="O" state="🔳" />
		<Tile value="N" state="🔳" />
		<Tile value="A" state="🔳" />
	</div>
	<div>La letra <strong>W</strong> se encuentra en la palabra y esta en el lugar correcto</div>
	<div class="row">
		<Tile value="B" state="🔳" />
		<Tile value="A" state="🟨" />
		<Tile value="C" state="🔳" />
		<Tile value="A" state="🔳" />
		<Tile value="N" state="🔳" />
	</div>
	<div>La letra <strong>I</strong> se encuentra en la palabra pero esta en el lugar incorrecto.</div>
	<div class="row">
		<Tile value="W" state="🔳" />
		<Tile value="A" state="🔳" />
		<Tile value="T" state="🔳" />
		<Tile value="O" state="⬛" />
		<Tile value="N" state="🔳" />
	</div>
	<div>La letra <strong>O</strong> no se encuentra en la palabra.</div>
</div>


<style lang="scss">
	div {
		margin: 14px 0;
	}
	.examples {
		border-top: 1px solid var(--border-primary);
		:global(.row > *) {
			height: 100%;
			aspect-ratio: 1;
		}
		&:not(.complete) :global(.row .back) {
			transition-delay: 0.3s;
		}
	}
	.row {
		height: 40px;
		display: flex;	
		gap: 4px;
	}
</style>
