<template>
    <div class="ContDv">
        <img v-on:click="Left" id="Left" src="../assets/Left.png" alt="">
        <img v-on:click="Right" id="Right" src="../assets/Right.png" alt="">
        <div ref="Cont" class="Cont">
            <div v-for="item in TestingAryy" :key="item" class="Product">
                <img :src="item.url" alt="">
                <div class="PrDiv">
                    <h1>{{ item.Hone }}</h1>
                    <h2>{{ item.Htwo }}</h2>
                    <h3>{{ item.Hsvry }}</h3>
                    <hr>
                    <p>{{ item.Hpi }}</p>
                </div>
            </div> 
        </div>
    </div>
</template>

<script>
import Img1 from '../assets/battlefield.jpg'
import Img2 from '../assets/Batt.png'
import Img3 from '../assets/Siroba.png'

export default {
    data() {
        return {
            TstCV: 0,
            TestingCv: 0,
            TestingAryy: [
                {
                    url: Img1,
                    Hone: 'ძუკნა საროსკიპოში',
                    Htwo: 'Luka Saroskipo',
                    Hsvry: '2024 . კომედია,არენა',
                    Hpi: 'ლუკას ტყნამენ 3 ზანგი და პირველი ადგილისთვის ერთმანეთს ემტერებოდნენ. წლების შემდეგ, ორივემ სამედიცინო უნივერსიტეტი დაამთავრა. ჯონუ წარმატებული პლასტიკური ქირურგი გახდა.'
                },
                {
                    url: Img2,
                    Hone: 'მკვდარი მეგობარი',
                    Htwo: 'DOCTOR SLUMP',
                    Hsvry: '2024 . კომედია,რომანტიკა',
                    Hpi: 'იო ჯონუ და ნამ ჰანული საუკეთესო მოსწავლეები იყვნენ და პირველი ადგილისთვის ერთმანეთს ემტერებოდნენ. წლების შემდეგ, ორივემ სამედიცინო უნივერსიტეტი დაამთავრა. ჯონუ წარმატებული პლასტიკური ქირურგი გახდა'
                },
                {
                    url: Img3,
                    Hone: 'ძუკნა საროსკიპოში',
                    Htwo: 'Luka Saroskipo',
                    Hsvry: '2024 . კომედია,არენა',
                    Hpi: 'იო ჯონუ და ნამ ჰანული საუკეთესო მოსწავლეები იყვნენ და პირველი ადგილისთვის ერთმანეთს ემტერებოდნენ. წლების შემდეგ, ორივემ სამედიცინო უნივერსიტეტი დაამთავრა. ჯონუ წარმატებული პლასტიკური ქირურგი გახდა.'
                }
            ]
        }
    },
    mounted(){
        setInterval(this.Right, 6000)
    },
    methods: {
        Right() {
            if(this.TestingCv == 0){
            this.TestingCv = 1;
            let AllProduct = document.querySelectorAll('.Product img');
            AllProduct.forEach(item => {
                item.style.transform = 'translateY(10px)'
                item.style.opacity = '0.1'
                setTimeout(() => {
                    item.style.transform = 'translateY(0px)'
                    item.style.opacity = '1'
                }, 300)
            })
            this.$refs.Cont.scrollLeft += '1200'
            this.TstCV++
            if (this.TstCV == 3) {
                this.$refs.Cont.scrollLeft = '0'
                this.TstCV = 0
            }
            let AllPrDiv = document.querySelectorAll('.PrDiv')
            AllPrDiv.forEach(item =>{
                item.style.transform = 'translateX(-600px)'
                item.style.opacity = '0'
                item.style.filter = 'blur(100px)'
                setTimeout(() =>{
                item.style.filter = 'blur(0px)'
                item.style.transform = 'translateX(0px)'
                item.style.opacity = '1'
                }, 500)
            })
            setTimeout(() =>{
                this.TestingCv = 0;
            },2000)
        }
        },
        Left() {
            this.$refs.Cont.scrollLeft -= '1200'
            this.TstCV--
            if (this.TstCV == -1) {
                this.$refs.Cont.scrollLeft = '3600'
                this.TstCV = 2
            }
            let AllProduct = document.querySelectorAll('.Product img');
            AllProduct.forEach(item => {
                item.style.transform = 'translateY(10px)'
                item.style.opacity = '0.4'
                setTimeout(() => {
                    item.style.transform = 'translateY(0px)'
                    item.style.opacity = '1'
                }, 300)
            })
        },
    }
}
</script>

<style>
.PrDiv h1{
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 100;
    color: white;
    margin: 0;
    padding: 0;
}
.PrDiv h2{
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 100;
    color: white;
    margin: 10px 0;
    padding: 0;
}
.PrDiv h3{
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 100;
    color: white;
    margin: 10px 0;
    padding: 0;
}
.PrDiv p{
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 100;
    color: white;
    margin: 10px 0;
    padding: 0;
    width: 300px;
    text-align: center;
}
.PrDiv {
    position: absolute;
    height: 400px;
    width: 500px;
    backdrop-filter: blur(20px);
    left: 0px;
    top: 0px;
    transition: 1s;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
}

.Cont {
    width: 1200px;
    height: 400px;
    display: flex;
    overflow: hidden;
    position: relative;
}
.Product {
    width: 1200px;
    height: 100%;
    flex-shrink: 0;
    position: relative;
    overflow: hidden;
}

.Product img {
    width: 100%;
    height: 110%;
    object-fit: cover;
    transition: 0.5s;
    margin-top: -10px;
}

#Left {
    width: 55px;
    height: 55px;
    position: absolute;
    top: 170px;
    cursor: pointer;
    border-radius: 50%;
    left: -15px;
    z-index: 5;
}

#Right {
    width: 55px;
    height: 55px;
    position: absolute;
    top: 170px;
    cursor: pointer;
    border-radius: 50%;
    right: -15px;
    z-index: 5;
}

.ContDv {
    width: 1200px;
    height: 400px;
    position: relative;
    background-color: black;
    border-radius: 15px;
    overflow: hidden;
}

body {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>