<script>
    import fundo from '../../assets/fundoF.png'
</script>
<img src={fundo} alt="fundo">
<div class="conteudo">
    <p>Rojério assustou Ovaldo que foge em direção à cidade grande!</p>
    <button>
        <a href="/fim">CONTINUAR</a>
    </button>
    
</div>


<style>
        img {
        width: 524px;
        height: 698px;
        position: absolute;
        top: 0px;
        right: 0px;
        z-index: 1;
    }
    .conteudo {
        position: relative;
        z-index: 2;
        padding: 40px;
        height: 618px;
        font-size: 20px;

    }
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
</style>