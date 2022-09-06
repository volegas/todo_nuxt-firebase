<template>
  <div id="app" class="container-fluid">
    <div class="container-fluid">
        <div>
          <Topic v-if="state == 0" v-on:setTopic = "updateTopic($event)"/>
          <Entry :socket="socket" v-if="state == 1" :topic="topic" v-on:setCharacter = "updateCharacter($event)"/>
          <Chat v-if="state == 2" :character="selectedCharacter" :name="name" :socket="socket" :topic="topic"/>
        </div>
    </div>
  </div>
</template>

<script>
import Entry from './components/entry.vue'
import Chat from './components/chat.vue'
import Topic from './components/topicselection.vue'
import io from 'socket.io-client';
export default {
  data() {
    return {
      state:0,
      selectedCharacter:null,
      name:null,
      topic:null,
      socket : io('https://immense-citadel-10641.herokuapp.com',{
        "rejectUnauthorized" : false
      })
    }
  },
  name: 'app',
  components: {
    Entry,
  