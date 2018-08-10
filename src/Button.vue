<template>
    <button class="g-button" :class="{[`${iconPosition}`]: true}">
        <svg v-if="icon" class="icon"><use :xlink:href="`#icon-${icon}`"></use></svg>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>

<script>
    export default {
        name: "Button",
        props: {
            icon: {},
            iconPosition: {
                type: String,
                default: 'left',
                validator(value){
                    return value === 'left' || value === 'right'
                }
            }
        }
            //['icon', 'iconPosition']
    }
</script>

<style lang="scss">
    .g-button{
        display: inline-flex;
        justify-content: center;
        align-items: center;
        vertical-align: top;
        font-size: var(--font-size);
        height: var(--button-height);
        padding: 0 1em;
        border-radius: var(--border-radius);
        border: 1px solid var(--border-color);
        background: var(--button-bg);
        &:hover{
            border-color: var(--border-color-hover);
        }
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline: none;
        }
        &.left{
            .icon{
                margin-right: 0.3em;
            }
        }
        &.right{
            .content{
                order: 1
            }
            .icon{
                order: 2;
                margin-left: 0.3em;
            }
        }
    }
</style>