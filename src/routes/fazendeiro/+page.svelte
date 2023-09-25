<script>
  let atual = 0;
  let resposta = null;
  let temp = '';
  let passado = 0;
  let tamanhoOvo = 1.6 * 430 + 'px';
  let offsetOvo = '0px';
  let offsetFazendeiro = '110px';
  let tamanhoFazendeiro = 1 * 400 + 'px';
  function ovoFalando() {
    tamanhoOvo = 1.6 * 430 + 'px';
    offsetOvo = '0px';
    tamanhoFazendeiro = 1 * 400 + 'px';
    offsetFazendeiro = '110px';
  }
  function fazendeiroFalando() {
    tamanhoOvo = 1 * 430 + 'px';
    offsetOvo = '110px';
    tamanhoFazendeiro = 1.5 * 400 + 'px';
    offsetFazendeiro = '0px';
  }
  function trocar() {
    if (atual == -2) {
      atual = passado;
    } else if (atual == -1) {
      atual = passado + 1;
    } else if (atual == 0 || atual == 2 || atual == 5) {
      atual++;
    } else if (atual == 1 && resposta != null) {
      if (levenshteinDistance(resposta.toLowerCase(), 'intermitente') <= 2) {
        passado = atual;
        atual = -1;
      } else {
        passado = atual;
        atual = -2;
      }
      resposta = null;
      temp = '';
    } else if (atual == 3 && resposta != null) {
      if (
        levenshteinDistance(resposta.toLowerCase(), 'difícil') <= 2 ||
        levenshteinDistance(resposta.toLowerCase(), 'dificil') <= 2
      ) {
        passado = atual;
        atual = -1;
      } else {
        passado = atual;
        atual = -2;
      }
      resposta = null;
      temp = '';
    } else if (atual == 4 && resposta != null) {
      if (
        levenshteinDistance(resposta.toLowerCase(), 'hábito') <= 2 ||
        levenshteinDistance(resposta.toLowerCase(), 'habito') <= 2 ||
        levenshteinDistance(resposta.toLowerCase(), 'comportamento') <= 2
      ) {
        passado = atual;
        atual = -1;
      } else {
        passado = atual;
        atual = -2;
      }
      resposta = null;
      temp = '';
    } else if (atual == 6 && resposta != null) {
      if (levenshteinDistance(resposta.toLowerCase(), 'continuamente') <= 2) {
        passado = atual;
        atual = -1;
      } else {
        passado = atual;
        atual = -2;
      }
      resposta = null;
      temp = '';
    }
    switch (atual) {
      case -2:
        ovoFalando();
        break;
      case -1:
        ovoFalando();
        break;
      case 0:
        ovoFalando();
        break;
      case 1:
        fazendeiroFalando();
        break;
      case 2:
        ovoFalando();
        break;
      case 3:
        fazendeiroFalando();
        break;
      case 4:
        ovoFalando();
        break;
      case 5:
        fazendeiroFalando();
        break;
      case 6:
        ovoFalando();
        break;
      case 7:
        tamanhoOvo = '0px';
        tamanhoFazendeiro = '0px';
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
  import celeiro from '../../assets/celeiro.png';
  import fazendeiro from '../../assets/fazendeiro.png';
  import Narrativa from './narrativa.svelte';
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="tela" on:click={() => trocar()}>
  <img src={celeiro} alt="fundo" class="fundo" />

  <img
    class="ovaldo"
    src={ovo}
    alt="ovo"
    style="--theme-width: {tamanhoOvo}; --offset: {offsetOvo}"
  />
  <img
    class="rojerio"
    src={fazendeiro}
    alt="fazendeiro"
    style="--theme-width: {tamanhoFazendeiro}; --offset: {offsetFazendeiro}"
  />

  <div class="dialogo">
    {#if atual == -2}
      <h2 class="falando">Ovaldo</h2>
      <p>Acho que não é bem isso...</p>
    {:else if atual == -1}
      <h2 class="falando">Ovaldo</h2>
      <p>Era isso mesmo!</p>
    {:else if atual == 0}
      <h2 class="falando">Ovaldo</h2>
      <p>Por que você joga no bicho toda semana?</p>
    {:else if atual == 1}
      <h2 class="falando">Rojério</h2>
      <p>
        Por que eu já ganhei <span class="verde">algumas vezes</span>... É um
        reforço
        <span
          ><form
            on:submit|preventDefault={() => {
              resposta = temp;
              trocar();
            }}
          >
            <label>
              <input bind:value={temp} />
            </label>
          </form></span
        >
      </p>
    {:else if atual == 2}
      <h2 class="falando">Ovaldo</h2>
      <p>
        Mas o cachorro recebe carinho toda vez que pega o graveto, por que você
        joga se só <span class="verde">as vezes</span> ganha?
      </p>
    {:else if atual == 3}
      <h2 class="falando">Rojério</h2>
      <p>
        Porque como eu venço <span class="verde">algumas vezes</span> é um
        comportamento mais
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
        </span> de parar, mesmo que eu nem sempre ganhe um dia vai ser meu dia!
      </p>
    {:else if atual == 4}
      <h2 class="falando">Ovaldo</h2>
      <p>
        Acho que agora entendi, então o reforço intermitente é melhor quando
        você quer construir um <span>
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
        </span> que demora mais a ser esquecido?
      </p>
    {:else if atual == 5}
      <h2 class="falando">Rojério</h2>
      <p>
        Isso mesmo Ovaldo, mas <span class="verde">sempre</span> que Aafolou morde
        meu sapato... eu rebolo ele no mato!
      </p>
    {:else if atual == 6}
      <h2 class="falando">Ovaldo</h2>
      <p>
        Então o fazendeiro pune <span>
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
        </span> o cachorro, melhor não me meter com ele...
      </p>
    {:else if atual == 7}
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
  .rojerio {
    position: absolute;
    right: var(--offset);
    bottom: 80px;
    width: var(--theme-width);
    height: auto;
    z-index: 1;
  }
</style>
