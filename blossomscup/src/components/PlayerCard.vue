<template>
    <div class="d-flex flex-column">
        <div class="pfp position-relative">
            <img alt="Vue logo" :src="pfp()" style="width: 250px; height: 250px;">
            <div class="pfp-border position-absolute"></div>
        </div>

        <div class="d-flex flex-column details">
            <div class="position-relative" style="height: 60px">
                <div class="position-absolute name-bg"></div>
                <h2 class="position-absolute text-uppercase pl-3">{{player.name}}</h2>
            </div>
            
            <div class="d-flex flex-column align-items-center justify-content-center rank">
                <div class="d-flex align-items-center justify-content-center">
                    <img alt="Vue logo" class="me-2" :src="rank()" style="width: 75px; height: 75px;">
                    <h3>{{tr()}}</h3>
                </div>
                <span class="winchance mt-2">Win Chance: {{ wc() }}%</span>

            </div>
        </div>
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  player: Object
})

const { player } = toRefs(props);

const tr = () => Math.trunc(player.value.tr)

const wc = () => Number(player.value.strictProb).toFixed(2)

const rank = () => {
    if (player.value.name === 'weiiiiii') {
        return 'https://tetr.io/res/league-ranks/ss.png'
    }
    return 'https://tetr.io/res/league-ranks/u.png'
}

const pfp = () => {
    const pfps = {
        tossedbloom: 'https://tetr.io/user-content/avatars/610ec566ea073c5a9ff74f1e.jpg?rv=1661275765209',
        garlik: 'https://tetr.io/user-content/avatars/614abca9f7759744dc7ba401.jpg?rv=1665407367470',
        weiiiiii: 'https://tetr.io/user-content/avatars/5ed1518b8751236bfbf77f7e.jpg?rv=1617438024477',
        judist: 'https://tetr.io/user-content/avatars/5ec2bc8c46fbeb624db412d9.jpg?rv=1690508492107',
        doodoodog: 'https://tetr.io/user-content/avatars/616adb1b96100025d13944d1.jpg?rv=1645554477791',
        wongsz: 'https://tetr.io/user-content/avatars/5e98c7dd4515a67e2992e0a5.jpg?rv=1671106938399',
        olkward: 'https://tetr.io/user-content/avatars/61d8274a1d2f6f741fce44ca.jpg?rv=1671289691228',
        caan_do: 'https://tetr.io/user-content/avatars/6067578552bd429ba3d3a0d4.jpg?rv=1695132375399',
    }

    return pfps[player.value.name]
}

</script>

<style scoped>
.pfp {
    height: 250px;
    width: 250px;
}

.pfp img {
    border-radius: 8px;
}

.pfp-border {
    border-radius: 6px;
    border: 3px solid rgb(238, 163, 24);
    height: 240px;
    width: 230px;
    top: 5px;
    left: 10px;
}

.name-bg {
    width: 120%;
    height: 60px;
    transform: skewX(-25deg) translate(-10%, -10px);
    background: rgb(57, 0, 64);
    border-radius: 4px;
    z-index: 1;
}

.name-bg::before {
    content: '';
    border: 7px solid rgb(238, 163, 24);
    transform: skewX(-3deg);
    width: 20%;
    height: 60px;
    bottom: -10px;
    left: 10px;
    z-index: 1;
    border-right: none;
    border-top: none;
    display: block;
    position: absolute;   
}

.name-bg::after {
    content: '';
    border: 7px solid rgb(238, 163, 24);
    transform: skewX(-3deg);
    width: 60%;
    height: 60px;
    top: -10px;
    right: 10px;
    z-index: 2;
    border-left: none;
    border-bottom: none;
    display: block;
    position: absolute;   
}

h2 {
    font-family: "Now"; 
    z-index: 2;
    color: #FEFADC;
    width: 100%;
}

h3 {
    font-family: "Now"; 
    color: #FEFADC;
}

.winchance {
    font-family: "Now"; 
    color: #FEFADC;
}

.rank {
    background: rgb(14,15,14);
    background: linear-gradient(0deg, rgba(14,15,14,1) 22%, rgba(57,0,64,1) 100%); 
    position: relative;
    top: -40px;
    height: 240px;
    border-radius: 24px;
}
</style>