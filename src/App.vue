<template>
    <div class="container">
        <div class="glass">
            <div class="calculator">
                <div class="calc">
                    {{ calc }}
                </div>
                <div class="value">
                    {{ value }}
                </div>
                <div class="buttons">
                    <div
                        v-for="x in 10"
                        v-on:click="setModifier(x - 1)"
                        class="btn"
                        :key="x"
                    >
                        {{ x - 1 }}
                    </div>
                    <div v-on:click="add()" class="btn">+</div>
                    <div v-on:click="sub()" class="btn">-</div>
                    <div v-on:click="divide()" class="btn">/</div>
                    <div v-on:click="mult()" class="btn">x</div>
                    <div v-on:click="calculate()" class="btn">=</div>
                    <div v-on:click="reset()" class="btn">C</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "App",
    data: function () {
        return {
            calc: "",
            value: null,
        };
    },
    methods: {
        add() {
            this.calc += "+";
        },
        sub() {
            this.calc += "-";
        },
        mult() {
            this.calc += "*";
        },
        divide() {
            this.calc += "/";
        },
        setModifier(x) {
            this.calc += x;
        },
        calculate() {
            this.value = eval(this.calc);
            this.calc = this.value;
        },
        reset() {
            this.value = null;
            this.calc = "";
        },
    },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Rajdhani:300&display=swap");

*,
*::before,
*::after {
    box-sizing: border-box;
}
body {
    width: 100vw;
    height: 100vh;
    background-image: url("./assets/bg.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    color: rgba(255, 255, 255, 1);
    font-family: "Rajdhani", sans-serif;
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    text-align: center;
}

.calculator {
    width: 320px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    justify-content: center;
    align-items: center;
    backdrop-filter: blur(5px);
    box-shadow: 0 25px 45px rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(255, 255, 255, 0.5);
    border-right: 1px solid rgba(255, 255, 255, 0.2);
    border-left: 1px solid rgba(255, 255, 255, 0.2);
}

.buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 280px;
}

.btn {
    flex: 0 0 93px;
    height: 63px;
    border: 1px solid transparent;
    line-height: 61px;
    transition: all 0.5s;
    border-radius: 3px;

    &:hover {
        background-color: rgba(255, 255, 255, 0.2);
        border-color: rgba(255, 255, 255, 0.1);
        color: #fff;
        cursor: pointer;
        transition: all 0.3s;
    }
}

.value{
  height: 50px;
  line-height: 50px;
  font-size: 30px;
}
// body {
//     margin: 0;
//     padding: 0;
// }
// .container {
//     width: 100vw;
//     height: 100vh;
//     background-image: url("./assets/bg.jpg");
//     background-position: center;
//     background-size: cover;
//     background-repeat: no-repeat;
//     display: flex;
//     flex-direction: column;
//     align-content: center;
//     justify-content: center;
//     align-items: center;
//     @media only screen and (min-width: 480px) {
//         flex-direction: row;
//     }
//     .glass {
//         width: 100%;
//         max-width: 350px;
//         height: 250px;
//         margin: 20px;
//         border: 2px solid rgba(255, 255, 255, 0.2);
//         background: rgba(255, 255, 255, 0.4);
//         border-radius: 10px;
//         z-index: 2;
//         overflow: hidden;
//         backdrop-filter: blur(5px);
//         -webkit-backdrop-filter: blur(5px);
//     }
//     .glass {
//         border: 2px solid rgba(0, 0, 0, 0.2);
//         background: rgba(0, 0, 0, 0.4);
//     }

//     .calculator{
//       justify-content: center;
//       align-items: center;

//       .buttons{
//         display: flex;
//         flex-wrap: wrap;
//         justify-content: center;
//         width: 280px;

//         .btn{
//           flex: 0 0 93px;
//           height: 63px;
//           border: 1px solid transparent;
//           line-height: 61px;
//           transition: all 0.5s;
//           border-radius: 3px;

//           &:hover{
//             background-color: rgba(255, 255, 255, 0.2);
//             border-color: rgba(255, 255, 255, 0.1);
//             color: #fff;
//             cursor: pointer;
//             transition: all 0.3s;
//           }
//         }
//       }

//     }
// }
</style>
