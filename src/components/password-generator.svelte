<script>
	import { onMount } from "svelte";

  let longChars = 15;
  let password = '';

  let mayus = true;
  let minus = true;
  let nums = true;
  let simbols = false;

  let copied = false;
  const generatePassword = (long) => {
    let chars = ''
    if(mayus) {
      chars += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    }
    if(minus) {
      chars += 'abcdefghijklmnopqrstuvwxyz';
    }
    if(nums) {
      chars += '0123456789';
    }
    if(simbols) {
      chars += '!@#$%^&*()_+~`|}{[]:;?><,./-=';
    }
    let result = '';
    const charsLength = chars.length;
    for (let i = 0; i < long; i++) {
      result += chars.charAt(Math.floor(Math.random() * charsLength));
    }
    return result;
  }

  function handleGenerate() {
    password = generatePassword(longChars);
  }
  const copyPassword = () => {
    navigator.clipboard.writeText(password);
    copied = true;
    setTimeout(() => {
      copied = false;
    }, 3000);
  };

  onMount(() => {
    handleGenerate();
  });

</script>

<div class="flex">

  <div class="container mx-auto m-20 flex flex-col justify-center items-center">
    <div class="my-20 flex flex-col items-center gap-6">
      <h1 class="text-7xl text-green-500">Generador contraseñas</h1>
      <h2 class="text-xl text-white">Generador de contraseñas seguras de forma sencilla</h2>
    </div>
    <div class="flex flex-col bg-green-500 rounded-xl p-10 w-[50%]">
      {#if copied}
      <div class="mb-3 p-2 bg-indigo-800 items-center text-indigo-100 leading-none lg:rounded-full flex lg:inline-flex" role="alert">
        <span class="flex rounded-full bg-indigo-500 uppercase px-2 py-1 text-xs font-bold mr-3">Copy</span>
        <span class="font-semibold mr-2 text-left flex-auto">Tu contraseña se ha copiado al portapapeles</span>
        <!-- <svg class="fill-current opacity-75 h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M12.95 10.707l.707-.707L8 4.343 6.586 5.757 10.828 10l-4.242 4.243L8 15.657l4.95-4.95z"/></svg> -->
      </div>
      {/if}
      <div class="flex w-full gap-3">
        
        <div class="flex bg-white rounded-xl px-3 justify-center w-full">
          <input type="text" class="text-center text-lg w-full font-semibold outline-none" bind:value={password}>
          <button class="text-black" on:click={copyPassword}>
            <svg id='Copy_24' width='24' height='24' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'><rect width='24' height='24' stroke='none' fill='#000000' opacity='0'/>
              <g transform="matrix(1 0 0 1 12 12)" >
              <path style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-dashoffset: 0; stroke-linejoin: miter; stroke-miterlimit: 4; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;" transform=" translate(-12, -12)" d="M 4 2 C 2.895 2 2 2.895 2 4 L 2 18 L 4 18 L 4 4 L 18 4 L 18 2 L 4 2 z M 8 6 C 6.895 6 6 6.895 6 8 L 6 20 C 6 21.105 6.895 22 8 22 L 20 22 C 21.105 22 22 21.105 22 20 L 22 8 C 22 6.895 21.105 6 20 6 L 8 6 z M 8 8 L 20 8 L 20 20 L 8 20 L 8 8 z" stroke-linecap="round" />
              </g>
              </svg>
          </button>
        </div>
        
        <button on:click={handleGenerate} class="bg-green-700 hover:bg-green-800 text-white rounded-lg p-3 px-6">Generar Contraseña</button>
      </div>
      <div class="flex flex-col my-6 gap-3">
        <div class="flex gap-3 w-full">
          <div class="flex items-center text-white font-semibold">
            <div class="inline-flex items-center">
              <label class="relative flex items-center p-3 rounded-full cursor-pointer" htmlFor="blue">
                <input type="checkbox"
                  class="before:content[''] peer relative h-5 w-5 cursor-pointer appearance-none rounded-md border border-blue-gray-200 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-blue-500 checked:bg-blue-500 checked:before:bg-blue-500 hover:before:opacity-10"
                  id="blue" bind:checked={mayus} />
                <span
                  class="absolute text-white transition-opacity opacity-0 pointer-events-none top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 peer-checked:opacity-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 20 20" fill="currentColor"
                    stroke="currentColor" stroke-width="1">
                    <path fill-rule="evenodd"
                      d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                      clip-rule="evenodd"></path>
                  </svg>
                </span>
              </label>
            </div>
            <label for="mayusculas">Mayúsculas</label>
          </div>
          <div class="flex items-center text-white font-semibold">
            <div class="inline-flex items-center">
              <label class="relative flex items-center p-3 rounded-full cursor-pointer" htmlFor="blue">
                <input type="checkbox"
                  class="before:content[''] peer relative h-5 w-5 cursor-pointer appearance-none rounded-md border border-blue-gray-200 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-blue-500 checked:bg-blue-500 checked:before:bg-blue-500 hover:before:opacity-10"
                  id="blue" bind:checked={minus} />
                <span
                  class="absolute text-white transition-opacity opacity-0 pointer-events-none top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 peer-checked:opacity-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 20 20" fill="currentColor"
                    stroke="currentColor" stroke-width="1">
                    <path fill-rule="evenodd"
                      d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                      clip-rule="evenodd"></path>
                  </svg>
                </span>
              </label>
            </div>
            <label for="minusculas">Minúsculas</label>
          </div>
          <div class="flex items-center text-white font-semibold">
            <div class="inline-flex items-center">
              <label class="relative flex items-center p-3 rounded-full cursor-pointer" htmlFor="blue">
                <input type="checkbox"
                  class="before:content[''] peer relative h-5 w-5 cursor-pointer appearance-none rounded-md border border-blue-gray-200 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-blue-500 checked:bg-blue-500 checked:before:bg-blue-500 hover:before:opacity-10"
                  id="blue" bind:checked={nums} />
                <span
                  class="absolute text-white transition-opacity opacity-0 pointer-events-none top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 peer-checked:opacity-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 20 20" fill="currentColor"
                    stroke="currentColor" stroke-width="1">
                    <path fill-rule="evenodd"
                      d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                      clip-rule="evenodd"></path>
                  </svg>
                </span>
              </label>
            </div>
            <label for="numeros">Números</label>
          </div>
          <div class="flex items-center text-white font-semibold">
            <div class="inline-flex items-center">
              <label class="relative flex items-center p-3 rounded-full cursor-pointer" htmlFor="blue">
                <input type="checkbox"
                  class="before:content[''] peer relative h-5 w-5 cursor-pointer appearance-none rounded-md border border-blue-gray-200 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-blue-500 checked:bg-blue-500 checked:before:bg-blue-500 hover:before:opacity-10"
                  id="blue" bind:checked={simbols} />
                <span
                  class="absolute text-white transition-opacity opacity-0 pointer-events-none top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 peer-checked:opacity-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 20 20" fill="currentColor"
                    stroke="currentColor" stroke-width="1">
                    <path fill-rule="evenodd"
                      d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                      clip-rule="evenodd"></path>
                  </svg>
                </span>
              </label>
            </div>
            <label for="simbolos">Símbolos</label>
          </div>
        </div>
        <div class="flex w-full">
          <label for="longChars" class="w-60 text-white font-semibold">Password Long: {longChars}</label>
          <input type="range" class="w-full" bind:value={longChars} min="8" max="25" />
        </div>
      </div>
      
    </div>
  </div>
  
</div>
