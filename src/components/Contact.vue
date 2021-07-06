<template>
    <div id="contact" class="content contact"> <!-- 元素id与配置文件中anchor.id一致 -->
        <!-- 标题 -->
        <ModuleHeader :title="contact.header.title" :sub-title="contact.header.subtitle"/>
        
        <!-- 自定义内容 -->
        <p>地址：北京市怀柔区雁栖经济开发区雁栖东二路5号中科院电子所四室</p>
        <p>邮编：101407</p>
        <p>邮箱：lwenxin@mail.ie.ac.cn</p>

        <div class="m-part">
            <h3 class="title">高德地图</h3>
            <mapDrag @drag="dragMap" class="mapbox"></mapDrag>
            <ul class="info">
            <li><span>经度：</span>{{ dragData.lng }}</li>
            <li><span>纬度：</span>{{ dragData.lat }}</li>
            <li><span>地址：</span>{{ dragData.address }}</li>
            <li><span>最近的路口：</span>{{ dragData.nearestJunction }}</li>
            <li><span>最近的路：</span>{{ dragData.nearestRoad }}</li>
            <li><span>最近的POI：</span>{{ dragData.nearestPOI }}</li>
            </ul>
        </div>
        
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import ModuleHeader from '@/components/module/ModuleHeader.vue';
    import mapDrag from '@/components/mapDrag.vue'
    import {Module} from '@/api/user_interface';

    @Component({
        components: {
            ModuleHeader,
            mapDrag,
        },
        computed: {
            contact(): Module {
                // 使用getModule方法获取该模块的配置内容
                return this.$store.getters.getModule('contact');
            },
        },
    })
    export default class Contact extends Vue {
        public dragData={
                    lng: null,
                    lat: null,
                    address: null,
                    nearestJunction: null,
                    nearestRoad: null,
                    nearestPOI: null
                }
        /**
         * dragMap
data         */
        public dragMap(data:any) {
            this.dragData = {
                lng: data.position.lng,
                lat: data.position.lat,
                address: data.address,
                nearestJunction: data.nearestJunction,
                nearestRoad: data.nearestRoad,
                nearestPOI: data.nearestPOI
            }
        }
    }
</script>

<style scoped lang="scss">
    // 自定义样式
    @import '../styles/variable';

    .contact {
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

.m-part{ margin-bottom: 30px; }
.m-part::after{ content: ''; display: block; clear: both; }
.m-part .title{ font-size: 30px; line-height: 60px; margin-bottom: 10px; color: #333; }
.m-part .mapbox{ width: 600px; height: 400px; margin-bottom: 20px; float: left; }
.m-part .info{ margin: 0; padding: 0; list-style: none; line-height: 30px; margin-left: 620px; }
.m-part .info span{ display: block; color: #999; }
.m-part ol{ line-height: 40px; margin-left: 0; padding-left: 0; }
.m-part pre{ padding: 10px 20px; line-height: 30px; border-radius: 3px; box-shadow: 0 0 15px rgba(0,0,0,.5); }
.m-footer{ background: #eee; line-height: 60px; text-align: center; color: #999; font-size: 12px; }
.m-footer a{ margin:  0 5px; color: #999; text-decoration: none; }
</style>
