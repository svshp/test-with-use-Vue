<template>
    <div class='current-quest' :style='{ width: quantInRowNew }'>
        <div class='current-quest__alias'>
            {{ quest.alias}}
        </div>
        <div class='current-quest__status' v-on:click='onSwitch'>
            <icon-check v-if='quest.status === "SUCCESS"' />
            <icon-delete v-else-if='quest.status === "CRASH"' />
            <icon-dash v-else-if='quest.status === "NO_DATA"' />
        </div>
    </div>
</template>

<script>
    import IconCheck from '../templates/IconCheck';
    import IconDelete from '../templates/IconDelete';
    import IconDash from '../templates/IconDash';

    export default {
        name: 'ListQuests',
        components: {
            'icon-check': IconCheck,
            'icon-delete': IconDelete,
            'icon-dash': IconDash
        },
        data: function() {
            return {
                curWidth: 0
            }
        },
        props: ['quest', 'quantInRow'],
        computed: {
            quantInRowNew() {
                return Number(100 / this.$props.quantInRow).toFixed(5) + '%'
            }
        },
        methods: {
            onSwitch: function (e) {
                switch (e.target.className.toUpperCase()) {
                    case 'FIELD-ICON-CHECK': {
                        this.$parent.$parent.typePage = 'PAGE_OF_DATA';
                        break;
                    }
                    case 'FIELD-ICON-DELETE': {
                        this.$parent.$parent.typePage = 'PAGE_OF_DATA';
                        break;
                    }
                    case 'FIELD-ICON-DASH': {
                        this.$parent.$parent.typePage = 'PAGE_WITHOUT_DATA';
                        break;
                    }
                };
            }
        }
    }
</script>

<style>
    .current-quest {
        border: 1px solid black;
        border-right: none;
        box-sizing: border-box;
    }

    .current-quest:last-child {
        border-right: 1px solid black;
    }

    .current-quest__alias {
        padding: 5px;
        text-align: center;
        font-weight: 600;
        border-bottom: 1px solid black;
    }

    .current-quest__status {
        padding: 5px;
    }
</style>