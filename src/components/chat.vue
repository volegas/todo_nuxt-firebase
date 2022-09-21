
<template>
  <div class="container-fluid main">
        <div class="chatinfo">
            <div class="heading">
                <h2 class="headingText textmod"> {{topic}} </h2>
                <div class="separator"></div>
            </div>
            <div class="userInfo">
                <div class="character-image">
                    <img :src="characters[character].src">
                </div>
                <h4 class="mont info"> Your messages will be modified by {{characters[character].name}} </h4>
            </div>
            <div class="userContainer">
                <div class="users" v-for="(user,index) in onlineUsers" :key="index">
                    <div class="dot"></div>
                    <h6 class="username">{{user.name}}</h6>
                </div>
            </div>
        </div>
        <div class="chatscreen">
           <div>
                <div ref="messageView" class="chats">
                    <div class="messages" v-for="(msg, index) in messages" :key="index">
                        <div v-bind:style="chatBubbleStyle(index)">
                            <chatbubble :message="msg"></chatbubble>
                        </div>
                    </div>
                </div>
            </div>
            <div class="separatorChat"></div>
            <div class="message">
                <form @submit.prevent="sendMessage">
                    <div class="gorm-group pb-3">
                        <div class="displayprompt"> {{displayText}} </div>
                        <input type="text" autocomplete="off" v-model="message" class="form-control" id="custom">
                    </div>
                </form>
            </div>
        </div>
  </div>
</template>

<script>
import chatbubble from './chatbubble.vue'
export default {
    data() {
        return {
            user: '',
            message: '',
            messages: [],
            characterMapping: {
                0:'Chandler',
                1:'Joey',
                2:'Monica',
                3:'Phoebe',
                4:'Rachel',
                5:'Ross'
            },
            characters : [{
                    src:'/monica.png',
                    name:'Chandler'
                }, {
                    src:'/joey.png',
                    name:'Joey'
                }, {
                    src:'/monica.png',
                    name:'Monica'
                }, {
                    src:'/phoebe.png',
                    name:'Phoebe'
                }, {
                    src:'/rachel.png',
                    name:'Rachel'
                }, {
                    src:'/ross.png',
                    name:'Ross'
                }],
            onlineUsers: [],
            labelState: 0
        }
    },
    components: {
        chatbubble
    },
    props:['character','name','socket','topic'],
    computed: {
        characterName() {
            return this.characterMapping[this.character]
        },
        displayText() {
            let labelText = {
                0:'All you text will be ' + this.characterMapping[this.character] + '-fied',
                1:'Your text is now getting ' + this.characterMapping[this.character] + '-fied',
                2:'Your text has been successfully ' + this.characterMapping[this.character] + '-fied'
            }