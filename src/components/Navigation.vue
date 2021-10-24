<template>
    <header>
        <div class="nav-1">
            <div class="container">
                <div class="nav-1-links">
                    <ul class="menu-1">
                        <router-link class="link" to="/">Shop</router-link>
                        <router-link class="link" to="/">Community</router-link>
                        <router-link class="link" to="/">Publicity</router-link>
                    </ul>
                    <ul v-show="!mobile" class="menu-2">
                        <a href="#" class="follow">Suivez-nous</a>
                        <a href="#" class="link">
                            <i class="lni lni-youtube"></i></a>
                        <a href="#" class="link">
                            <i class="lni lni-facebook-filled"></i></a>
                        <a href="#" class="link">
                            <i class="lni lni-instagram-original"></i></a>
                        <a href="#" class="link">
                            <i class="lni lni-twitter-original"></i></a>
                    </ul>
                </div>
            </div>
        </div>
        <div class="nav-2">
            <div class="container">
                <div class="branding">
                    <router-link class="header" :to="{name: 'Home'}">Winkel</router-link>
                </div>
                <div class="nav-links">
                    <ul v-show="!mobile">
                        <router-link class="link" to="/home">Accueil</router-link>
                        <router-link class="link" to="/recomm" >Nos recommendatons</router-link>
                        <router-link class="link" to="/customer">Service client</router-link>
                        <router-link class="link" to="/sell">Promotions</router-link>
                        <router-link class="link" to="/sell">Contact</router-link>
                    </ul>
                </div>
                <div class="right-links">
                    <ul v-show="!mobile">
                        <span @click="toggleSearch" class="link">
                            <i class="lni lni-search-alt"></i>
                        </span>
                        <a class="link" href="/recomm" ><span>Cart(0) | </span><i class="lni lni-cart-full"></i></a>
                        <a class="link" href="/recomm" ><i class="lni lni-user"></i></a>
                    </ul>
                </div>
                <img @click="toggleNav" v-show="mobile" class="menu-icon" src="../assets/icons/menu.svg"/>
            </div>
            <transition name="mobile-nav">
                <ul class="mobile-nav" v-show="mobileNav">
                    <router-link class="link" to="/home">Accueil</router-link>
                    <router-link class="link" to="/recomm" >Nos recommendatons</router-link>
                    <router-link class="link" to="/customer">Service client</router-link>
                    <router-link class="link" to="/sell">Vendre</router-link>
                </ul>
            </transition>
        </div>
        <div  class="nav-3">
            <div class="container d-flex justify-content-center">
                <transition name="search">
                    <form v-show="search" class="search-box">
                        <input placeholder="Rechercher un produit">
                        <i class="lni lni-search-alt"></i>
                    </form>
                </transition>
            </div>
        </div>

    </header>
</template>

<script>
    export default {
        name: "Navigation",
        data() {
            return {
                mobile: null,
                mobileNav: null,
                windownWidth: null,
                search: null
            }
        },

        created() {
            window.addEventListener('resize', this.checkScreen);
            this.checkScreen();
        },

        methods: {
            checkScreen(){
                this.windownWidth = window.innerWidth

                if (this.windownWidth <= 750) {
                    this.mobile = true;
                    return;
                }

                this.mobile = false;
                this.mobileNav = false;
                return;
            },

            toggleNav(){
                this.mobileNav = !this.mobileNav;
            },

            toggleSearch(){
                this.search = !this.search
            }
        },
    }
</script>

