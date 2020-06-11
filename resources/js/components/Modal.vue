<template>
    <div class="modal" v-show="value">
        <!-- overlay -->
        <div class="modal__overlay"></div>
        
        <!-- modal -->
        <div class="modal__content">
            <div class="close" @click.prevent="close">×</div>
            <p>Step 1 of 2</p>
            <div class="slides">
                <img class="slides__line--active" src="/img/slide-line-active.svg">
                <div class="slides__line--disabled"></div>
            </div>
            <h3>Enter Your Email To Get <font>FREE</font> <br>iPhone Photography Email Tips:</h3>
            <div
                class="email"
                :class="{ 'email--invalid': invalidEmail }"
            >
                <input
                    type="email"
                    class="email__field"
                    placeholder="Please enter your email here"
                    v-model="email"
                    @focus="inputEmail"
                >
                <label for="email" class="email__label">Please enter your email here</label>
            </div>
            <button
                class="modal__tips__button"
                @click="sumbitForm"
            >
                Send Me The Tips »
            </button>
        </div>
    </div>
</template>

<script>
import validateEmail from '../validateEmail';

export default {
    name: 'Modal',
    data() {
        return {
            email: '',
            invalidEmail: false,
        }
    },
    props: {
        value: {
            required: true
        },
    },
    computed: {
        emailValidation() {
            return validateEmail(this.email);
        }
    },
    methods: {
        close() {
            this.$emit('input', !this.value);
        },
        sumbitForm() {
            this.invalidEmail = !this.emailValidation;
        },
        inputEmail() {
            this.invalidEmail = false;
        }
    }
}
</script>

<style scoped lang="scss">
.modal {
     &__overlay {
        position: fixed;
        z-index: 9998;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #262626;
        mix-blend-mode: normal;
        opacity: 0.8;
    }
    &__content {
        position: fixed;
        width: 570px;
        height: 310px;
        z-index: 9999;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        padding: 20px 30px;
        background-color: #fff;
        display: flex;
        justify-self: center;
        align-items: center;
        flex-direction: column;

        > * {
            max-width: 446px;
        }

        .close {
            position: absolute;
            top: 10px;
            right: 10px;
            cursor: pointer;
            color: #464646;
            font-size: 38px;
            line-height: 46px;
        }

        p {
            font-size: 14px;
            line-height: 17px;
            color: #848484;
        }

        .slides {
            display: flex;
            &__line--disabled {
                width: 222px;
                border: 1px solid #E5E5E5;
            }
        }

        h3 {
            line-height: 28px;
            text-align: center;
            font {
                color: #277a03;
            }
        }

        .email {
            position: relative;
            padding: 15px 0 0;
            margin-top: 10px;
            font-weight: 300;
            width: 446px;

            &__field {
                font-family: inherit;
                width: 93%;
                height: 45px;
                border: 0;
                box-shadow: inset 0px 1px 5px rgba(142, 142, 142, 0.5);
                outline: 0;
                font-size: 16px;
                line-height: 19px;
                font-weight: 300;
                color: #212121;
                padding: 15px 15px 0px 15px;
                background: transparent;
                transition: border-color 0.2s;

                &::placeholder {
                    color: transparent;
                }
                &:placeholder-shown ~ .email__label {
                    cursor: text;
                    top: 45%;
                    font-size: 18px;
                    margin-left: 15.12px;
                    font-size: 18px;
                }

                &:focus {
                    border: 1px solid #9E9E9E;
                }
            }

            &__label {
                z-index: -100;
            }

            label,
            .email__field:focus ~ .email__label {
                position: absolute;
                top: 24px;
                display: block;
                transition: 0.2s;
                font-size: 14px;
                color: #9b9b9b;
                margin-left: 15.12px;
            }

            .email__field:focus ~ .email__label {
                margin-left: 15.12px;
                color: #828282;
            }

            &.email--invalid {
                .email__field, label, .email__field:focus ~ .email__label {
                    color: #E51323;
                }
            }
        }

        .modal__tips__button {
            width: 100%;
            height: 58px;
            color: white;
            background: linear-gradient(90deg, #AC519C 0.74%, #E5424F 100%);
            box-shadow: 0px 3px 10px rgba(104, 104, 104, 0.5);
            border: none;
            font-style: normal;
            font-weight: bold;
            font-size: 18px;
            line-height: 22px;
            cursor: pointer;
            margin-top: 20px;

            &:focus {
                outline: none;
            }

            &:hover {
                background: linear-gradient(90deg, #B678AA 1.29%, #E28990 100%);
                box-shadow: 0px 3px 10px rgba(104, 104, 104, 0.5);
            }
        }
    }
}

@media (max-width: 767px) {
    .modal {
        &__content {
            width: 355px;
            height: 272px;
            padding: 13px 18px;
        }
        .close {
            position: absolute;
            top: 1px;
            right: 9px;
            cursor: pointer;
            color: #464646;
            font-size: 29px;
            line-height: 35px;
        }
        .slides__line {
            &--active, &--disabled {
                width: 163px;
            }
        }

        h3 {
            font-style: normal;
            font-weight: bold;
            font-size: 20px;
            line-height: 26px;
            text-align: center;
            margin-bottom: 0px;
            font {
                color: #277a03;
            }
        }

        .email {
            width: 320px;
        }

        .modal__tips__button {
            width: 320px;
            height: 45px;
            margin-top: 16px;
        }
    }
}
</style>
