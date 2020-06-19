<template>
  <div class="container">
    <div class="c-blog">
        <div class="c-blog__header">
        <div class="c-blog__header__title">{{ title }}</div>
        </div>
        <div class="c-blog__main">
        <div class="c-blog__main__content">
            <section class="c-blog__main__content__section" v-html="caption">
            </section>

            <section class="c-blog__main__content__section">
                <picture>
                    <source srcset="../assets/26226_travel-photos.svg" media="(min-width: 768px)">
                    <img srcset="../assets/26226_travel-photos.svg" alt="…">
                </picture>
            </section>

            <section class="c-blog__main__content__section"
                v-for="(cont, index) in content"
                :key="index"
            >
                <h4>{{ `${index + 1}. ${cont.title}` }}</h4>
                <div v-html="cont.description"></div>
            </section>
        </div>
        <div class="c-blog__main__aside">
            <section class="c-blog__main__aside__section">
                <button class="button" @click="showModal()">Send Me The Tips</button>
            </section>
        </div>
        </div>

        <footer></footer>

        <Modal v-show="modal" @close="modal = false" />
    </div>
  </div>
</template>

<script>
import Modal from '../components/Modal.vue';


export default {
  name: 'home',

  components: {
    Modal,
  },

  data() {
    return {
        title: '10 Best Photo Apps For Incredible iPhone Photography (2020 Edition)',
        caption: '<p>How do you capture more interesting travel photos with your iPhone? How do you avoid taking the same cliche vacation photos that everyone else takes? I recently interviewd Steffen Geldner - a talented iPhone photographer with a passion for travel. In this article, Steffen reveals 7 tips for shooting beautiful travel photos that will preserve the amazing memories of your trip. Read on to discover how to take better travel photos with your iPhone!</p>',
        content: [
            {
                title: 'Research Your Destination To Find The Best Photo Opportunities',
                description: '<p>Before your trip, I recommend researching the destination to find the most interesting photo opportunties</p><p>I always research the location I\'m travelling to. I do this extensively and obsessively!</p><p>It\'s up to you how much research you do. But you should definitely spend a bit of time looking up some great places to take pictures.</p><p>So, what kind of research can you do?</p><p>First, you could serach for photos that other people have taken at the locations you\'re planning to visit.</p><p>Search on Instagram on Google to get an idea of the kinds of photos people take there.</p>',
            },
            {
                title: 'Capture Your Journey To Tell The Complete Story Of Your Travels',
                description: '<p>Travel photography isn\'t just about photographing the destination.</p><p>For a more complete photograph story, capture your journey to and from the location you\'re visiting.</p><p>If you \'re travelling by plane, try to get a window sear where you have a view of the wing or propeller.</p><p>And of course, you could capture a beautiful aerial view of clouds, mountains, or city lights as you\'re flying above.</p><p>Your journey will often involve several different types of transport. And they all offer great phot opportunities.</p><p>Whether you \'re traveling by car, taxi, bus, train, boat, or plane, try to capture some interesting photos.</p>',
            },
        ],
        modal: false,
    };
  },
  methods: {
      showModal() {
          console.log("sdfsdfsdf")
          this.modal = true
          console.log(this.moda)
      }
  }
};
</script>

<style lang="scss">
body {
    font-family: Lato;
    font-style: normal;
    color: #101010;
    width: 100vw;
    margin: 0;
    // overflow: hidden;
}

.container {
    margin: 0 auto;
    width: 1000px;
}

.c-blog {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding: 75px 50px 0px 50px;


    &__header {
        max-width: 560px;

        &__title {
            position: relative;
            padding: 16px 0;
            font-weight: bold;
            font-size: 26px;
            line-height: 31px;
            z-index: 1;
            
            &:before {
                content: " ";
                background-image: linear-gradient(90deg, #AC519C 0.83%, #E5424F 100%);
                width: 100%;
                height: 1px;
                bottom: -1px;
                position: absolute;
                z-index: -1;
            }
        }
    }

    &__main {
        display: flex;
        &__content {
            max-width: 560px;
            padding: 35px 0;
            &__section {
                font-weight: 300;
                font-size: 16px;
                line-height: 24px;

                img {
                    padding: 16px 0;
                    width: 100%;
                }
                h4 {
                    padding: 23px 0;
                    font-weight: bold;
                    font-size: 18px;
                    line-height: 22px;
                }
            }
        }
        &__aside {
            margin-left: 70px;
            h4 {
                padding: 8px 0;
                font-weight: bold;
                font-size: 18px;
                line-height: 22px;

            }
            &__section {
                max-width: 270px;
                background: #F5F5F5;
                min-height: 640px;
                justify-content: center;
                padding: 50px 25px 0 25px;

                .button {
                    font-family: Lato;
                    font-style: normal;
                    font-weight: bold;
                    font-size: 15px;
                    line-height: 18px;
                    text-align: center;
                    color: #FFFFFF;
                    width: 220px;
                    height: 40px;
                    font-size: 12px;
                    border: none;
                    outline: none;
                    background: linear-gradient(90deg, #AC519C 0.83%, #E5424F 100%);
                    box-shadow: 0px 3px 10px rgba(104, 104, 104, 0.5);
                    &:hover {
                        background: linear-gradient(90deg, #B678AA 1.29%, #E28990 100%);                        
                    }
                }
            }
        }
    }
}


footer {
  padding-bottom: 138px;
  text-align: center;
  font-size: 1.4em;
  color: white;
}

@media screen and (max-width: 640px) {

    .container {
        width: 100vw;
    }

    .c-blog {
        padding: 0px 18px 0px 17px;
        &__header {
            &__title {
                padding: 25px 0;
            }
        }
        &__main {
            display: block;
            &__content {
                padding-top: 12px;
                &__section {
                    img {
                        width: 100vw;
                        margin: 0 -18px;
                    }
                }
            }
            &__aside {
                margin: 0;
                &__section {
                    display: flex;
                    width: 100%;
                    max-width: calc(100% - 55px);
                    min-height: 426px;
                    padding: 34px 28.5px 0 28.5px;
                    .button {
                        margin: 0 auto;
                        width: 100%;
                    }
                }
            }
        }
    }
    footer {
        padding-bottom: 37px;
    }
}
@media (min-width: 641px) and (max-width: 767px) {
    .container {
        width: 100vw;
    }
    .c-blog {
        padding: 0px 18px 0px 17px;
        &__header {
            margin: 0 auto 0 20px;
            &__title {
                padding: 25px 0;
            }
        }
        &__main {
            display: block;
            margin: 0 auto 0 20px;
        
            &__aside {
                margin: 0;
                &__section {
                    display: flex;
                    justify-content: center;
                    min-height: 426px;
                    margin: 0 auto;
                }
            }
        }
    }
}
@media (min-width: 768px) and (max-width: 940px) {
    .container {
        width: 100vw;
    }

    .c-blog {
        padding: 0px 18px 0px 17px;
        &__header {
            margin: 0 auto 0 70px;
            &__title {
                padding: 25px 0;
            }
        }
        &__main {
            display: block;
            margin: 0 auto 0 70px;
        
            &__aside {
                margin: 0;
                &__section {
                    display: flex;
                    justify-content: center;
                    min-height: 426px;
                    margin: 0 auto;
                }
            }
        }
    }
}
@media (min-width: 941px) and (max-width: 1024px) {
    .c-blog {
        padding: 0px 18px 0px 17px;
        max-width: 900px;
        margin: 0 auto;
        &__header {
            &__title {
                padding: 25px 0;
            }
        }
        &__main {
            &__content {
                padding-top: 12px;
            }
        }

    }
}
</style>
