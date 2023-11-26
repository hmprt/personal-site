<script lang='ts'>
    import {fade, fly} from 'svelte/transition'
    import {backInOut} from 'svelte/easing'
    import {onMount} from 'svelte'
    const splashText = `hhhhhhh                                                                                      tttt         
h:::::h                                                                                   ttt:::t         
h:::::h                                                                                   t:::::t         
h:::::h                                                                                   t:::::t         
h::::h hhhhh          mmmmmmm    mmmmmmm   ppppp   ppppppppp   rrrrr   rrrrrrrrr   ttttttt:::::ttttttt    
h::::hh:::::hhh     mm:::::::m  m:::::::mm p::::ppp:::::::::p  r::::rrr:::::::::r  t:::::::::::::::::t    
h::::::::::::::hh  m::::::::::mm::::::::::mp:::::::::::::::::p r:::::::::::::::::r t:::::::::::::::::t    
h:::::::hhh::::::h m::::::::::::::::::::::mpp::::::ppppp::::::prr::::::rrrrr::::::rtttttt:::::::tttttt    
h::::::h   h::::::hm:::::mmm::::::mmm:::::m p:::::p     p:::::p r:::::r     r:::::r      t:::::t          
h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p     p:::::p r:::::r     rrrrrrr      t:::::t          
h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p     p:::::p r:::::r                  t:::::t          
h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p    p::::::p r:::::r                  t:::::t    tttttt
h:::::h     h:::::hm::::m   m::::m   m::::m p:::::ppppp:::::::p r:::::r                  t::::::tttt:::::t
h:::::h     h:::::hm::::m   m::::m   m::::m p::::::::::::::::p  r:::::r                  tt::::::::::::::t
h:::::h     h:::::hm::::m   m::::m   m::::m p::::::::::::::pp   r:::::r                    tt:::::::::::tt
hhhhhhh     hhhhhhhmmmmmm   mmmmmm   mmmmmm p::::::pppppppp     rrrrrrr                      ttttttttttt  
                                            p:::::p                                                       
                                            p:::::p                                                       
                                            p:::::::p                                                     
                                            p:::::::p                                                     
                                            p:::::::p                                                     
                                            ppppppppp                                                     `

const splashRows = splashText.split('\n')
$: showSplash = false;
$: showHello = false;
$: showContent = false;

onMount(() => {
     showSplash = true
     setTimeout(() => {
         showSplash = false
     }, 3000)
    setTimeout(() => {
        showContent = true
    }, 5500)
})

</script>

<div class='flex flex-col w-screen h-screen bg-black text-white font-display justify-center items-center overflow-x-hidden'>

    <div id='splash-rows' class='flex flex-col whitespace-pre-wrap gap-0 w-fit overflow-x-hidden self-center justify-self-center place-self-center text-center'>
        {#if showSplash == true}
        {#each splashRows as row, i}
        {@const delay = i * 50}
        {@const leftOrRight = i % 2 == 0 ? -1 : 1}
        <div 
        transition:fly={{delay: delay, x: leftOrRight * 200, duration: 1000, easing: backInOut}}
        class='text-[6px] md:text-[12px] 
        -mt-[4px] md:-mt-[9px]'>
            {row}
        </div>
        {/each}
        {:else if showContent == true}
        <div class='flex flex-col w-full h-full p-4 text-start text-xl md:text-5xl items-start gap-4'>
            <div transition:fade={{duration: 500}}>My name is <span class='text-red-400'>Harvey Michael Pratt</span></div>
            <div transition:fade={{duration:500, delay: 2000}}>I'm a founder, artist and computer programmer</div>
            <div transition:fade={{duration:500, delay: 3500}}>In 2023 I founded <a class='underline text-blue-300' href='https://thepromenade.ai'>The Promenade</a> to build AI games</div>
            <div transition:fade={{duration:500, delay: 5500}}>My last project was <a class='underline text-blue-300' href='https://freenft.com/about'>FreeNFT</a></div>
            <div transition:fade={{duration:500, delay: 7000}}><a class='underline text-blue-400' href='https://twitter.com/npceo_'>Follow me </a> to stay up to date</div>
            </div>
        {/if}
        </div>
</div>
