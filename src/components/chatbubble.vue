<template>
    <div>
        <div class="container">
            <div class="bubbleC"> 
                <div v-bind:style="bubbleStyle" class="bubble">
                        <div v-bind:style="colourStyle">
                            <h6 v-if ="!this.message.self">{{message.user}}</h6>
                        </div>
                        <div>
                            {{message.message}}
                        </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            colourmap