<div class="tela">
    <div class="cabecalho">
        <h2>OVO!</h2>
        <a href="/credito">Créditos</a>
    </div>
    <div class="centro">
        <h1>Ovoventuras de Ovaldo</h1>
        <h2>A FAZENDA</h2>
        <a href="/abertura">INICIAR</a>
    </div>
</div>




<style>
    @import url('https://fonts.googleapis.com/css2?family=Oi&family=Rosarivo&display=swap');
    * {
        margin: 0px;
    }
    .tela {
        width: 1224px;
        height: 870px;
    }
    .cabecalho{

        height: 88px;
        position: relative;
        display: flex;
        background-color: #FCB72C;
        color: #C0410C;
        font-weight: 900;
        justify-content: center;
        align-items: center;
    }
    .cabecalho a{
        font-family: 'Rosarivo', serif;
        position: absolute;
        text-decoration: none;
        font-size: 20px;
        color: #C0410C;
        top: 20px;
        right: 20px;
    }
    .cabecalho h2 {
        font-family: 'Oi', cursive;
        font-size: 20px;
    }
    .centro {
        background-size: cover;
        background-image: url(../assets/fazenda.jpg);
        height: 782px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: 'Rosarivo', serif;
    }
    .centro h1{
        color: #C0410C;
        font-size: 80px;
    }
    .centro h2{
        color: #C0410C;
        font-size: 60px;
        font-weight: 150;
    }
    .centro a{
        text-decoration: none;
        color: #C0410C;
        background-color: #FCB72C;
        font-size: 30px;
        padding: 25px 30px 25px 30px;
        border-radius: 40px;
    }
</style>