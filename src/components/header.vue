<template>
    <div>
        <b-nav tabs>
            <b-nav-item disabled=""><b>quiz</b></b-nav-item>
            <b-nav-item disabled>correct answered questions {{correctAns}}/{{totalQue}}</b-nav-item>
        </b-nav>
    </div>
</template>

<script>
export default {
    props:{
        correctAns:Number,
        totalQue:Number
    }
}
</script>