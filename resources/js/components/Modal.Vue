<template>
  <div id="myModal" class="c-modal">
    <div class="c-modal__content">
      <span class="c-modal__close" @click="$emit('close'); email = ''">&times;</span>
      <div class="c-modal__content__wrapper">
        <div class="c-modal__content__title">
          Step 1 of 2
        </div>
        <div class="c-modal__content__caption">
          Enter Your Email To Get <span>FREE</span><br/>
          iPhone Photography Email Tips:
        </div>
        <div class="c-modal__content__email field" :class="{ error: !validEmail }">
          <input
            required
            type="email"
            id="email"
            placeholder="email"
            v-model="email"
            @blur="validateEmail(email)"
          />
          <label for="email">Please enter your email here</label>
        </div>
        <div class="c-modal__content__action">
          <button class="button">
            Send Me The Tips<span>&gg;</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',

  data() {
    return {
      email: '',
      validEmail: true,
    };
  },

  watch: {
    email(email) {
      this.validateEmail(email);
    },
  },

  methods: {
    validateEmail(email) {
      // eslint-disable-next-line
      const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      if (!email || re.test(String(email).toLowerCase())) this.validEmail = true;
      else this.validEmail = false;
      console.log('validateEmail', this.validEmail);
    },
  },
};
</script>

<style lang="scss">

.c-modal {
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 20vh;
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
  box-shadow: 0px 0px 60px rgba(0, 0, 0, 0.5);

  &__close {
      float: right;
      position: relative;
      z-index: 5;
      top: -10px;
      right: 5px;
      font-size: 38px;
      font-weight: bold;
      line-height: 46px;
      color: #464646;

      &:hover,
      &:focus {
        color: #000;
        text-decoration: none;
        cursor: pointer;
      }
  }
  
  &__content {
    max-width: 570px;
    max-height: 310px;
    background-color: #fefefe;
    margin: auto;
    padding: 11px;
    border: 1px solid #888;
    width: 50%;
    min-width: 400px;
    max-width: 600px;

    &__wrapper {
      position: relative;
      padding: 0 65px;
    }

    &__title {
      position: relative;
      width: 100%;
      padding: 18px 0 12px 0;
      font-weight: 300;
      font-size: 14px;
      line-height: 17px;
      text-align: center;
      color: #848484;

      &:after {
        content:"";
        width:100%;
        height:3px;
        left:0;
        bottom:0;
        position:absolute;
        z-index:9;
        background: linear-gradient(to right, brown 50%, #E5E5E5 50%);
      }
    }

    &__caption {
      font-weight: bold;
      font-size: 23px;
      margin: 22px auto;
      margin-bottom: 0;
      text-align: center;
      line-height: 28px;
      letter-spacing: 0.8px;
      color: #464646;

      span {
        color: green;
      }
    }

    &__email {
      display: flex;
      flex-flow: column-reverse;
      margin-bottom: 20px;

      &.error {
         label {
            color: red;
         }
         input {
            color: red;
            border: 1px solid red;
            box-shadow: inset 0px 1px 5px rgba(142, 0, 0, 0.5);
         }
       }
       input {
          font-size: 14px;
          width: calc(100% - 22px);
          border: none;
          outline: none;
          height: 40px;
          background: #fff;
          padding: 14px 10px 0 12px;
          box-shadow: inset 0px 1px 5px rgba(142, 142, 142, 0.5);

          &::placeholder {
            color: #fff
          }
          &:focus {
            outline: 0;
            &::-webkit-input-placeholder {
              opacity: 1;
            }
          }
          &:not(:placeholder-shown) + label,
          &:focus + label {
            transform: translate(5px, 1.5rem) scale(0.8);
            cursor: pointer;
          }
       }
       label {
          cursor: text;
          text-align: left;
          padding-left: 11px;
          text-transform: none;
          font-size: 14px;
          line-height: 22px;
          display: flex;
          align-items: center;
          text-align: center;
          color: #828282;;
          max-width: 66.66%;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
          transform-origin: left bottom;
          transform: translate(0, 2.5rem) scale(1.2);
       }
    }

    &__action {
      button {
        width: 100%;
        height: 48px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: bold;
        font-size: 18px;
        line-height: 22px;
        text-align: center;
        color: #FFFFFF;
        margin-bottom: 27px;
        background: linear-gradient(90deg, #AC519C 0.83%, #E5424F 100%);
        box-shadow: 0px 3px 10px rgba(104, 104, 104, 0.5);
        border: none;
        outline: none;
        span {
          font-size: 14px;
          margin-left: 5px;
        }
        &:hover {
          background: linear-gradient(90deg, #B678AA 1.29%, #E28990 100%);                        
        }

      }
    }

  }
}


label {
  font-size: 12px;
  text-align: left;
  padding-left: 11px;
  text-transform: none;
  color: #828282;
}

@media screen and (max-width: 575px) {
  .c-modal {

    &__close {
      font-size: 29px;
      line-height: 35px;
    }

    &__content {
      min-width: 285px;
      width: calc(100% - 42px);
      padding: 9px;
      &__wrapper {
        padding: 0 7px 0 11px;
      }
      &__title {
        padding: 4px 0 11px 0;
      }
      &__caption {
        margin-top: 20px;
        font-size: 20px;
        line-height: 26px;
        text-align: left;
      }
      &__action {
        .button {
          margin-bottom: 15px;
        }
      }
    }
  }
}

@media (min-width: 576px) and (max-width: 911px) {
  .c-modal {
    &__content {
      width: 80%;
    }
  }
}

label, input {
  transition: all 0.2s;
  touch-action: manipulation;
}


::-webkit-input-placeholder {
  opacity: 0;
  transition: inherit;
}

</style>
