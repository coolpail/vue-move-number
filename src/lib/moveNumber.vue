<template>
    <div class="wrap" >
        <div class="move" v-for="(el, index) in arr" :key="index" :style="{transform: `translate3d(0, -${Number(el[0]) * 100}%, 0)`, width: `${width}`, height: `${height}`}">
            <div :style="styleObject" v-for="(item, dex) in el[1]" :key="dex" >
                {{ dex }}
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "moveNumber" ,
    data () {
        return {
            styleObject: {
                width: this.width,
                height: this.height,
                textAlign: "center"
            }
        }
    },
    props: {
        number: {
            type: Number,
            default: 0
        },
        width: {
            type: String
        },
        height: {
            type: String
        }
    },
    computed: {
        arr () {
            let ar = String(this.number).split("")
            const len = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
            ar = ar.map(el => {
                    if(el == 0) {
                        return [].concat([el], [len.slice(0)]) 
                    }else {
                        return [].concat([el], [len.slice(0, (Number(el) + 1))])
                    }
                }
            )
            return ar
        }
    }
}
</script>
<style>
.wrap {
    display: flex;
    overflow: hidden;
}
.move {
    transition: transform 1s;
}
</style>


