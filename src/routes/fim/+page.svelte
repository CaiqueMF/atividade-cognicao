<div class="tela">
    <div class="cabecalho">
        <h2>OVO!</h2>
        <a href="/credito">Créditos</a>
    </div>
    <div class="centro">
        <p>Próximo Capítulo</p>
        <h1>Ovoventuras de Ovaldo</h1>
        <h2>A Cidade</h2>
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
        background: url(../../assets/cidade.jpg);
        background-size: cover;
        background-color: #F5F5F5;
        height: 782px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 10px;
    }
    .centro h1{
        color: white;
        font-size: 80px;
    }
    .centro h2{
        color: white;
        font-size: 60px;
        font-weight: 150;
    }
    p {
        color: white;
        font-size: 45px;
        font-weight: 100;
    }
</style>