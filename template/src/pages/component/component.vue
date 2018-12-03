<template>
    <div class="group">
        <div class="group-hd">
            <img class="group-logo" src="../../images/component_logo.png" />
            <div class="group-desc">以下将展示小程序官方组件能力，组件样式仅供参考，开发者可根据自身需求自定义组件样式。</div>
        </div>

        <div v-for="(item, index, key) in items" class="group-bd" :key="key">
            <div class="item border-bottom" @click="toggleClick" :data-index="index" :data-id="item.id">
                <img class="item-logo" :src="item.icon" />
                <span class="item-desc">\{{item.name}}</span>
                <img v-if="item.id" class="item-logo item-toggle" src="../../images/right_arrow.png" />
                <img v-else class="item-logo item-toggle" :src="item.open ? '../../images/close.png' : '../../images/open.png'" />
            </div>
            <div v-if="item.open">
                <div class="sub-item border-bottom" v-for="(subItem,key) in item.list" :key="key" @click="oneItemClick" :data-id="subItem.id">
                    <span class="sub-item-desc">\{{subItem.subName}}</span>
                    <img class="item-logo sub-item-goto" src="../../images/right_arrow.png" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "component",
    data() {
        return {
            items: [{
                icon: '../../images/view.png',
                name: '视图容器',
                open: false,
                list: [{
                    subName: 'view',
                    id: 'view'
                }, {
                    subName: 'scroll-view',
                    id: 'scroll-view'
                },{
                    subName: 'movable-view',
                    id: 'movable-view'
                },{
                    subName: 'cover-view',
                    id: 'cover-view'
                }, {
                    subName: 'swiper',
                    id: 'swiper'
                }]
            }, {
                icon: '../../images/basecontent.png',
                name: '基础内容',
                open: false,
                list: [{
                    subName: 'icon',
                    id: 'icon'
                }, {
                    subName: 'text',
                    id: 'text'
                },{
                    subName: 'rich-text',
                    id: 'rich-text'
                }, {
                    subName: 'progress',
                    id: 'progress'
                }]
            }, {
                icon: '../../images/form.png',
                name: '表单组件',
                open: false,
                list: [{
                    subName: 'button',
                    id: 'button'
                }, {
                    subName: 'checkbox',
                    id: 'checkbox'
                }, {
                    subName: 'input',
                    id: 'input'
                }, {
                    subName: 'label',
                    id: 'label'
                    // }, {
                    //     subName: 'textarea',
                    //     id: 'textarea'
                }, {
                    subName: 'picker',
                    id: 'picker'
                }, {
                    subName: 'radio',
                    id: 'radio'
                }, {
                    subName: 'slider',
                    id: 'slider'
                }, {
                    subName: 'switch',
                    id: 'switch'
                }]
            }, {
                icon: '../../images/navigate.png',
                name: '导航',
                open: false,
                list: [{
                    subName: 'navigator',
                    id: 'navigator'
                }]
            }, {
                icon: '../../images/media.png',
                name: '媒体组件',
                open: false,
                list: [{
                    subName: 'audio',
                    id: 'audio'
                }, {
                    subName: 'image',
                    id: 'image'
                }, {
                    subName: 'video',
                    id: 'video'
                }]
            }, {
                icon: '../../images/location.png',
                name: '地图',
                open: false,
                list: [{
                    subName: 'map',
                    id: 'map'
                }]
            },{
                icon: '../../images/net.png',
                name: '开放能力',
                open: false,
                list: [{
                    subName: 'open-data',
                    id: 'open-data'
                }, {
                    subName: 'web-view',
                    id: 'web-view'
                }]
            }

            // {
            //     icon: '../../images/canvas.png',
            //     name: '画布',
            //     open: false,
            //     list: [{
            //         subName: 'canvas',
            //         id: 'canvas'
            //     }]
            // }
            ]
        }
    },
      created() {
        console.log('当前运行环境：' + this.getEnv())
      },
    methods: {
        oneItemClick: e => {
            console.log('oneItemClick ..')
            let viewName = e.currentTarget.dataset.id;
            duv.navigateTo({
                url: '/pages/' + viewName + '/main'
            });
        },

        toggleClick(e) {
            console.log(e)
            // // 无子项直接跳转
            let apiName = e.currentTarget.dataset.id;
            if (apiName) {
                duv.navigateTo({
                    url: '/pages/' + apiName + '/' + apiName
                });
                return;
            }
            // 子项展开与收起
            let items = this.items;
            let index = e.currentTarget.dataset.index;
            items[index].open = !items[index].open;
            this.setData({
                'items': items
            });
        }
    }
  }
</script>

<style lang="scss">
.group {
    font-size: 30rpx;
}

.group-hd {
    height: 374rpx;
    padding: 0 44rpx 0 58rpx;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #fff;
}

.group-logo {
    width: 104rpx;
    height: 104rpx;
}

.item-logo {
    width: 52rpx;
    height: 52rpx;
}

.group-desc {
    text-align: center;
    color: #999;
    margin-top: 28rpx;
    line-height: 1.6;
}

.group-bd {
    border-top: 7px solid #f5f5f5;
    background: #fff;
}

.group-bd:last-child {
    border-bottom: 7px solid #f5f5f5;
}

.item {
    padding: 34rpx 46rpx 34rpx 60rpx;
    position: relative;
    display: flex;
    align-items: center;
}

.item-close:after {
    height: 0;
}

.item-logo {
    display: inline-block;
}

.item-desc {
    font-size: 34rpx;
    margin-left: 36rpx;
}

.item-toggle {
    position: absolute;
    right: 46rpx;
}

.sub-item {
    position: relative;
    margin-left: 150rpx;
    padding: 25rpx 0;
    display: flex;
    align-items: center;
}

.sub-item:last-child:after {
    height: 0;
}

.sub-item-goto {
    position: absolute;
    right: 46rpx;
}

.sub-item-desc {
    color: #666;
}

</style>
