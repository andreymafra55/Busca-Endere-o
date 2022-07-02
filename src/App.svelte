<script lang="ts">
  let cep ="";
  let dados = {}

  async function consulta() {
    console.log(cep);
    let response = await fetch(`https://viacep.com.br/ws/${cep}/json/ `)
    let data = await response.json();
    console.log(data);
    dados=data;
  }

</script>

<main>
  <h1>Busca Endereço</h1>
  <input type="text" bind:value={cep} placeholder="Digite seu cep">
  <button on:click={consulta}>consultar</button>
  
  <fieldset>

    <br>
    Cidade : {dados.localidade ?? '-'}
    <br>
    Bairro : {dados.bairro ?? '-'}
    <br>
    Rua : {dados.logradouro ?? '-'}
  </fieldset>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  h2{
    color: black;
    text-transform: uppercase;
    font-size: 1.2rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  input[type=text]{
    width: 10%;
    padding: 12px 20px;
    margin: 10px 0;
    box-sizing: border-box;
  }

  fieldset{
    width: 20%;
    margin-left: 475px;
    
  }

  button{
    font-size: 15px;
    background-color: #e7e7e7; color: black;
    padding: 10px 24px;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
