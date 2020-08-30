<template>
    <main class="main">
            <div 
                class="option"
                :class="{load: item.type == 'load'}"
                v-for="(item, index) in questionList" :key="index"
                v-show="index == views && item.type !== 'load'" 
            >
                <p 
                    class="option__text" 
                    v-if="views == 0"
                >
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum necessitatibus 
                </p>
                
                <p 
                    class="option__text--bold"
                    :class="{bottom: item.type == 'date'}" 
                    v-text="item.question"
                >
                </p>

                <div class="container">
                    <label v-if="item.type == 'date'" @change="checkBirth">
                        <select class="option__select day" type="text" v-model="pickedDay">
                            <option disabled value>Day</option>
                            <option v-for="day in days" :value="day">{{day}} </option>
                        </select>
                    </label>

                    <label v-if="item.type == 'date'" @change="checkBirth">
                        <select class="option__select month" type="text" v-model="pickedMonth">
                            <option disabled value>Month</option>
                            <option v-for="month in months" :value="month">{{month}}</option>
                        </select>
                    </label>

                    <label v-if="item.type == 'date'" @change="checkBirth">
                        <select class="option__select year" type="text" v-model="pickedYear">
                            <option disabled value>Year</option>
                            <option class="text__center" v-for="year in years" :value="year">{{year}}</option>
                        </select>
                    </label>
                </div>

                <button
                    :class="{left: !isView, center: isView, active: answer.id == id}" 
                    @click="click(answer)" 
                    v-for="answer in item.answers" 
                    :key="answer.id" 
                    v-text="answer.answer"
                    v-if="item.type == 'radio'" 
                >
                </button>

                <button 
                    class="option__button"
                    :class="{top: !isTop}" 
                    v-show="isClick == true && views !== 0" 
                    @click="next(item)"
                >
                    Next
                </button>

                <div 
                    class="option__alarm"
                    :class="{top: !isTop}" 
                    v-show="isChecked == false && isClick == false && item.type !== 'load'"
                >
                    Please, answer the question!
                </div>
            </div>

            <div 
                class="load"
                v-if="questionList.length - 1  == views"
            >
                <p class="load__time">{{time}}%</p>

                <div class="load__text" v-show="time > 0">
                    <div class="text-ff">
                        Lorem ipsum dolor sit amet
                        <span class="dot">......................................</span> 
                    </div>
                    <span class="text-b5">Finish!</span>
                </div>

                <div class="load__text" v-show="time > 20">
                    <div class="text-ff">
                        Lorem ipsum dolor sit amet
                        <span class="dot">......................................</span> 
                    </div>
                    <span class="text-b5">Finish!</span>
                </div>

                <div class="load__text" v-show="time > 40">
                    <div class="text-ff">
                        Lorem ipsum dolor sit amet
                        <span class="dot">......................................</span> 
                    </div>
                    <span class="text-b5">Finish!</span>
                </div>

                <div class="load__text" v-show="time > 60">
                    <div class="text-ff">
                        Lorem ipsum dolor sit amet
                        <span class="dot">...............................................</span> 
                    </div>
                    <span class="text-b5">Finish!</span>
                </div>

                <div class="load__text" v-show="time > 80">
                    <div class="text-ff">
                        Lorem ipsum dolor sit amet
                        <span class="dot">........................................................................................</span> 
                    </div>
                    <span class="text-b5">Finish!</span>
                </div>

                <p class="load__text--bold" v-show="time == 100">Done!</p>
            </div>

            <div 
                class="finish" 
                v-if="questionList.length == views"
            >
                <p class="finish__text"> Lorem ipsum dolor sit</p>

                <p class="finish__text--red">Congratulations!!</p>

                <p class="finish__text--bold">Lorem ipsum dolor sit amet consectetur adipisicing elit. </p>

                <p class="finish__text--border">
                    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Explicabo, excepturi vitae? 
                    Ipsum aspernatur error doloribus eaque expedita assumenda quam? Distinctio tempore 
                    minus exercitationem provident cumque earum fugiat incidunt, dolorum dicta?
                </p>

                <a 
                    class="finish__link" 
                    href="tel:xxxxxxxxx"
                >
                    Call and listen
                </a>
            </div>
    </main>
