<script>
    let atual = 0
    let resposta=null
    let temp =''
    let passado = 0
    let tamanhoOvo = 1.3
    let tamanhoFazendeiro = 1
    function trocar(){
        if(atual==-2 || atual==-1){
            atual = passado+1
        }else if(atual==0||atual==2||atual==5){
            atual++
        }else if(atual == 1 && resposta!=null){
            if(levenshteinDistance(resposta.toLowerCase(),"intermitente")<=2){
                passado=atual
                atual = -1
            }else{
                passado=atual
                atual = -2
            }
            resposta = null
            temp = ''
        }else if(atual == 3 && resposta!=null){
            if(levenshteinDistance(resposta.toLowerCase(),"dificil")<=2){
                passado=atual
                atual = -1
            }else{
                passado=atual
                atual = -2
            }
            resposta = null
            temp = ''
        }else if(atual == 4 && resposta!=null){
            if(levenshteinDistance(resposta.toLowerCase(),"habito")<=2){
                passado=atual
                atual = -1
            }else{
                passado=atual
                atual = -2
            }
            resposta = null
            temp = ''
        }else if(atual == 6 && resposta!=null){
            if(levenshteinDistance(resposta.toLowerCase(),"continuamente")<=2){
                passado=atual
                atual = -1
            }else{
                passado=atual
                atual = -2
            }
            resposta = null
            temp = ''
        }
    }

    const levenshteinDistance = (str1 = '', str2 = '') => {
       const track = Array(str2.length + 1).fill(null).map(() =>
       Array(str1.length + 1).fill(null));
       for (let i = 0; i <= str1.length; i += 1) {
          track[0][i] = i;
       }
       for (let j = 0; j <= str2.length; j += 1) {
          track[j][0] = j;
       }
       for (let j = 1; j <= str2.length; j += 1) {
          for (let i = 1; i <= str1.length; i += 1) {
             const indicator = str1[i - 1] === str2[j - 1] ? 0 : 1;
             track[j][i] = Math.min(
                track[j][i - 1] + 1, // deletion
                track[j - 1][i] + 1, // insertion
                track[j - 1][i - 1] + indicator, // substitution
             );
          }
       }
       return track[str2.length][str1.length];
    };
    
    import ovo from '../../assets/ovo.png'
    import celeiro from '../../assets/celeiro.png'
    import fazendeiro from '../../assets/fazendeiro.png'
  import Narrativa from './narrativa.svelte';
    
</script>

    <img src={celeiro} alt="fundo" on:click={()=>trocar()}>
    
    <img class= "ovaldo" src={ovo} alt="ovo">
    <img class="Rojério" src={fazendeiro} alt="fazendeiro">
    
    <div class="dialogo">
        {#if atual == -2}
            <h2 class="falando">Ovaldo</h2>
            <p>Acho que não é bem isso...</p>
        {:else if atual == -1}
            <h2 class="falando">Ovaldo</h2>
            <p>era isso mesmo!</p>
        {:else if atual == 0}
            <h2 class="falando">Ovaldo</h2>
            <p>Por que você joga no bicho toda semana?</p>
        {:else if atual == 1}
            <h2 class="falando">Rojério</h2>
            <p>Por que eu ja ganhei <span class="verde">algumas vezes</span>... E um reforco</p>
            <form on:submit|preventDefault={() => {resposta = temp
                trocar()
                }}>
                <label>
                    <input bind:value={temp} />
                </label>
            </form>
        {:else if atual == 2}
            <h2 class="falando">Ovaldo</h2>
            <p>Mas o cachorro recebe carinho toda vez que pega o graveto, por que voce joga se só <span class="verde">as vezes</span> ganha?</p>
        {:else if atual == 3}
            <h2 class="falando">Rojério</h2>
            <p>Porque como eu venço <span class="verde">algumas vezes</span> é um comportamento mais <span>
                <form on:submit|preventDefault={() => {resposta = temp
                    trocar()
                    }}>
                    <label>
                        <input bind:value={temp} />
                    </label>
                </form>
            </span> de parar, mesmo que eu nem sempre ganhe um dia vai ser meu dia!</p>
        {:else if atual == 4}
            <h2 class="falando">Ovaldo</h2>
            <p>Acho que agora entendi, então o reforço intermitente é melhor quando você quer construir um <span>
                <form on:submit|preventDefault={() => {resposta = temp
                    trocar()
                    }}>
                    <label>
                        <input bind:value={temp} />
                    </label>
                </form>
            </span> que demora mais a ser esquecido?</p>
        {:else if atual == 5}
            <h2 class="falando">Rojério</h2>
            <p>Isso mesmo Ovaldo, mas sempre que Aafolou morde meu sapato... eu rebolo ele no mato</p>
        {:else if atual == 6}
            <h2 class="falando">Ovaldo</h2>
            <p>Então o fazendeiro pune <span>
                <form on:submit|preventDefault={() => {resposta = temp
                    trocar()
                    }}>
                    <label>
                        <input bind:value={temp} />
                    </label>
                </form>
            </span> o cachorro, melhor não me meter com ele...</p>
        {:else if atual == 7}
            <Narrativa/>
        {/if}
    </div>

<style>

</style>