<template>
    <div class="container-fluid full econtainer">
        <div class="marginSet">
        </div>
        <div class="headContainer">
            <h2 class="headingText textmod"> {{topic}} </h2>
            <div class="separator"></div>
        </div>
        <div class="mainContainer">
            <div class="headContainer">
                <h4 class="mont"> Who would you like your words to be twisted by? </h4>
            </div>
            <div class="charContainer">
                <div class="characters" v-for="(char,index) in characters" :key="index">
                    <div class="character-card"  @mouseover="transformButtom(1,index)" @mouseout="transformButtom(2,index)" @click="selectcharacter(index)" :class="{active: activeItem === index}">
                        <div class="selector">
                        </div>
                        <div>
                            <div class="alert" v-if="char.taken">
                                Unavailable
                            </div>
                            <div class="character-image">
                                <img :src="char.src">
                            </div>
                            <div class="character-name">
                                <div class="montSm">
                                    {{char.name}}
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="headContainer">
                <h4 class="set mont"> What are you called by your friends? </h4>
                <inp