</template>

<script>
export default {
    data: () => ({
        views: 0,
        isView: true,
        isClick: true,
        isChecked: false,
        isTop: false,
        id: null,
        days: null,
        months: null,
        years: null,
        pickedMonth: "",
        pickedDay: "",
        pickedYear: "",
        time: 0,
        questionList :  [
            {
                question: 'Lorem:',
                answers: [
                    {
                        id: 1,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 2,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum?',
                answers: [
                    {
                        id: 3,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 4,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 5,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 6,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum',
                answers: [
                    {
                        id: 7,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 8,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 9,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 10,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum',
                answers: [
                    {
                        id: 11,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 12,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 13,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum',
                answers: [
                    {
                        id: 14,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 15,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 16,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 17,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum',
                answers: [
                    {
                        id: 18,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 19,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 20,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 21,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum',
                answers: [
                    {
                        id: 22,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 23,
                        answer: 'Lorem',
                        active: false
                    },{
                        id: 24,
                        answer: 'Lorem',
                        active: false
                    }
                ],
                type: 'radio'
            },
            {
                question: 'Lorem ipsum:',
                type: 'date'
            },
            {
                type: 'load'
            }
        ]
    }),
    props: {
        footer: Number
    },
    methods: {
        click(answer) {
            if(this.views == 0) {
                ++this.views;
            }
            else {
                this.id = answer.id;
                this.isChecked = true;
                this.isClick = true;
            }
        },
        next(item) {
            if (this.isChecked == false) {
                this.isChecked = false;
                this.isClick = false;
            }
            else if (item.type == 'radio' && this.isChecked == true && this.isClick == true) {
                ++this.views;
                this.isChecked = false;
                this.isView = false;
                this.isTop = true;
            }
            else if (item.type !== 'radio' && this.isChecked == true && this.isClick == true) {
                ++this.views;
                this.isChecked = false;
                this.timer();
                clearInterval(20000);
            }
        },
        timer() {
            let loader = setInterval(() => {
                if(this.time < 100) {
                    ++this.time; 
                }
                else {
                    setTimeout(() => {
                        this.views = this.questionList.length;
                        this.$emit('finish', this.views);
                    }, 1000);
                    clearInterval(loader);
                }
            }, 100);
        },
        checkBirth() {
            this.invalid = false;
            if (this.pickedMonth && this.pickedDay && this.pickedYear) {
                this.isClick = true;
                this.isChecked = true;
            } else {
                this.isClick = false;
                this.isChecked = false;
            }
        },
        genBirthDay(min, max) {
            let array = [];
            for (let i = min; i <= max; i++) {
                array.push(i);
            }
            return array;
        }
    },
    mounted() {
        this.days = [...this.genBirthDay(1, 31)];
        this.months = this.genBirthDay(1, 12);
        this.years = this.genBirthDay(
        1960,
        new Date().getFullYear() - 18
        ).reverse();
    }
}
</script>

<style lang="scss">
    .main {
        position: relative;
        width: 100%;
        z-index: 2;

        .option {
            width: 100%;
            display: flex;
            flex-direction: column;
            flex-wrap: nowrap;
            align-items: center;

            .container {
                width: 100%;

                label {
                    position: relative;
                    margin: 0 auto;
                    margin-top: 16px;
                    width: 70%;
                    display: flex;
                    justify-content: center;
                }

                label::before {
                    content: " ";
                    position: absolute;
                    top: 45%;
                    right: 22px;
                    width: 12px;
                    height: 8px;
                    background-image: url(../assets/image/arrow-bottom.svg);
                    background-repeat: no-repeat;
                    background-size: cover;
                    z-index: 2;
                }
            }

            .option__text {
                width: 95%;
                text-align: center;
                margin-top: 12px;
                font-weight: 500;
                font-size: 18px;
                line-height: 16px;
                color: #FFFFFF;
            }

            .option__select {
                font-weight: 500;
                font-size: 14px;
                line-height: 16px;
                padding-left: 14px;
                color: #2D132C;
                background-color: #FFFEFE;
                border: 1px solid #2D132C;
                box-sizing: border-box;
                border-radius: 36px;
                width: 100%;
                height: 8vmax;
                appearance: none;
                cursor: pointer;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }
            }

            .option__text--bold {
                margin-top: 24px;
                margin-bottom: 5px;
                text-align: center;
                padding: 0 16px;
                font-weight: bold;
                font-size: 19px;
                line-height: 20px;
                letter-spacing: -0.01em;
                color: #FFFFFF;
                width: 100%;
            }

            .center {
                margin-top: 16px;
                width: 70%;
                height: 8vmax;
                background-color: #FFFEFE;
                border: 1px solid #2D132C;
                border-radius: 36px;
                font-weight: 500;
                font-size: 14px;
                line-height: 16px;
                color: #2D132C;
                cursor: pointer;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }
            }

            .bottom {
                margin-bottom: 16px;
            }

            .left {
                width: 70%;
                height: 8vmax;
                margin-top: 16px;
                padding-left: 14px;
                background-color: #FFFEFE;
                border: 1px solid #2D132C;
                border-radius: 36px;
                font-style: normal;
                font-weight: 500;
                font-size: 14px;
                line-height: 16px;
                text-align: left;
                cursor: pointer;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }
            }

            .active {
                position: relative;
                background-color: #ee8d8d;
            }

            .option__button {
                margin-top: 22px;
                width: 80%;
                height: 8vmax;
                background-color: #EE4540;
                border: 1px solid #EE4540;
                border-radius: 10px;
                font-weight: bold;
                font-size: 18px;
                line-height: 21px;
                color: #FFFFFF;
                cursor: pointer;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }

                @media(min-height: 1200px) {
                    margin-top: 100%;
                }

                @media(max-height: 1200px) {
                    margin-top: 300px;
                }

                @media(max-height: 1000px) {
                    margin-top: 150px;
                }

                @media(max-height: 800px) {
                    margin-top: 150px;
                }

                @media(max-height: 700px) {
                    margin-top: 100px;
                }

                @media(max-height: 600px) {
                    margin-top: 24px;
                }
            }

            .option__alarm {
                width: 80%;
                height: 8vmax;
                margin-top: 22px;
                background-color: #EEEEEE;
                border: 1px solid #EE4540;
                border-radius: 10px;
                font-weight: bold;
                font-size: 18px;
                line-height: 21px;
                color: #EE4540;
                display: flex;
                justify-content: center;
                align-items: center;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }

                @media(min-height: 1200px) {
                    margin-top: 100%;
                }

                @media(max-height: 1200px) {
                    margin-top: 300px;
                }

                @media(max-height: 1000px) {
                    margin-top: 150px;
                }

                @media(max-height: 800px) {
                    margin-top: 150px;
                }

                @media(max-height: 700px) {
                    margin-top: 100px;
                }

                @media(max-height: 600px) {
                    margin-top: 24px;
                }
            }
        }

        .load {
            padding: 62px 16px 0 16px;

            .load__text {
                display: flex;
                font-weight: 500;
                font-size: 14px;
                line-height: 16px;
                width: 100%;

                .dot {
                    color: white;
                }

                .text-ff {
                    width: 84%;
                    color:  #ffa6a6;
                    font-family: "Roboto";
                    overflow: hidden;
                    white-space: nowrap;
                    text-overflow: ellipsis;
                }

                .text-b5 {
                    color: #b5ffb3;
                    font-family: "Roboto";
                }
            }

            .load__text--bold {
                width: 100%;
                text-align: center;
                margin-top: 97px;
                font-weight: bold;
                font-size: 18px;
                line-height: 21px;
                color: #EE4540;
            }

            .load__time {
                width: 100%;
                text-align: center;
                font-size: 32px;
                color: white;
            }
        }

        .finish {

            .finish__text {
                margin-top: 12px;
                padding-left: 16px;
                width: 100%;
                text-align: center;
                font-weight: 500;
                font-size: 19px;
                line-height: 20px;
                color: #F1F0F0;
            }

            .finish__text--red {
                text-align: center;
                margin-top: 24px;
                font-weight: 500;
                font-size: 24px;
                line-height: 28px;
                color: #EE4540;
                text-shadow: 0px 4px 5px rgba(0, 0, 0, 0.25);
                animation-name: puls;
                animation-duration: 1s;
                animation-iteration-count: infinite;
                animation-timing-function: linear;
            }

            .finish__text--bold {
                margin: 0 auto;
                margin-top: 5px;
                width: 208px;
                font-weight: 500;
                font-size: 24px;
                line-height: 28px;
                color: white;
            }

            .finish__text--border {
                margin: 0 auto;
                margin-top: 40px;
                width: 90%;
                padding: 14px;
                text-align: center;
                font-weight: 500;
                font-size: 14px;
                line-height: 16px;
                color: #FFFFFF;
                background-color: rgba(0, 2, 43, 0.8);
                border: 1px solid #FBE311;
                backdrop-filter: blur(4px);
            }

            .finish__link {
                position: relative;
                margin: 0 auto;
                margin-top: 24px;
                display: flex;
                justify-content: center;
                align-items: center;
                width: 90%;
                height: 8vmax;
                background-color: #EE4540;
                border: 1px solid #FFFFFF;
                border-radius: 10px;
                font-family: Roboto;
                font-weight: bold;
                font-size: 18px;
                line-height: 21px;
                color: #FFFFFF;
                text-decoration: none;
                text-align: right;
                animation-name: pulse;
                animation-duration: 1.5s;
                animation-iteration-count: infinite;
                animation-timing-function: linear;

                @media (max-width: 320px) {
                    height: 44px;
                }

                @media (min-width: 414px) {
                    height: 56px;
                }

                @media(min-height: 1200px) {
                    margin-top: 100%;
                }

                @media(max-height: 1200px) {
                    margin-top: 300px;
                }

                @media(max-height: 1000px) {
                    margin-top: 150px;
                }

                @media(max-height: 800px) {
                    margin-top: 150px;
                }

                @media(max-height: 700px) {
                    margin-top: 100px;
                }

                @media(max-height: 600px) {
                    margin-top: 24px;
                }

            }

            .finish__link::before {
                content: " ";
                position: relative;
                right: 4%;
                background-image: url(../assets/image/phone.svg);
                background-repeat: no-repeat;
                background-size: cover;
                width: 24px;
                height: 24px;
                animation-name: call;
                animation-duration: 1.5s;
                animation-iteration-count: infinite;
                animation-timing-function: linear;
            }
        }

        @keyframes puls {
            0% {
                font-size: 24px;
            }

            50% {
                font-size: 32px;
            }

            100% {
                font-size: 24px;
            }
        }

        @keyframes call {
            0% {
                transform: scaleX(1);
            }

            10%, 20% {
                transform: scale3d(.9, .9, .9) rotate(-3deg)
            }
            30%, 50%, 70%, 90% {
                transform: scale3d(1.1, 1.1, 1.1) rotate(3deg)
            }
            40%, 60%, 80% {
                transform: scale3d(1.1, 1.1, 1.1) rotate(-3deg)
            }

            100% {
                transform: scaleX(1);
            }
        }

        @keyframes pulse {
            0% {
                -webkit-transform: scaleX(1);
                transform: scaleX(1)
            }
            50% {
                -webkit-transform: scale3d(1.05, 1.05, 1.05);
                transform: scale3d(1.05, 1.05, 1.05)
            }
            to {
                -webkit-transform: scaleX(1);
                transform: scaleX(1)
            }
        }
    }
</style>