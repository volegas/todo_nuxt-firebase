<template>
  <div id="app" class="container-fluid">
    <div class="container-fluid">
        <div>
          <Topic v-if="state == 0" v-on:setTopic = "updateTopic($event)"/>
        