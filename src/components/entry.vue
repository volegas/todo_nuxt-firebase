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
                <input type="text" autocomplete="off" v-model="name" class="form-control set1" id="custom">
            </div>
            <div class="buttonContainer">
                <div class="button" v-bind:style="buttonClass" @click="nextScreen()">
                    <p> Get started </p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                characters : [{
                    src:'/chandler.png',
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
                activeItem: null,
                pickedCharacter: null,
                buttonState:0,
                name:'',
                onlineUsers:[]
            }
        },
        props:['socket','topic'],
        computed: {
            buttonClass() {
                console.log('buttonstate',this.buttonState)
                if(this.name.length != 0 && this.pickedCharacter) {
                    return {
                        'opacity':'1'
                    }
                } else {
                    return {
                        'opacity':'0.1'
                    }
                }
            }
        },
        methods: {
            selectcharacter(index) {
                console.log('index',index,this.characters[index]);
                if(!this.characters[index].taken) {
                    this.pickedCharacter = index;
                    this.activeItem = index;
                }
            },
            transformButtom(event,index) {
                if(event == 1 && !this.characters[index].taken && this.pickedCharacter == null) {
                    this.activeItem = index;
                } 
                if(event == 2 && this.pickedCharacter == null) {
                    this.activeItem = null;
                }
            },
            nextScreen() {
                if(this.name.length != 0 && this.pickedCharacter != null) {
                    let data = {
                        name:this.name,
                        character:this.pickedCharacter
                    }
                    this.$emit('setCharacter',data)
                }
            }
        },
        mounted() {
            this.socket.emit('SEND_MESSAGE', {
                fetchUsers:true
            });
            this.socket.on('MESSAGE', (data) => {
            if(!data.fromChat && (data.intro || data.reset)) {
                for(let i=0;i<data.users.length;i++) {
                    this.onlineUsers.push(data.users[i].user);
                   
                }
                for(let i=0;i<this.onlineUsers.length;i++) {
                    for(let j=0;j<this.characters.length;j++) {
                        if(this.characters[j].name.toLowerCase() == this.onlineUsers[i].toLowerCase()) {
                            this.characters[j].taken = true;
                        }
                    }
                }
            }
            // you can also do this.messages.push(data)
        });
        }
    }
</script>
<style scoped>
    @font-face {
        font-family: 