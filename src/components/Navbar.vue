<template>
    <div class="nav">
        <h3>{{name}}</h3>
        <div>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Projects</a></li>
                <li><a href="#">About us</a></li>
                <li><a href="#">Contact us</a></li>
                <li><a href="#">{{pro}}</a></li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default{
    props:['name','pro'],
    }
</script>


<style>
.nav{
    display: flex;
    background-color: gray;
    position: absolute;
    top: 0;
    width: 100%;
    align-items: center;
}
ul{
    display: flex;
    list-style: none;
}
li{
    margin-right: 10px;
}
h3{
    padding-left: 10px;
}
a{
    color: black;
    text-decoration: none;
}
</style>