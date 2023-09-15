<script>
let falando = "Ovaldo"
let atual = 0
let resposta=null
let temp =''
let tamanhoOvo = 1.3
let tamanhoCachorro = 1
let texto
function trocar(){
    if((atual<1||resposta!=null)&&atual!=2){
        if(falando == "Ovaldo"){
            falando = "Aafolou"
            tamanhoOvo = 1
            tamanhoCachorro = 1.3
        }
        else{
            falando = "Ovaldo"
            tamanhoOvo = 1.3
            tamanhoCachorro = 1
        }
        atual++
        if(atual == 2){
        if(levenshteinDistance(resposta.toLowerCase(),"continuo")<=2){
            texto = "era isso mesmo!"
        }else{
            texto = "Acho que não é bem isso..."
        }
    }
    }else if(atual==2){
        tamanhoCachorro=0
        tamanhoOvo=0
        atual++
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
import cachorro from '../../assets/cachorro.png'
import celeiro from '../../assets/celeiro.png'
  import Narrativa from './narrativa.svelte';

</script>
<img src={celeiro} alt="fundo" on:click={()=>trocar()}>

<img class= "ovaldo" src={ovo} alt="ovo">
<img class="aafolou" src={cachorro} alt="cachorro">

<div class="dialogo">
    <h2 class="falando">{falando}</h2>
    {#if atual == 0}
        <p>Por que você <span class="verde">sempre</span> pega o graveto quando seu dono joga?</p>
    {:else if atual == 1}
        <p>Por que <span class="verde">toda vez</span> que eu pego ele me dá carinho... É um reforço</p>
        <form on:submit|preventDefault={() => {resposta = temp
                                                trocar()
        }}>
            <label>
                <input bind:value={temp} />
            </label>
        </form>
    {:else if atual==2}
        <p>{texto}</p>
    {:else}
        <Narrativa/>
    {/if}
</div>