<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">
        <g-icon class="loading icon" v-if="loading" name="loading"></g-icon>
         <g-icon class="icon" v-if="icon && !loading" :name="icon"></g-icon>
         <div class="content">
            <slot></slot>
         </div>
    </button>
</template>
<script>
     export default {
        name: 'button',
        props:{
            icon:{},
            loading:{
                type:Boolean,
                default:false,
            },
            iconPosition:{
                type:String,
                default:'left',
                // validator(value){
                //     return value === 'left' || value === 'right'
                // }
            }
        }
    }
</script>
<style lang="scss">
    @keyframes spin{
        0% {transform: rotate(0deg);}
        100% {transform:rotate(360deg);}
    }
    .g-button{
        font-size:var(--font-size);
        height: var(--button-height);
        padding:0 1em; /* width */
        border-radius: var(--border-radius);
        border:1px solid var(--border-color);
        background:var(--button-bg);
        display: inline-flex;justify-self: center;align-items:center;
        vertical-align:middle;
        // line-height: 0;
        &:hover{
            border-color:var(--border-color-hover);
        }
        &:active{
            background: var(--button-active-bg);
        }
        &:focus{
            outline:none;
        }
        > .icon{
            order:1;
            margin-right: .3em;
        }
        >.content{
            order:2;
        }
        &.icon-right{
            > .icon{
                order:2;
                margin-right: 0;
                margin-left: .3em;
            }
            > .content{
                order:1;
            }
        }
        .loading{
            animation:spin 1s infinite linear;
        }
    }
</style>