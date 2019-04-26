<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-6 col-xs-12">
          <TextArea></TextArea>
          <ProgressBars :missions="missions"></ProgressBars>
        </div>

        
          <MissionWrapper :missions="missions"></MissionWrapper>

          <div v-if="openModal" class="modal-window">
            <div style="max-width: 100%">
            <h3>End SomeThing first</h3>
            <a @click.prevent="openModal =false" class="modal-close" href="">
                x
            </a>
          </div>
        </div>
          

      </div>
    </div>
  </div>
</template>

<script>
import Mission from './components/Mission'
import MissionWrapper from './components/MissionWrapper'
import ProgressBars from './components/ProgressBars'
import TextArea from './components/TextArea'
//import Hello from './components/Hello'

export default {
  name: 'app',
  data(){
    return {
      missions: [],
      openModal: false
    }
  },
  components: {
    TextArea,
    ProgressBars,
    MissionWrapper,
    Mission
  },

  created() {
    eventBus.$on("add" ,(mission) => {
      if(this.missions.length < 10)
        this.missions.push(mission);
      else this.openModal = true
    });
    eventBus.$on("deleted" ,(index) => {
      this.missions.splice(index, 1);
    });

  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Comfortaa', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.container{
  padding-top: 60px;
}
</style>
