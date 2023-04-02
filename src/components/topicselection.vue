
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