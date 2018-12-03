<template>
    <div id="app">
        <page-main v-if='typePage === "PAGE_MAIN"'/>
        <page-of-data v-else-if='typePage === "PAGE_OF_DATA"' />
        <page-without-data v-else-if='typePage === "PAGE_WITHOUT_DATA"' />
    </div>
</template>

<script>
    import PageMain from './components/PageMain';
    import PageOfData from './components/PageOfData';
    import PageWithoutData from './components/PageWithoutData';

    export default {
        name: 'App',
        data: function() {
            return {
                typePage: 'PAGE_MAIN'
            }
        },
        components: {
            'page-main': PageMain,
            'page-of-data': PageOfData,
            'page-without-data': PageWithoutData
        }
    }
</script>