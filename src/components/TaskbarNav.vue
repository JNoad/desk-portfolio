<template>
    <nav>
        <ul>
            <li>
                <router-link></router-link>
            </li>
            <li>
                <router-link></router-link>
            </li>
            <li>
                <router-link></router-link>
            </li>
            <li>
                <router-link></router-link>
            </li>
            <li>
                <router-link></router-link>
            </li>
            <li>
                <router-link></router-link>
            </li>
        </ul>
    </nav>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
    nav {
        width: 100%;
        height: 60px;
        background-color: #222;
        box-shadow: 0 0 4px #151515;
        box-shadow: 
            inset 0 -3px 6px -2px black, 
            inset 6px 0px 6px -6px rgba(0, 0, 0, 0.8), 
            inset -6px 0px 6px -6px rgba(0, 0, 0, 0.8),
            0 -8px 3px -6px rgba(0, 0, 0, 0.85);
        ;
        ul {
            display: flex;
            justify-content: center;
            align-items: center;

            height: 100%;
            li {
                list-style: none;
                margin: 6px;
                a {
                    width: 40px; height: 40px;
                    display: block;
                    border-radius: 6px;
                    background-color: pink;

                    &:hover {
                        background-color: lightblue;
                    }
                }
            }
        }
        
    }
</style>