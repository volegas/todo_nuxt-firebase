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
            colourmapping: {
                'Chandler': '#d12725',
                'Joey': '#00b8eb',
                'Monica': '#d12725',
                'Phoebe': '#fbbe15',
                'Rachel':'#00b8eb',
                'Ross': '#fbbe15'
            },
        }
    },
    name:'chatbubble',