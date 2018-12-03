<template>
    <div class="wrap">
        <div class="title">默认样式</div>
        <div class="group">
            <div>
                <icon v-for="(type, key) in types.smallDefault" :key="key" :type="type" class="small-default" />
            </div>
        </div>

        <div class="title">尺寸选择</div>
        <div class="group choose">
            <icon v-for="(size, key) in sizes" :key="key" type="success" :size="size" class="icon-size" />
        </div>

        <div class="title">颜色选择</div>
        <div class="group choose">
            <icon v-for="(color, key) in colors" :key="key" type="success" size="40" :color="color" class="icon-color" />
        </div>
    </div>
</template>

<script>
  export default {
    name: "icon",
      data() {
        return {
            types: {
                smallDefault: ['success', 'info', 'warn', 'waiting',
                    'success_no_circle', 'clear', 'search', 'personal',
                    'setting', 'top', 'close', 'cancel', 'download',
                    'checkboxSelected', 'radioSelected', 'radioUnselect']
            },
            colors: [
                '#333', '#666', '#999', '#3C76FF', '#F7534F'
            ],
            sizes: [
                40, 35, 30, 25
            ]
        }
      }
  }
</script>

<style>
    .wrap {
        font-size: .16rem;
    }
    .group {
        background: #fff;
        padding: .17rem .4rem;
    }
    icon:last-child {
        margin-right: 0;
    }
    .big-default {
        margin-right: .19rem;
    }
    .small-default {
        margin: .2rem .2rem .1rem 0;
        display: inline-block;
    }
    .small-primary {
        margin: .15rem .2rem .1rem 0;
        display: inline-block;
    }
    .default {
        height: 1.8rem;
    }
    .choose {
        height: .8367rem;
        line-height: .8rem;
    }
    .icon-color,
    .icon-size {
        margin-right: .15rem;
        line-height: 1;
    }
    @media screen and (max-width: 320px) {
        .icon-color {
            margin-right: .08rem;
        }
    }

</style>
