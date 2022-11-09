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
                