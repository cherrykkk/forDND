<template>
    <div>
        <v-touch @swipeup='fold()' >
            <div @click='unfold()'>
                <slot name='brief'></slot>    
            </div>
            <div :class="['more',[briefView? 'fold':'unfold']]">
                <slot name='detail'></slot>
            </div>
        </v-touch>
    </div>
</template>

<script>

export default{
    data(){
        return {
            briefView:true
        }
    },
    methods:{
        unfold(){
            this.briefView = false
        },
        fold(){
            this.briefView = true
        },
        changeFold(){
            this.briefView = !this.briefView
            console.log("changefold")
        }
    }
}
</script>


<style scoped>
.more{
    overflow: hidden;
    transition: 0.5s 0s;
}
.fold{
    max-height:0;
}
.unfold{
    max-height: 200px;
}
</style>