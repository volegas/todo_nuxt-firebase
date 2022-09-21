
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
