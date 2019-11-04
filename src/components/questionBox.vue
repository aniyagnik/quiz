<template>
    <div class='questionBox-container'>
        <b-jumbotron>
            <template v-slot:header>question {{number}}</template>

            <template v-slot:lead>
            {{currentQuestion.question}}
            </template>

            <hr class="my-4">
            <b-list-group>
                <b-list-group-item 
                  v-for="(option,index) in suffleOptions" 
                  :key=index
                  @click="selectedOption(index)"
                  :class="[
                  !answered && index===selectedIndex? 'selectedAnswer' : 
                  answered && index===correctIndex ? 'correctAnswer' :
                  answered && selectedIndex===index && index!==correctIndex ? 'wrongAnswer' :'' ]"
                >
                    {{option}}
                </b-list-group-item>
            </b-list-group>
            <b-button variant="primary"
              @click="checkSubmittedAns"
              :disabled="selectedIndex==null || answered"
            >
                Submit
            </b-button>
            <b-button variant="success" @click="next" href="#">Next</b-button>
        </b-jumbotron>
    </div>
</template>
<script>
import _ from "lodash";
export default {
    props:{
        currentQuestion:Object,
        number: Number,
        next:Function,
        incrementCorrect: Function
    },
    data(){
        return {
            selectedIndex:null,
            suffleOptions:[],
            answered:false,
            correctIndex:null
        }
    },
    watch:{
        currentQuestion:{
            immediate:true,
            handler(){
                this.selectedIndex=null
                this.answered=false
                this.suffleOptionsFunction()
            }
        }
    },
    methods:{
        selectedOption(index){
            this.selectedIndex=index
        },
        suffleOptionsFunction(){
            let options=[...this.currentQuestion.incorrect_answers,this.currentQuestion.correct_answer]
            this.suffleOptions=_.shuffle(options)
            this.correctIndex=this.suffleOptions.indexOf(this.currentQuestion.correct_answer)
        },
        checkSubmittedAns(){
            this.answered=true
            if(this.selectedIndex===this.correctIndex){
                this.incrementCorrect()
            }
        }
    }
}
</script>

<style scoped>
.list-group{
    margin-bottom:15px;
}

.list-group-item:hover {
    background-color: lightgray;
    cursor: pointer;
}

.btn{
    margin : 0 10px;
}

.selectedAnswer{
    background-color:lightblue; 
}

.correctAnswer{
    background-color:lightgreen; 
}

.wrongAnswer{
    background-color:rgb(238, 160, 160); 
}
</style>