<script>
    import celeiro from '../../assets/celeiro.png'
    import fundo from '../../assets/fundoF.png'
    import Dialogo0 from './dialogo0.svelte';
    import Dialogo1 from './dialogo1.svelte';
    import Dialogo2 from './dialogo2.svelte';
    let atual = 0

</script>
    <img src={celeiro} alt="celeiro">
    <div class="centro">
        <img src={fundo} alt="fundo">
        {#if atual == 0}
            <Dialogo0/>
        {:else if atual == 1}
            <Dialogo1/>
        {:else}
            <Dialogo2/>
        {/if}
        {#if atual<2}
            <button on:click={()=>atual++}>CONTINUAR</button>
        {:else}
            <button>
                <a href="/cachorro">CONTINUAR</a>
            </button>
        {/if}
    </div>
<style>

</style>