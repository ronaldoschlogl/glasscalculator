<template>
    <div class="container">
        <div class="glass">
            <div class="calculator">
                <div class="calc">
                    {{ calculatorValue }}
                </div>
                <div class="value">
                    {{ previousCalculatorValue }}
                </div>
                <div class="buttons">
                    <div
                        class="button"
                        v-for="n in btnArr"
                        :key="n"
                        :class="{
                            operator: [
                                'C',
                                '*',
                                '/',
                                '-',
                                '+',
                                '%',
                                '=',
                            ].includes(n),
                        }"
                    >
                        <div class="btn" @click="action(n)">
                            {{ n }}
                        </div>
                    </div>
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
            calculatorValue: "",
            btnArr: [
                "C",
                "*",
                "/",
                "-",
                "7",
                "8",
                "9",
                "+",
                "4",
                "5",
                "6",
                "%",
                "1",
                "2",
                "3",
                "=",
                "0",
                ".",
            ],
            operator: null,
            previousCalculatorValue: "",
        };
    },
    methods: {
        action(n) {
            if (!isNaN(n) || n === ".") {
                this.calculatorValue += n + "";
            }
            if (n === "C") {
                this.calculatorValue = "";
            }
            if (n === "%") {
                this.calculatorValue = this.calculatorValue / 100 + "";
            }
            if (["/", "*", "-", "+"].includes(n)) {
                this.operator = n;
                this.previousCalculatorValue = this.calculatorValue;
                this.calculatorValue = "";
            }
            if (n === "=") {
                this.calculatorValue = eval(
                    this.previousCalculatorValue +
                        this.operator +
                        this.calculatorValue
                );
                this.previousCalculatorValue = "";
                this.operator = null;
            }
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
    color: #fff;
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
    width: 100%;
    background: rgba(32, 32, 32, 0.1);
    border-radius: 10px;
    justify-content: center;
    align-items: center;
    backdrop-filter: blur(10px);
    box-shadow: 0 25px 45px rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(255, 255, 255, 0.5);
    border-right: 1px solid rgba(255, 255, 255, 0.2);
    border-left: 1px solid rgba(255, 255, 255, 0.2);
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    width: 280px;
    border-radius: 4px;
    align-items: center;
    justify-content: center;
    margin: 10px auto;
    gap: 5px;
}

.btn {
    padding: 6px;
    border: 1px solid transparent;
    border-radius: 3px;
    margin: 4px;
    font-size: 1.5em;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
    &:hover {
        background-color: rgba(255, 255, 255, 0.2);
        border-color: rgba(255, 255, 255, 0.1);
        color: #fff;
        cursor: pointer;
        transition: all 0.3s;
    }
}

.value {
    height: 50px;
    line-height: 50px;
    font-size: 30px;
}
</style>
