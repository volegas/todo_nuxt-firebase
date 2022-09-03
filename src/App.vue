<template>
  <div id="app" class="container-fluid">
    <div class="container-fluid">
        <div>
          <Topic v-if="state == 0" v-on:setTopic = "updateTopic($event)"/>
          <Entry :socket="socket" v-if="state == 1" :topic="topic" v-on:setCharacter = "updateCharacter($event)"/>
          <Chat v-if="state == 2" :character="selectedCharacter" :name="name" :socket="socket" :topic="topic"/>
        </div