<style lang="scss" scoped>

    header{
        z-index: 99;
    }
    .nav-1{
        display: flex;
        background-color: #023e7d;
        height: 2.131rem;

        .nav-1-links{
            position: relative;
            display: flex;
            flex: 1;
            align-items: center;
        }

        .menu-1{
            display: flex;
            align-items: center;

            .link:hover{
                color: rgba(255, 255, 255, .5);
                font-weight: 500;
            }

            .link{
                padding: 8px 0;
                text-decoration: none;
                font-size: 0.75rem;
                font-weight: 500;
                color: #fff;
                transition:all 250ms ease-in;
            }
            a::after{
                margin: 0 15px;
                right: 0;
                top: 23%;
                content: "|";
                color: #fff;
            }

            a:last-child::after{
                content: "";
            }
        }

        .menu-2{
            display: flex;
            align-items: center;
            position: absolute;
            right: 0;

            .follow{
                margin-right: 20px;
                font-size: 12px;
                text-decoration: none;
                color: #979dac;
                pointer-events: none;
            }

            .link{
                padding-right: 15px;
                i{
                    height: 22px;
                    width: 100%;
                    color: white;
                }
                .lni-facebook-filled:hover{
                    color: blue;
                }

                .lni-youtube:hover{
                    color: red;
                }

                .lni-instagram-original:hover{
                    color: deeppink;
                }

                .lni-twitter-original:hover{
                    color: dodgerblue;
                }
            }
        }
    }
    .nav-2{
        background-color: #0353a4;
        .container{
            height: 5.2rem;
            display: flex;

            .branding{
                align-items: center;
                display: flex;
                margin-left: 3px;
                .header{
                    font-weight: 600;
                    font-size: 24px;
                    color: #fff;
                    text-decoration: none;
                }
            }

            .nav-links{
                position: relative;
                padding-top: 20px;
                display: flex;
                flex: 1;
                justify-content: center;
                align-items: center;

                ul{
                    margin-right: 10px;
                    .link{
                        margin-right: 10px;
                        text-transform: uppercase;
                        font-size: 0.8rem;
                        color: rgba(255, 255, 255, 1);
                        text-decoration: none;
                        transition:all 400ms linear;
                        padding: 12px;
                        letter-spacing: 0.5px;
                    }

                    .link:hover{
                        font-weight: 600;
                        color: antiquewhite;
                        border-bottom: #f5f7fa solid 3px;
                    }
                    .link:last-child{
                        margin-right: 0;
                    }
                }
                a{
                    &.router-link-exact-active {
                        color: antiquewhite;
                        opacity: 4;
                        border-bottom: #f5f7fa solid 3px;
                    }
                }
            }

            .right-links{
                position: relative;
                padding-top: 20px;
                display: flex;
                justify-content: flex-end;
                align-items: center;
                .link{
                    color: white;
                    text-decoration: none;
                    cursor: pointer;

                    span{
                        font-size: 15px;
                        color: white;
                        cursor: pointer;
                    }
                }

                i{
                    font-size: 18px;
                    color: #fff;
                    padding-right: 30px;
                }
            }
        }

        .menu-icon{
            cursor: pointer;
            height: 25px;
            width: auto;
            position: absolute;
            top: 63px;
            right: 25px;
        }
    }
    .nav3{
        display: flex;
        .container{
        }
    }

    .search-box{
        margin: 30px 0;
        background-color: #023e7d;
        height: 2.5rem;
        width: 80%;
        input{
            border: none;
            outline: none;
            padding: 8px 45px;
            width: 100%;
            background-color: transparent;
            color: white;
            &::placeholder{
                color: rgba(255, 255, 255, .8);
                text-transform: uppercase;
                letter-spacing: 1.5px;
                font-size: 12px;
            }
        }

        i{
            position: relative;
            font-size: 15px;
            padding: 0;
            margin: 0;
            bottom: 31px;
            left: 20px;
            color: white;
        }
    }

    .mobile-nav{
        z-index: 99;
        padding: 20px;
        width: 70%;
        max-width: 200px;
        display: flex;
        flex-direction: column;
        position: fixed;
        height: 100%;
        top: 0;
        left: 0;
        background-color: #0353a4;

        .link{
            padding: 15px 0;
            color: #fff;
            transition:all 1s ease;
            text-decoration: none;
            &:hover{
                color: antiquewhite;
                opacity: 4;
                border-bottom: #f5f7fa solid 3px;
            }
        }
        a{
            &.router-link-exact-active {
                color: antiquewhite;
                border-bottom: #f5f7fa solid 3px;
            }
        }
    }

    .mobile-nav-enter-active, .mobile-nav-leave-active{
        transition: all 1s ease;
    }

    .mobile-nav-enter{
        transform: translateX(-200px);
    }

    .mobile-nav-enter-to{
        transform: translateX(0);
    }

    .mobile-nav-leave-to{
        transform: translateX(-200px);
    }

    .search-enter-active, .search-leave-active{
        transition: all 1s ease;
    }

    .search-enter{
        transform: translateY(-70px);
    }

    .search-enter-to{
        transform: translateY(0);
    }

    .search-leave-to{
        transform: translateY(-70px);
    }
</style>