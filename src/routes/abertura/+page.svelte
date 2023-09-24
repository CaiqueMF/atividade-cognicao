<script>
    import celeiro from '../../assets/celeiro.png'
    import fundo from '../../assets/fundoF.png'
    import Dialogo0 from './dialogo0.svelte';
    import Dialogo1 from './dialogo1.svelte';
    import Dialogo2 from './dialogo2.svelte';
    let atual = 0

</script>
<div class="tela">
    <img class="fundo" src={celeiro} alt="celeiro">
    <div class="centro">
        <div class="centralizado">
            <img class="pagina" src={fundo} alt="fundo">
            <div class="conteudo">
                
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
        </div>
    </div>
</div>
<style>
a {
    text-decoration: none;
    color: #C0410C;
}

button {
    cursor: pointer;
    position: absolute;
    bottom: 60px;
    width: 200px;
    height: 50px;
    border-radius: 30px;
    box-shadow: 2px 2px #aeaeae;
    left: 0px;
    right: 0px;
    margin-left: auto;
    margin-right: auto;

    text-decoration: none;
    font-size: 20px;
    color: #C0410C;
    background-color: #FCB72C;
    padding: 0;
    border: none;
}
.conteudo {
        position: relative;
        z-index: 2;
        padding: 40px;
        height: 600px;

}
.tela {
        width: 1224px;
        height: 870px;
        position: relative;
    }
.fundo {
    width: 1224px;
    height: 870px;
    z-index: 0;
}
.centro {
    position: absolute;
    width: 1224px;
    height: 870px;
    left: 0px;
    top: 0px;
}
.centralizado {
    width: 524px;
    height: 698px;
    margin: auto;
    margin-top: 70px;
    position: relative;
}
.pagina {
    position: absolute;
    left: 0px;
    top: 0px;
    width: 524px;
    height: 698px;
    z-index: 1;
}

</style>