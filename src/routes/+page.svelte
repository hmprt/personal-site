<script lang='ts'>
    import {fade, fly} from 'svelte/transition'
    import {backInOut} from 'svelte/easing'
    import {onMount} from 'svelte'
//     const splashText = `hhhhhhh                                                                                      tttt         
// h:::::h                                                                                   ttt:::t         
// h:::::h                                                                                   t:::::t         
// h:::::h                                                                                   t:::::t         
// h::::h hhhhh          mmmmmmm    mmmmmmm   ppppp   ppppppppp   rrrrr   rrrrrrrrr   ttttttt:::::ttttttt    
// h::::hh:::::hhh     mm:::::::m  m:::::::mm p::::ppp:::::::::p  r::::rrr:::::::::r  t:::::::::::::::::t    
// h::::::::::::::hh  m::::::::::mm::::::::::mp:::::::::::::::::p r:::::::::::::::::r t:::::::::::::::::t    
// h:::::::hhh::::::h m::::::::::::::::::::::mpp::::::ppppp::::::prr::::::rrrrr::::::rtttttt:::::::tttttt    
// h::::::h   h::::::hm:::::mmm::::::mmm:::::m p:::::p     p:::::p r:::::r     r:::::r      t:::::t          
// h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p     p:::::p r:::::r     rrrrrrr      t:::::t          
// h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p     p:::::p r:::::r                  t:::::t          
// h:::::h     h:::::hm::::m   m::::m   m::::m p:::::p    p::::::p r:::::r                  t:::::t    tttttt
// h:::::h     h:::::hm::::m   m::::m   m::::m p:::::ppppp:::::::p r:::::r                  t::::::tttt:::::t
// h:::::h     h:::::hm::::m   m::::m   m::::m p::::::::::::::::p  r:::::r                  tt::::::::::::::t
// h:::::h     h:::::hm::::m   m::::m   m::::m p::::::::::::::pp   r:::::r                    tt:::::::::::tt
// hhhhhhh     hhhhhhhmmmmmm   mmmmmm   mmmmmm p::::::pppppppp     rrrrrrr                      ttttttttttt  
//                                             p:::::p                                                       
//                                             p:::::p                                                       
//                                             p:::::::p                                                     
//                                             p:::::::p                                                     
//                                             p:::::::p                                                     
//                                             ppppppppp                                                     `

const splashText = `|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

NNNNNNNN        NNNNNNNNPPPPPPPPPPPPPPPPP           CCCCCCCCCCCCCEEEEEEEEEEEEEEEEEEEEEE     OOOOOOOOO     
N:::::::N       N::::::NP::::::::::::::::P       CCC::::::::::::CE::::::::::::::::::::E   OO:::::::::OO   
N::::::::N      N::::::NP::::::PPPPPP:::::P    CC:::::::::::::::CE::::::::::::::::::::E OO:::::::::::::OO 
N:::::::::N     N::::::NPP:::::P     P:::::P  C:::::CCCCCCCC::::CEE::::::EEEEEEEEE::::EO:::::::OOO:::::::O
N::::::::::N    N::::::N  P::::P     P:::::P C:::::C       CCCCCC  E:::::E       EEEEEEO::::::O   O::::::O
N:::::::::::N   N::::::N  P::::P     P:::::PC:::::C                E:::::E             O:::::O     O:::::O
N:::::::N::::N  N::::::N  P::::PPPPPP:::::P C:::::C                E::::::EEEEEEEEEE   O:::::O     O:::::O
N::::::N N::::N N::::::N  P:::::::::::::PP  C:::::C                E:::::::::::::::E   O:::::O     O:::::O
N::::::N  N::::N:::::::N  P::::PPPPPPPPP    C:::::C                E:::::::::::::::E   O:::::O     O:::::O
N::::::N   N:::::::::::N  P::::P            C:::::C                E::::::EEEEEEEEEE   O:::::O     O:::::O
N::::::N    N::::::::::N  P::::P            C:::::C                E:::::E             O:::::O     O:::::O
N::::::N     N:::::::::N  P::::P             C:::::C       CCCCCC  E:::::E       EEEEEEO::::::O   O::::::O
N::::::N      N::::::::NPP::::::PP            C:::::CCCCCCCC::::CEE::::::EEEEEEEE:::::EO:::::::OOO:::::::O
N::::::N       N:::::::NP::::::::P             CC:::::::::::::::CE::::::::::::::::::::E OO:::::::::::::OO 
N::::::N        N::::::NP::::::::P               CCC::::::::::::CE::::::::::::::::::::E   OO:::::::::OO   
NNNNNNNN         NNNNNNNPPPPPPPPPP                  CCCCCCCCCCCCCEEEEEEEEEEEEEEEEEEEEEE     OOOOOOOOO     

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

`
const splashRows = splashText.split('\n')
$: showSplash = false;
$: showHello = false;
$: showContent = false;

onMount(() => {
     showSplash = true
     setTimeout(() => {
         showSplash = false
     }, 2000)
    setTimeout(() => {
        showContent = true
    }, 3500)
})

</script>

<div class='flex flex-col w-screen h-screen bg-black text-white font-display justify-center items-center overflow-x-hidden relative'>

    <div id='splash-rows' class='flex flex-col whitespace-pre-wrap gap-0 w-full max-w-[700px] overflow-x-hidden self-center justify-self-center place-self-center text-center'>
        {#if showSplash == true}
            {#each splashRows as row, i}
            {@const delay = i * 25}
            {@const leftOrRight = i % 2 == 0 ? -1 : 1}
            <div 
                transition:fly={{delay: delay, x: leftOrRight * 500, duration: 1000, easing: backInOut}}
                class='text-[6px] md:text-[12px] 
                -mt-[4px] md:-mt-[9px]'>
                    {row}
            </div>
            {/each}
        {:else if showContent == true}
        <!-- Top Bar -->
        <!-- <div class='absolute top-0 left-0 w-full h-fit flex items-center justify-center border-b-2 border-white p-2'>
            <div class='underline text-3xl flex h-full items-center justify-center text-center' in:fade>
                hmprt
            </div>
        </div> -->
        <div class='flex flex-col w-full h-full p-4 text-start text-xl md:text-5xl items-start gap-4'>
            <div transition:fade={{duration: 500}}>My name is <span class='text-red-400'>Harvey Michael Pratt</span></div>
            <div transition:fade={{duration:500, delay: 1000}}>I'm a founder, artist and computer programmer</div>
            <div transition:fade={{duration:500, delay: 2000}}>In 2023 I founded <a class='underline text-blue-300' href='https://thepromenade.ai'>The Promenade</a> to build AI games</div>
            <div transition:fade={{duration:500, delay: 3000}}>My last project was <a class='underline text-blue-300' href='https://freenft.com/about'>FreeNFT</a></div>
            <div transition:fade={{duration:500, delay: 4000}}><a class='underline text-blue-400' href='https://twitter.com/npceo_'>Follow me </a> to stay up to date</div>
            </div>
        {/if}
        </div>
</div>
