<template>
    <div 
        v-if="this.open" 
        class="unusable-filter" 
    />
    <aside class="sidemenu">
        <div v-if="this.open" class="headerbox">
            <img src="../assets/logo.png"/>
            <h3>Vue.js</h3>
        </div>
        <menu-icon :left=iconLeft :size="4" @openChanged="setOpen" />
        <nav v-if="this.open" class="navpart">
            <ul class="nav-list-root">
                <nav-list-item :href="'/'" :text="'Home'">
                    <house-icon/>
                </nav-list-item>
                <nav-list-item :href="'/rowing'" :text="'Rowing'">
                    <rowing-icon/>
                </nav-list-item>
                <nav-list-item :href="'/settings'" :text="'Settings'">
                    <settings-icon/>
                </nav-list-item>
            </ul>
        </nav>
    </aside>
</template>

<script>
import HouseIcon from './icons/HouseIcon.vue';
import RowingIcon from './icons/RowingIcon.vue';
import SettingsIcon from './icons/SettingsIcon.vue';
import MenuIcon from './MenuIcon.vue';
import NavListItem from './NavListItem.vue';

export default {
  components: { MenuIcon, NavListItem, HouseIcon, RowingIcon, SettingsIcon },
    el: '#icon',
    props:{
        width: Number,
        top:Number,
        itmes:Array
    },
    data () {
        
        return {
            inactiveWidth : 0,
            btnadjust: 3,
            open : false,
            listItems: []
        }
    },
    computed:{
        menuWidth() {
            return this.open ? this.width : this.inactiveWidth
        },
        buttonOffset() {
            return this.menuWidth - this.btnadjust;
        },
        borderOffset() {
            return this.menuWidth - 20;
        },
        iconLeft () {
            return this.transformToPx(this.buttonOffset);
        },
        getMenuWidth() {
            return this.transformToPx(this.menuWidth)
        },
        getBorderOffset() {
            return this.transformToPx(this.borderOffset)
        },
        getTop(){
            return this.transformToPx(this.top)
        }
    }, methods:{
        transformToRem(i){
            return i + 'rem';
        },
        transformToPx(i){
            return i + 'px';
        },
        setOpen(open){
            this.open = open;
        },
        setItemRef(el) {
            if (el) {
                this.listItems.push(el)
            }   
        }
    }
}
</script>

<style scoped>
    h3 {
        color: white;
        font-size: x-large;
    }

    .sidemenu {
        top:v-bind(getTop);
        width: v-bind(getMenuWidth);
        left: 0;
        bottom: 0;
        height: 100%;
        margin: 0;
        background-color: #2c3e50;
        border-right: #2c3e50 solid 17px;
        display: block;
        position: fixed;
        justify-content: space-between;
        box-shadow: 2px 0px 8px #2c3e50;
    }

    .unusable-filter {
        left: v-bind(getMenuWidth);
        height: 100%;
        right: 0;
        top: 0;
        bottom: 0;
        position: fixed;
        background-color: #FFFFFFA0;
    }

    .headerbox {
        width: 80%;
        margin: auto;
    }

    .headerbox img {
        width: inherit;
    }

    .navpart {
        display: flex;
        width: 100%;
        padding: 0;
        margin-top: 15px;
    }

    .nav-list-root {
        width: 100%;
        margin: 0;
        display: list-item;
        padding: 0;
    }

</style>