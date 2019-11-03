<template>
    <div class='questionBox-container'>
        <b-jumbotron>
            <template v-slot:header>question 1</template>

            <template v-slot:lead>
            questions
            </template>

            <hr class="my-4">

            <p>option list
            </p>

            <b-button variant="primary" href="#">Submit</b-button>
            <b-button variant="success" href="#">Next</b-button>
        </b-jumbotron>
    </div>
</template>