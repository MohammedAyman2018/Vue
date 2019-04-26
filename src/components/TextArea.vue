<template>
	<div>
		<form>
			<div class="row">
				<div class="input-field col s12">
					<textarea v-model="mission" @keyup.enter="addMission" id="textarea2" 
					class="materialize-textarea" data-length="30"></textarea>
					<label for="textarea2">Just Do What You Need!</label>
				</div>
				<a 
					@click="addMission"
					class="waves-effect waves-purple btn-small purple lighten-3 white-text">
					<i class="material-icons right">add</i>Add
				</a>
			</div>
		</form>

		<div v-if="openModalOne" class="modal-window">
			<div style="max-width: 100%">
				<h3>Am I Joke To You?</h3>
				<img src="../assets/joke.jpg" class="img-responsive" width="350px">
				<a @click.prevent="openModalOne =false" class="modal-close" href="">
					x
				</a>
			</div>
		</div>
			
		<div v-if="openModalTwo" class="modal-window">
			<div style="max-width: 100%">
				<h3>Must Be Shorter Then 30 letter</h3>
				<a @click.prevent="openModalTwo =false" class="modal-close" href="">
					x
				</a>
			</div>
		</div>
</div>

</template>

<script>
import Mission from './Mission'

export default {
	name: 'TextArea',
	data () {
		return {
			mission: '',
			openModalOne: false,
			openModalTwo: false
		}
	},
	methods: {
		addMission() {
			if(this.mission == '' || this.mission == '\n'){
				this.mission ='';
				this.openModalOne= true;
			}

			else if (this.mission.length > 30) {	
				this.mission = this.mission.slice(0,30);
				this.openModalTwo = true;
			}

			else{
				eventBus.$emit('add', this.mission);
				this.mission ='';
			}
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
	div.col.s12{
		padding-left: 0;
		padding-right: 10px;
	}
	.modal-window {
		width: 100%;
		height: 100%;
		position: fixed;
		top: 0;
		left:0;
		background-color: rgba(0,0,0,0.7);
		z-index: 999999;
	}
	.modal-window > div{
		width: 400px;
		position: absolute;
		background-color: white;
		padding: 10px 30px;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%) 
	}
	.modal-close{
		font-size: 20px;
		color: black;
		position: absolute;

		top: 10px;
		right: 10px;
		transition: all 0.4s ease;
	}
	.modal-close:hover{
		color: gray;
		text-decoration: none;
	}
</style>
