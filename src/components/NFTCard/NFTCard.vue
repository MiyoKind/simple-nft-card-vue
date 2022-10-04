<template>
  <div class="card">
    <div class="card__product-img">
      <img
        class="card__img"
        alt="product-image"
        :src="require('@/static/images/' + img)"
      >
    </div>
    <div class="card__content">
      <p class="card__name">{{ name }}</p>
      <p class="card__genre" v-if="genre">{{ genre }}</p>
      <div class="card__content-bottom">
        <div class="card__price">
          <div class="icon">
            <img src="@/assets/images/nft-card/icon-ethereum.svg" alt="">
          </div>
          <p>{{ price }} ETH</p>
        </div>
        <div v-if="token" class="card__token">
          <p>{{ token }} tokens</p>
        </div>
      </div>
        <button>BUY NOW!</button>
    </div>
    <div class="card__footer">
      <div class="card__avatar">
        <img :src="require('@/static/images/' + avatar)" alt="avatar-image">
      </div>
      <p class="card__author">Creation of <span class="card__author--alt-color">{{ author }}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    song() {
      return {
        type: Object,
        default: {},
        required: true
      }
    },
    img: {
      type: String,
      default: '',
      required: true
    },
    name: {
      type: String,
      default: '',
      required: true
    },
    genre: {
      type: String,
      default: ''
    },
    id: {
      type: [String, Number],
      default: null
    },
    price: {
      type: Number,
      default: 0,
      required: true
    },
    token: {
      type: [String, Number],
      default: ''
    },
    author: {
      type: String,
      default: ''
    },
    avatar: {
      type: String,
      default: '',
    },
  }
}
</script>

<style scoped lang="scss">
.icon {
  display: flex;
}

.card {
  color: #8BACD9;
  padding: 24px;
  max-width: 402.58px;
  max-height: 465px;
  font-size: 1.5rem;
  border: 5px solid white;
  border-radius: 8px;
  box-shadow: 0 0 #8BACD9;
  transition: box-shadow 0.5s ease-in-out;
  &:hover {
    box-shadow: 10px 9px 0 3px #8BACD9;
  }
  @media screen and (min-width: 768px) {
    font-size: 1.6rem;
    height: 465px;
    width: 250px;
    padding-bottom: 32px;
  }
  .card__product-img {
    cursor: pointer;
    position: relative;
    z-index: 1;
    bottom: 10%;
    border-radius: 8px;
    box-shadow: rgba(240, 46, 170, 0.4) 0 5px, rgba(240, 46, 170, 0.3) 0 10px, rgba(240, 46, 170, 0.2) 0 15px, rgba(240, 46, 170, 0.1) 0 20px, rgba(240, 46, 170, 0.05) 0 25px;
    @mixin hoverOpacity {
      content: "";
      position: absolute;
      left: 0;
      width: 100%;
      height: 100%;
      opacity: 0;
      transition: opacity 0.25s ease-out;
    }
    &::after {
      @include hoverOpacity;
      background: no-repeat rgba(246, 71, 255, 0.5) url(../../assets/images/nft-card/play-button-svgrepo-com.svg) center;
    }
    &:hover {
      &::after {
        opacity: 1;
      }
    }
  }
  .card__content {
    display: flex;
    flex-direction: column;
    position: relative;
    bottom: 20px;
    gap: 12px;
    padding: 24px 0 16px 0;
    @media screen and (min-width: 768px) {
      gap: 16px;
      padding: 24px 0;
    }
    .card__name {
      color: white;
      margin-bottom: 5px;
      font-size: 2.2rem;
      font-weight: bold;
      cursor: pointer;
      &:hover {
        color: #00FFF8;
      }
    }
    .card__genre {
      font-size: 1.8rem;
      line-height: 2.6rem;
      font-weight: lighter;
      border-radius: 60px;
      border: 3px solid grey;
      text-align: center;
      cursor: default;
    }

    .card__content-bottom {
      display: flex;
      justify-content: space-between;
      padding-top: 4px;
      @media screen and (min-width: 768px) {
        padding-top: 6px;
      }
      > * {
        display: flex;
        align-items: center;
        gap: 8px;
        font-weight: 600;
      }
      .card__price {
        color: #00FFF8;
      }
    }
    button {
      margin-top: 10px;
      background-color: #3DD1E7;
      border: 0 solid #E5E7EB;
      box-sizing: border-box;
      color: #000000;
      display: flex;
      font-family: ui-sans-serif,system-ui,-apple-system,system-ui,"Segoe UI",Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
      font-size: 2rem;
      font-weight: 700;
      justify-content: center;
      line-height: 1.75rem;
      padding: .75rem 1.65rem;
      position: relative;
      text-align: center;
      text-decoration: none #000000 solid;
      text-decoration-thickness: auto;
      width: 100%;
      max-width: 460px;
      cursor: pointer;
      transform: rotate(-2deg);
      user-select: none;
      -webkit-user-select: none;
      touch-action: manipulation;
    }

    button:focus {
      outline: 0;
    }

    button:after {
      content: '';
      position: absolute;
      border: 1px solid #000000;
      bottom: 4px;
      left: 4px;
      width: calc(100% - 1px);
      height: calc(100% - 1px);
    }

    button:hover:after {
      bottom: 2px;
      left: 2px;
    }

    button:active {
      background-color: orange;
    }

    @media (min-width: 768px) {
      button {
        padding: .75rem 3rem;
        font-size: 1.25rem;
      }
    }

  }
  .card__footer {
    display: flex;
    align-items: center;
    border-top: 1px solid #2E405A;
    gap: 16px;
    padding-top: 16px;
    .card__avatar {
      display: flex;
      border-radius: 90px;
      border: 1px solid white;
      cursor: pointer;
      img {
        width: 33px;
      }
    }
    .card__author--alt-color {
      color: white;
      cursor: pointer;
      &:hover {
        color: #00FFF8;
      }
    }
  }
}

//Transition
.fade-enter-active,
.fade-leave-active {
    transition: 0.25s ease-out;
}
.fade-leave-to,
.fade-enter-from {
  opacity: 0;
}
</style>
