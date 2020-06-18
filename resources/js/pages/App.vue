<template>
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
            <button class="button" @click="modal = true">Send Me The Tips</button>
        </section>
      </div>
    </div>

    <footer>Footer</footer>

  </div>
</template>

<script>

export default {
  name: 'home',

  data() {
    return {
        title: '10 Best Photo Apps For Incredible iPhone Photography (2020 Edition)',
        caption: '<p>How do you capture more interesting travel photos with your iPhone? How do you avoid taking the same cliche vacation photos that everyone else takes? I recently interviewd Steffen Geldner - a talented iPhone photographer with a passion for travel. In this article, Steffen reveals 7 tips for shooting beautiful travel photos that will preserve the amazing memories of your trip. Read on to discover how to take better travel photos with your iPhone!</p>',
        content: [
            {
                title: 'Research Your Destination To Find The Best Photo Opportunities',
                description: '<p>Before your trip, I recommend researching the destination to find the most interesting photo opportunties</p><p>I always research the location I\'m travelling to. I do this extensively and obsessively!</p><p>So, what kind of research can you do?</p><p>First, you could serach for photos that other people have taken at the locations you\'re planning to visit.</p>',
            },
            {
                title: 'Capture Your Journey To Tell The Complete Story Of Your Travels',
                description: '<p>Travel photography isn\'t just about photographing the destination.</p><p>For a more complete photograph story, capture your journey to and from the location you\'re visiting</p><p>If you are travelling by plane, try to get a window sear where you have a view of the wing o propeller.</p><p>And of course, you could capture a beautiful aerial view of clouds, mountains, or city lights as you\'re flying above.</p>',
            },
        ],
        modal: false,
    };
  },
};
</script>

<style lang="scss">

.c-blog {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding: 75px 50px 0px 50px;
    font-family: Lato;
    font-style: normal;
    color: #101010;

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
            width: 270px;
            margin: 0 70px;
            h4 {
                padding: 8px 0;
                font-weight: bold;
                font-size: 18px;
                line-height: 22px;

            }
            &__section {
                width: 100%;
                background: #F5F5F5;
                min-height: 700px;
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

.section {
    font-family: Lato;
    font-style: normal;
    font-weight: 300;
    font-size: 16px;
    line-height: 24px;

    color: #101010;
}


footer {
  grid-column: span 3;
  padding: 30px;
  text-align: center;
  font-size: 1.4em;
  color: white;
}
</style>
