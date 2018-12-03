<template>
    <div class='main-page__container'>
        <h1>Main Page:</h1>
        <div class='main-page__table'>
            <list-quests v-for='(item, index) in dataMainPage' v-bind:key='index' v-bind:quest='JSON.parse(JSON.stringify(item))' v-bind:quantInRow='quantInRow' />
        </div>
    </div>
</template>

<script>
    import dataMainPage from '../../data/MainPageInfo.json';

    import ListQuests from './ListQuests';

    export default {
        name: 'MainPage',
        data: function() {
            return {
                dataMainPage: JSON.parse(JSON.stringify(dataMainPage)),
                quantInRow: 3
            }
        },
        components: {
            'list-quests': ListQuests
        }
    }
</script>

<style>
    .main-page__container {
        max-width: 600px;
        margin: 0 auto;
    }

    .main-page__table {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
        box-sizing: border-box;
    }
</style>