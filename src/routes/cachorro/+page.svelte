<script>
  let falando = 'Ovaldo';
  let atual = 0;
  let resposta = null;
  let temp = '';
  let tamanhoOvo = 1.6 * 430 + 'px';
  let tamanhoCachorro = 1 * 350 + 'px';
  let offsetOvo = '0px';
  let offsetCachorro = '110px';
  let texto;

  function trocar() {
    console;
    if ((atual < 1 || resposta != null) && atual != 2) {
      if (falando == 'Ovaldo') {
        falando = 'Aafolou';

        tamanhoOvo = 1 * 430 + 'px';
        tamanhoCachorro = 1.5 * 350 + 'px';
        offsetOvo = '110px';
        offsetCachorro = '0px';
      } else {
        falando = 'Ovaldo';
        tamanhoOvo = 1.6 * 430 + 'px';
        tamanhoCachorro = 1 * 350 + 'px';
        offsetOvo = '0px';
        offsetCachorro = '110px';
      }
      atual++;
      if (atual == 2) {
        if (
          levenshteinDistance(resposta.toLowerCase(), 'contínuo') <= 2 ||
          levenshteinDistance(resposta.toLowerCase(), 'continuo') <= 2
        ) {
          texto = 'Era isso mesmo!';
        } else {
          texto = 'Acho que não é bem isso...';
        }
      }
    } else if (atual == 2) {
      tamanhoCachorro = '0px';
      tamanhoOvo = '0px';
      atual++;
    }
    if (atual >= 3) {
      tamanhoCachorro = '0px';
      tamanhoOvo = '0px';
    }
  }
  const levenshteinDistance = (str1 = '', str2 = '') => {
    const track = Array(str2.length + 1)
      .fill(null)
      .map(() => Array(str1.length + 1).fill(null));
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
          track[j - 1][i - 1] + indicator // substitution
        );
      }
    }
    return track[str2.length][str1.length];
  };

  import ovo from '../../assets/ovo.png';
  import cachorro from '../../assets/cachorro.png';
  import celeiro from '../../assets/celeiro.png';
  import Narrativa from './narrativa.svelte';
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="tela" on:click={() => trocar()}>
  <img class="fundo" src={celeiro} alt="fundo" />
  <img
    class="ovaldo"
    src={ovo}
    alt="ovo"
    style="--theme-width: {tamanhoOvo}; --offset: {offsetOvo}"
  />
  <img
    class="aafolou"
    src={cachorro}
    alt="cachorro"
    style="--theme-width: {tamanhoCachorro}; --offset: {offsetCachorro}"
  />

  <div class="dialogo">
    {#if atual <= 2}
      <h2 class="falando">{falando}</h2>
    {/if}
    {#if atual == 0}
      <p>
        Por que você <span class="verde">sempre</span> pega o graveto quando seu
        dono joga?
      </p>
    {:else if atual == 1}
      <p>
        Por que <span class="verde">toda vez</span> que eu pego ele me dá
        carinho... É um reforço
        <span>
          <form
            on:submit|preventDefault={() => {
              resposta = temp;
              trocar();
            }}
          >
            <label>
              <input bind:value={temp} />
            </label>
          </form>
        </span>
      </p>
    {:else if atual == 2}
      <p>{texto}</p>
    {:else}
      <div class="centro">
        <div class="centralizado">
          <Narrativa />
        </div>
      </div>
    {/if}
  </div>
</div>

<style>
  .verde {
    color: #008e28;
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
  span {
    display: inline-block;
  }
  .falando {
    position: absolute;
    left: 110px;
    bottom: 170px;
    z-index: 1;
    font-size: 45px;
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 40px;
    border-radius: 15px;
    border: 5px solid;
    border-color: #c0410c;
    background-color: #fcb72c;
    color: #c0410c;
  }
  p {
    width: 1224px;
    height: 160px;
    position: absolute;
    bottom: 0px;
    z-index: 3;
    color: #c0410c;
    background-color: #fcb72c;
    margin: 0px;
    font-size: 35px;
    text-align: center;
    padding-top: 80px;
    border-top: 5px solid;
    border-color: #c0410c;
    display: inline;
  }
  input {
    font-size: 35px;
    border: 0px;
    border-radius: 15px;
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
  .ovaldo {
    position: absolute;
    left: var(--offset);
    bottom: 80px;
    width: var(--theme-width);
    height: auto;
    z-index: 1;
  }
  .aafolou {
    position: absolute;
    right: var(--offset);
    bottom: 80px;
    width: var(--theme-width);
    height: auto;
    z-index: 1;
  }
</style>
