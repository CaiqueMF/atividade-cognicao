<script>
    import celeiro from '../../assets/celeiro.png'
    import ovo from '../../assets/ovo.png'
    import cachorro from '../../assets/cachorro.png'
    import fazendeiro from '../../assets/fazendeiro.png'
    import fundo from '../../assets/fundoL.png'
</script>
<div class="tela">
    <img class="fundo" src={celeiro} alt="celeiro">
    <div class="dentro">
        <div class="cabecalho">
            <a href="/">voltar</a>
            <h2>OVO!</h2>
        </div>
        <div class="centro">
            <img class="pagina" src={fundo} alt="fundo">
            <div class="conteudo">
                <ul>
                    <h1>Equipe: OVO!</h1>
                    <li> Caique França (554935)</li>
                    <li> David Silva (555735)</li>
                    <li> Márcio Freires (554069)</li>
                    <li> Milena Costa(553713)</li>
                    <li> Rafaely Sombra (552241)</li>
                    <li> Levi Ribeiro (552849)</li>
                </ul>
                <ul class="horizontal">
                    <li><img src={ovo} alt="ovo"></li>
                    <li><img src={cachorro} alt="cachorro"></li>
                    <li><img src={fazendeiro} alt="fazendeiro"></li>
                    <li><img src={celeiro} alt="celeiro"></li>
                    <ul>
                        <li><a href="https://www.vniuqu.com/?product_id=174309900_51">https://www.vniuqu.com/?product_id=174309900_51</a></li>
                        <li><a href="https://www.pngwing.com/en/free-png-nlbej">https://www.pngwing.com/en/free-png-nlbej</a></li>
                        <li><a href="https://www.pngwing.com/en/free-png-ijorq">https://www.pngwing.com/en/free-png-ijorq</a></li>
                        <li><a href="https://eduilsonduarte.artstation.com/projects/W2D4AD">https://eduilsonduarte.artstation.com/projects/W2D4AD</a></li>
                    </ul>
                </ul>
                <div class="biblio">
                    <h2>Bibliografia</h2>
                    <a href="https://www.ufrgs.br/psicoeduc/behaviorismo/maquina-de-ensinar-de-skinner-1/">https://www.ufrgs.br/psicoeduc/behaviorismo/maquina-de-ensinar-de-skinner-1/</a>
                    <a href="https://ctd-smd.wixsite.com/cognosis2023-2/waldenii">https://ctd-smd.wixsite.com/cognosis2023-2/waldenii</a>
                </div>
            </div>
        </div>
    </div>
</div>
<style>
    .biblio {
        display: flex;
        flex-direction: column;
    }
    .biblio h2 {
        padding-top: 35px;
        font-size: 35px;
    }
    * {
        margin: 0px;
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
    .dentro {
        position: absolute;
        width: 1224px;
        height: 870px;
        left: 0px;
        top: 0px;
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
        position: absolute;
        text-decoration: none;
        font-size: 20px;
        color: #C0410C;
        top: 20px;
        right: 20px;
    }
    .cabecalho h2 {
        font-size: 40px;
    }
    .centro {
        width: 1009px;
        height: 756px;
        margin: auto;
        position: relative;
    }
    .centro .pagina{
        position: absolute;
        left: 0px;
        top: 0px;
        width: 1009px;
        height: 756px;
        z-index: 1;
    }
    .conteudo {
        position: relative;
        z-index: 2;
        text-align: center;
    }
    .conteudo ul{
        padding-top: 70px;
        text-align: center;
        list-style-type: none;
        font-size: 20px;
    }
    .horizontal {
        display: flex;
        justify-content: center;
    }
    .horizontal img{
        height: 130px;
        width: auto;
    }
    .horizontal ul {
        padding: 15px;
        font-size: 15px;
    }
    a{
        text-decoration: none;
        color: black;
    }
</style>