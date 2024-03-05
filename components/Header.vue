<template>
  <header class="header">
    <div class="top__bar">
      <div class="container">
        <div class="soc__netw">
          <a href="" class="soc__netw-link">
            <Icon name="iconoir:instagram" color="white"></Icon>
          </a>
          <a href="" class="soc__netw-link">
            <Icon name="iconoir:telegram" color="white"></Icon>
          </a>
        </div>
        <PhonesList/>
        <LocaleSwitcher />
      </div>
    </div>
    <div class="header__bot">
      <div class="container">
        <div class="logo__wrapper">
          <nuxt-link :to="localPath('/')" class="logo__link">
            <img src="../assets/img/logo.png" width="150" alt="" />
          </nuxt-link>
        </div>
        <div class="mobile__nav-btn-wrapper" style="display: none">
          <a class="mobile__nav-btn" uk-toggle href="#mobile_navigate">
            <Icon name="iconoir:menu" color="white"></Icon>
          </a>
        </div>
        <div class="nav__wrapper">
          <NavMenu></NavMenu>
        </div>
      </div>
    </div>
    <div
      id="mobile_navigate"
      class="mobile__navigate-offcanvas"
      uk-offcanvas="overlay: true; flip:true"
    >
      <div class="uk-offcanvas-bar">
        <button class="uk-offcanvas-close" type="button" uk-close></button>
        <div class="offcanvas__wrapper">
          <div class="offcanvas__head">
            <div class="offcanvas__logo">
              <img src="../assets/img/logo.png" width="70" alt="" />
            </div>
          </div>
          <div class="offcanvas__nav-wrapper">
            <NavMenu/>
          </div>
          <div class="offcanvas__phones">
            <PhonesList/>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
<script setup>
import PhonesList from "~/components/PhonesList.vue";

const localPath = useLocalePath();
</script>
<style lang="scss">
.header {
  .mobile__navigate-offcanvas {
    &::before {
      background: rgba($color: $main-color, $alpha: 0.4);
      backdrop-filter: blur(2px);
    }
    .uk-offcanvas-close {
      color: $main-color;
    }
    .uk-offcanvas-bar {
      background-color: white;
      padding: 15px;
      .offcanvas__head {
        padding-bottom: 25px;
        margin-bottom: 25px;
        border-bottom: 1px solid $main-color;
        .offcanvas__logo {
          img {
            filter: drop-shadow(5px 5px 5px #5b60ac);
          }
        }
      }
      .offcanvas__nav-wrapper{
        padding-bottom: 25px;
        margin-bottom: 25px;
        border-bottom: 1px solid $main-color;
        .nav__menu{
          flex-direction: column;
          align-items: flex-start;
        }
      }
      .offcanvas__phones{
        .phones{
          display: flex;
          flex-direction: column;
          gap: 15px;
          .phone{
            color: $main-color !important;
            svg{
              path{
                fill: $main-color;
              }
            }
          }
        }
      }
    }
  }
  .top__bar {
    padding: 5px 0;
    color: white;
    background-color: $main-color;

    .container {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    a {
      svg {
        width: 20px;
        height: 20px;

        path {
          transition: 0.3s;
        }
      }

      &:hover {
        svg {
          path {
            stroke: $hover-color;
          }
        }
      }
    }

    .soc__netw {
      display: flex;
      align-items: center;
      gap: 5px;
      width: fit-content;

      .soc__netw-link {
        padding: 5px;
      }
    }

    .phones {
      display: flex;
      align-items: center;

      svg {
        margin-right: 5px;
        width: 18px;
      }

      .phone {
        color: white;
        font-size: 16px;
        transition: 0.3s;
        font-weight: 300;
        &:hover {
          color: $hover-color !important;
        }
      }
    }
  }
  .header__bot {
    padding: 15px 0;
    .container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      .logo__wrapper {
        .logo__link {
          img {
            filter: drop-shadow(5px 5px 5px $main-color);
          }
        }
      }
    }
  }
}
@media screen and (max-width: $breakpoint-md) {
  .header {
    .mobile__navigate-offcanvas {
    }
    .top__bar {
      .phones {
        display: none;
      }
    }
    .header__bot {
      .container .logo__wrapper .logo__link img {
        max-width: 100px;
      }
      .nav__wrapper {
        display: none;
      }
      .mobile__nav-btn-wrapper {
        display: block !important;
        .mobile__nav-btn {
          display: flex;
          width: 30px;
          height: 30px;
          align-items: center;
          justify-content: center;
          background-color: transparent;

          svg {
            width: 30px;
            height: 30px;
            border-radius: 5px;
            color: $main-color !important;
          }
        }
      }
    }
  }
}
</style>
