<template>
    <footer class="footer" :style="{ top: top + 'px', position: position }">
        <p class="footer__copyright" v-if="footer !== 9">
            ©2019. Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
            Explicabo quidem, exercitationem quasi labore consequatur commodi 
            quibusdam modi velit laborum nam quas perspiciatis quaerat odit. 
            Eligendi tempora perferendis id. Nam, aut.
        </p>
        <p class="footer__terms" v-if="footer == 9">
            ©2019. Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
            Explicabo quidem, exercitationem quasi labore consequatur commodi 
            quibusdam modi velit laborum nam quas perspiciatis quaerat odit. 
            Eligendi tempora perferendis id. Nam, aut.©2019. Lorem ipsum dolor 
            sit, amet consectetur adipisicing elit. Explicabo quidem, exercitationem 
            quasi labore consequatur commodi quibusdam modi velit laborum nam quas 
            perspiciatis quaerat odit. Eligendi tempora perferendis id. Nam, 
            aut.©2019. Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
            Explicabo quidem, exercitationem quasi labore consequatur commodi 
            quibusdam modi velit laborum nam quas perspiciatis quaerat odit. 
            Eligendi tempora perferendis id. Nam, aut.
        </p>
    </footer>
</template>

<script>
export default {
    data: () => ({
    top: null,
    position: null,
    views: null,
    copyright: true
    }),
    props: {
        footer: Number
    },
    methods: {
        appHeight() {
            let mainEl = document.querySelector('.main');
            let headerEl = document.querySelector('.header');
            let appEl = document.querySelector('#app');
            let leftEl = document.querySelector('.body-black__left');
            let rightEl = document.querySelector('.body-black__right');
            let imgEl = document.querySelector('.body-img');
            let containerEl = document.querySelector('.body-container');

            leftEl.style.left ='-' + (appEl.clientWidth / 2) + 'px';
            rightEl.style.right ='-' + (appEl.clientWidth / 2) + 'px';

            if(appEl.clientWidth < appEl.clientHeight && appEl.clientWidth < appEl.clientHeight - 250 ) {
                imgEl.style.width = (appEl.clientHeight - 250) + 'px';
                imgEl.style.left = '-' + ((appEl.clientHeight - 100) / 4) + 'px';
                imgEl.style.right = '-' + ((appEl.clientHeight - 100) / 4) + 'px';
            }
            else {
                imgEl.style.width = 50 + '%';
                imgEl.style.left = '-' + ((appEl.clientHeight - 100) / 4) + 'px';
                imgEl.style.right = '-' + ((appEl.clientHeight - 100) / 4) + 'px';
            }

            if(appEl.clientHeight > (mainEl.clientHeight + headerEl.clientHeight + 40)) {
                this.top = appEl.clientHeight - 30;
                this.position = 'absolute';
            }
            else {
                this.top = mainEl.clientHeight + headerEl.clientHeight + 30;
                this.position = 'absolute';
            }
        }
    },
    mounted() {
        this.appHeight();
        window.onresize = this.appHeight;
    }
}
</script>

<style lang="scss">
    .footer {
        width: 100%;
        z-index: 2;

        .footer__copyright {
            height: 18px;
            font-family: "Roboto";
            font-weight: normal;
            font-size: 10px;
            line-height: 6px;
            text-align: center;
            font-variant: small-caps;
            color: rgba(229, 229, 229, 0.8);
        }

        .footer__terms {
            font-family: "Roboto";
            font-weight: normal;
            font-size: 10px;
            line-height: 12px;
            padding: 8px 16px 0 16px;
            text-align: justify;
            text-transform: lowercase;
            color: #E7D7CC;
            background-color: rgba(3, 1, 35, 0.9);
            backdrop-filter: blur(4px);
        }
    }
</style>