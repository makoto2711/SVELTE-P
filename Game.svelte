<script> 
  let arr = [1, 2, 3, 4, 5, 6],
    show = true,
    number = "",
    life_points = 2,
    message = ""
 

  function start() {
    show = false;
    number = randomNumber();
    shuffle(arr);
    arr = [...arr];
    alert(`You have: ${life_points} 💓`);
  }

  const randomNumber = () => Math.floor(Math.random() * (6 - 1 + 1) + 1) + "";

  function action(i) {
    const rpta = arr[i] == +number;

    if (rpta) message = "You Win";
    else
      life_points-- == 0
        ? (message = life_points + "")
        : (message = "You Lose");

    if (!life_points || rpta) {
      show = true;
      life_points = 2;
      alert(message);
    } else alert(`You have: ${life_points} 💓`);
  }

  function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
      let j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
  }
</script>

<div class="container-fluid">
  <div class="row py-5 justify-content-center align-items-center h-100">
    <div class="col-10 col-md-4">
      {#if show}
        <section class="text-center">
          <button on:click={start} class="px-4 py-1 bg-warning fs-5">
            <strong>Start</strong>
          </button>
        </section>
      {/if}
      <section class="py-3">
        <p class="text-white fs-3">Number: {number}</p>
      </section>

      <div class="row">
        {#each arr as item, i}
          <div class="col-6 col-md-4 col-lg-2 px-2 py-3 py-lg-0 px-lg-2">
            {#if show}
              <img
                src="./img/0{item}.png"
                loading="lazy" class="w-100 h-100" alt="" />
            {:else}
            <a on:click|preventDefault={() => {action(i); }} href="_self"  >
               <img 
                src="./img/0{number}.png"
                loading="lazy" class="w-100 h-100" alt="" />
             </a> 
              
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>

<style>

  a 
  {
    position: relative;
    display: inline-block; 


  }
 
  img {
    border: 1px solid white;
    border-radius: 8px; 
background: #8fdad1;
box-shadow:  2px 2px 6px #1fbaa8,
             -2px -2px 6px #1fbaa8;
  }

  a::before
  {
    content: "";
    border-radius: 8px;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(83, 83, 83); /* Cambia el color de fondo aquí */
    opacity: 1; /* Cambia la opacidad del color de fondo aquí */ 
  }

    a::after {
    content: "?"; /* Cambia el texto aquí */
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #fff; /* Cambia el color del texto aquí */
    font-size: 1.5rem; /* Cambia el tamaño de fuente aquí */
    font-weight: bold; /* Cambia el peso de la fuente aquí */
    text-align: center;
  }

@media screen and (max-width: 48em ) 
{
     a::after {
    font-size: 2rem; /* Cambia el tamaño de fuente aquí */  
  }
}
  

</style>
