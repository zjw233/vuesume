<template>
    <div id="team" class="content team"> <!-- 元素id与配置文件中anchor.id一致 -->
        <!-- 标题 -->
        <ModuleHeader :title="team.header.title" :sub-title="team.header.subtitle"/>
        
        <!-- 自定义内容 -->
        <a-list item-layout="horizontal">
            <a-list-item data-aos="fade-in" v-for="card in team.cards" v-bind:key="card.name + card.degree">
            <a-list-item-meta :description="card.md">
                <a slot="title">{{ card.name }}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ card.degree }}</a>
                <a-avatar slot="avatar" :src="imgSrc(card)"/>
            </a-list-item-meta>
            </a-list-item>
        </a-list>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import ModuleHeader from '@/components/module/ModuleHeader.vue';
    import {Module} from '@/api/user_interface';

    @Component({
        components: {
            ModuleHeader,
        },
        computed: {
            team(): Module {
                // 使用getModule方法获取该模块的配置内容
                return this.$store.getters.getModule('team');
            },
        },
        methods: {
            imgSrc(item) {
                return require('../assets/' + item.picture + '.jpg');
            },
            errorHandler() {
                return true;
            },
        },
    })
    export default class Team extends Vue {
    }
    
    
</script>

<style scoped lang="scss">
    // 自定义样式
    @import '../styles/variable';

    .team {
        .col {
            padding: 0 1rem;
        }

        .avatar {
            display: block;
            width: 100%;
            border-radius: 5px;
        }

        .title {
            letter-spacing: 5px;
            text-transform: uppercase;
        }

        .brief {
            display: block;
            margin: 1rem auto;
        }

        @media screen and (max-width: $--screen-md-min) {
            .col {
                padding: 0;
                &.color-content {
                    margin-top: 1.5rem;
                }
            }
        }

        .keys-row {
            margin: 1rem auto;

            .keys-col {
                margin: .5rem auto;
                word-break: break-all;
                padding-right: 1rem;

                .key {
                    margin-right: .5rem;
                    font-weight: bold;
                }

                .value {
                    color: inherit;
                    text-decoration: underline;
                }
            }
        }
    }
</style>
