<template>
    <div class="main">
        <h1 class="title">10 Best Photo Apps For Incredible iPhone Photography (2020 Edition)</h1>
        <div class="container">
            <div class="description">
                <img class="divider" src="/img/divider.svg">
                <p class="description__summary">
                    How do you capture more interesting travel photos with your iPhone? How do you avoid taking the same cliché vacation photos that everyone else takes? I recently interviewed Steffen Geldner – a talented iPhone photographer with a passion for travel. In this article, Steffen reveals 7 tips for shooting beautiful travel photos that will preserve the amazing memories of your trip. Read on to discover how to take better travel photos with your iPhone!
                </p>
                <img class="travel-img" src="/img/travel-photo@3x.jpg">
                <story
                    number="1"
                    title= "Research Your Destination To Find The Best Photo Opportunities"
                    content="Before your trip, I recommend researching the destination to find the most interesting photo opportunities.<br><br>
                            I always research the location I’m traveling to.<br><br>
                            I do this extensively and obsessively!It’s up to you how much research you do.<br><br>
                            But you should definitely spend a bit of time looking up some great places to take pictures.<br><br>
                            So, what kind of research can you do?<br><br>
                            First, you could search for photos that other people have taken at the locations you’re planning to visit.<br><br>
                            Search on Instagram or Google to get an idea of the kinds of photos people take there.<br><br>"
                />
                <story
                    number="2"
                    title= "Capture Your Journey To Tell The Complete Story Of Your Travels"
                    content="Travel photography isn’t just about photographing the destination.<br><br>
                            For a more complete photographic story, capture your journey to and from the location you’re visiting.<br><br>
                            If you’re traveling by plane, try to get a window seat where you have a view of the wing or propeller.<br><br>
                            And of course, you could capture a beautiful aerial view of clouds, mountains, or city lights as you’re flying above.<br><br>
                            Your journey will often involve several different types of transport. And they all offer great photo opportunities.<br><br>
                            Whether you’re traveling by car, taxi, bus, train, boat, or plane, try to capture some interesting photos.<br><br>"
                />
            </div>
            <div class="tips">
                <button
                    @click="openModal"
                    class="tips__button"
                >
                    Send Me The Tips
                </button>
            </div>
        </div>
        <modal v-model="modalOpen" />
    </div>
</template>

<script>
import Story from './Story';
import Modal from './Modal';

export default {
    name: 'Home',
    data() {
        return {
            modalOpen: false
        }
    },
    components: {
        Story,
        Modal
    },
    mounted() {
        console.log('Component mounted.')
    },
    methods: {
        openModal() {
            this.modalOpen = !this.modalOpen;
        }
    }
}
</script>


<style scoped lang="scss">
.main {
    margin: 0 auto;
    margin-top: 76px;
    max-width: 910px;

    .title {
        max-width: 560px;
        margin-bottom: 0px;
    }
    .container {
        display: flex;
        justify-content: space-between;

        .description {
            max-width: 560px;

            img {
                max-width: 100%;
            }

            &__summary {
                margin-top: 28px;
                margin-bottom: 28px;
            }
            
            .travel-img {
                margin-bottom: 44px;
            }

        }

        .tips {
            background: #F5F5F5;
            max-width: 270px;
            max-height: 640px;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            margin-top: 16px;

            button {
                color: white;
                background: linear-gradient(90deg, #AC519C 0.83%, #E5424F 100%);
                box-shadow: 0px 3px 10px rgba(104, 104, 104, 0.5);
                margin-top: 50px;
                margin-left: 25px;
                margin-right: 25px;
                min-width: 220px;
                min-height: 40px;
                border: none;
                font-size: 15px;
                cursor: pointer;

                &:focus {
                    outline: none;
                }
            }
        }
    }

   
}

@media (max-width: 1199px) {
    .main {
        .title {
            margin: 0 auto;
            margin-top: 25px;
            padding-left: 17px;
            padding-right: 18px; 
        }
        .container {
            display: block;

            .description {
                margin: 0 auto;
            }
            
            .tips {
                margin: 0 auto;
                max-width: 560px;
                min-height: 426px;
            }
        }
    }
}

@media (max-width: 560px) {
    .main {
        .container {
            .tips {
                margin-left: 17px;
                margin-right: 18px;
            }
            .description {
                > *:not(.travel-img) {
                    padding-left: 17px;
                    padding-right: 18px; 
                }
            }
            .divider {
                width: 91%;
            }
        }
    }
}

</style>
