
<template>
    <div class="container-fluid full econtainer">
        <div class="marginSet">
        </div>
        <div class="headContainer">
            <h5 class="mont"> Enter a topic for your chatroom </h5>
            <div class="separator"></div>
        </div>
        <div class="topic">
            <h3 class="textmod"> The one where</h3>
        </div>
        <div class="topicContainer">
            <input type="text" autocomplete="off" v-model="topic" class="form-control input" id="custom" value="Eg: Where _____ dreams">
        </div>
        <div class="buttonContainer">
            <div class="button" v-bind:style="buttonClass" @click="nextScreen()">
                <p> Next </p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            topic:''
        }
    },
    computed: {
        buttonClass() {
            if(this.topic.length != 0) {
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
        nextScreen() {
            if(this.topic.length != 0) {
                console.log('topic')
                this.$emit('setTopic',this.topic)
            }
        }
    }
}
</script>
<style scoped>
    @font-face {
        font-family: 'friendsfont';
        src: url("./../assets/fonts/gabrwffr.woff");
        font-weight: normal;
        font-style: normal;
    }
    @font-face {
        font-family: 'montserrat';
        src: url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
        font-weight: normal;
        font-style: normal;
    }
    .mont {
        font-family: "montserrat";
        font-weight: 800;
        font-size: 20px
    }
    .textmod {
        font-family: "friendsfont";
        font-size: 25px;
        font-weight: 20;
        display: table;
        margin: 0 auto;
    }
    .econtainer {
        height: 100vh;
        background-color:#181817;
    }
    .input {
        margin-left: 10px;
    }
    .headContainer {