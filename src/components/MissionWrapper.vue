<template>
	
    <div class="col s12 m6 right">
        
        <ul class="collection with-header">
            <li class="collection-header">
                <h4 v-if="0 < missions.length && missions.length < 6"> {{ one_five }} </h4>
                <h4 v-else-if="5 < missions.length && missions.length< 11">{{ five_ten}}</h4>
                <h4 v-else-if="missions.length == 0"> {{ zero }} </h4>
            </li>

            <appMission :key="index"
                @click.native="deleted(index)"
                v-for="(mission, index) in missions"
                > {{mission}} </appMission> 

        </ul>
        
    </div> 

</template>

<script>

import myMission from './Mission'

export default {
	name: 'Mission',
	data () {
		return {
            zero: 'Time To Relax',
			one_five: 'Soft Work :)',
			five_ten: 'Hard Work :)'
		}
    },
    props: {
        missions: Array
    } ,
    methods: {
        deleted(index){
            eventBus.$emit('deleted', index);
        }
    },
    components: {
        appMission: myMission
    },
    created() {
        
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    ul{
        padding-left: 50px;
        margin-left: 10px;
        background: #fafafa;
        border-radius: 10px;
        box-shadow: 0 2px 8px rgba(0,0,0,.3);
        overflow: hidden;
    }

    ul:before {
        content: '';
        position: absolute;
        top: 0; bottom: 0; left: 0;
        width: 50px;
        background: radial-gradient(#575450 6px, transparent 7px) repeat-y;
        background-size: 30px 30px;
        border-right: 3px solid #D44147;
        box-sizing: border-box;
    }
</style>
