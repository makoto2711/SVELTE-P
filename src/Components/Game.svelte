<script>
  let arr = [1, 2, 3, 4, 5, 6],
    show = true, number = "", 
    life_points = 2, message = ""

  function start() {
    
    show = false
    number = randomNumber();
    shuffle(arr);
    arr = [...arr];
     alert(`You have: ${life_points} 💓`)
  }

  const randomNumber = () => Math.floor(Math.random() * (6 - 1 + 1) + 1) + "";

function action(i) 
{
  const rpta = arr[i] == +number

  if (rpta) message = "You Win"
  else life_points-- == 0 ? message = life_points+ "" : message  = "You Lose"

  if ( !life_points || rpta) 
  {
      show = true 
      life_points = 2
      alert(message)   
  }
  else alert(`You have: ${life_points} 💓`)
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
         <div class="col-6 col-md-4 col-lg-2 p-0">
          {#if show}
              <img src="./img/0{item}.png" loading="lazy" class="w-100 h-100" alt=""  />
          {:else}
            <button on:click={()=> {action(i)}} class="w-100 bg-light height fs-4">?</button>
          {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>

 <style>
    .height
    {
        height: 85px;
    }
 </style>
