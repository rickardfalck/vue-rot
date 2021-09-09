<template>
    <li class="navigation-list-item">
        <router-link :to="this.href" class="link"> 
            <div class="image-slot">
                <slot/>
            </div>
            <div>
                <p>
                    {{this.text}}
                </p>
            </div>
        </router-link>
    </li>
</template>

<script>
export default {
    props:{
        text:String,
        href:String
    },
    computed:{
        imageSource(){
            return '../assets/' + this.imgSrc;
        }
    }
}
</script>

<style scoped>
    .link {
        padding: 0;
        color: white;
        width: 100%;
        height: 100%;
        vertical-align: middle;
        display: inline-flex;
        align-content: center;
        text-decoration: unset;
        font-size: medium;
    }


    .link div {
        display: table-cell;
        vertical-align: middle;
        padding-top: 15px;
    }

    .image-slot{
        width: 50px;
        margin-left: 20px;
        margin-top: -3px;
    }

    .link p {
        height: 100%;
        margin: 0;
        padding: 0;
    }

    .navigation-list-item {
        list-style-type: none;
        width: 100%;
        height: 50px;
    }

    .navigation-list-item:hover {
        background-color: #FFFFFF0F;
    }

</style>