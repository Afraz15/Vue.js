<template>
    <div class="cal">     
        <div class="scr">{{current || '0'}}</div>
        <div><button @click="dgt(7)" class="btn btn-success"><h3>7</h3></button></div>
        <div><button @click="dgt(8)" class="btn btn-success"><h3>8</h3></button></div>
        <div><button @click="dgt(9)" class="btn btn-success"><h3>9</h3></button></div>
        <div><button @click="times" class="btn btn-warning"><h3>x</h3></button></div>
        <div><button @click="dgt(4)" class="btn btn-success"><h3>4</h3></button></div>
        <div><button @click="dgt(5)" class="btn btn-success"><h3>5</h3></button></div>
        <div><button @click="dgt(6)" class="btn btn-success"><h3>6</h3></button></div>
        <div><button @click="sub" class="btn btn-warning"><h3>-</h3></button></div>
        <div><button @click="dgt(1)" class="btn btn-success"><h3>1</h3></button></div>
        <div><button @click="dgt(2)" class="btn btn-success"><h3>2</h3></button></div>
        <div><button @click="dgt(3)" class="btn btn-success"><h3>3</h3></button></div>
        <div><button @click="div" class="btn btn-warning div"><h3>/</h3></button></div>
        <div class="endl"><button @click="dgt(0)" class="btn btn-success"><h3>0</h3></button></div>
        <div><button @click="add" class="btn btn-warning"><h3>+</h3></button></div>
        <div><button @click="sign" class="btn btn-success"><h3>+/-</h3></button></div>
        <div><button @click="dot()" class="btn btn-success"><h3>.</h3></button></div>
        <div><button @click="equal" class="btn btn-warning"><h3>=</h3></button></div>
        <div><button @click="clr" class="btn btn-warning d2"><h3>C</h3></button></div>
    </div>
</template>

<script>

export default {
    name: 'Cal',
    data: () => {
        return{
            current: '',
            oper: false,
            pre: null,
            click: false,
        }
    },

    methods: {
        clr(){
            this.current = ''
        },
        sign(){
            this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`
        },
        dgt(num){
            if(this.click){
                this.current = '',
                this.click = false;
            }
            this.current = `${this.current}${num}`;
        },
        dot(){
            if(this.current.indexOf('.') === -1){
                this.dgt('.')
            }
        },
        times(){
            this.oper = ( a, b ) => a * b,
            this.setpre();
        },
        sub(){
            this.oper = ( a, b ) => a - b,
            this.setpre();
        },
        add(){
            this.oper = ( a, b ) => a + b;
            this.setpre();
        },
        div(){
            this.oper = ( a, b ) => b / a;
            this.setpre();
        },
        equal(){
            this.current = `${this.oper(parseFloat(this.current),parseFloat(this.pre))}`,
            this.pre = null;
        },
        setpre(){
            this.pre = this.current,
            this.click = true;
        },
        done(){
            if(this.current){
                
            }
        }

    }

}

</script>

<style>

.cal{
    text-align: center;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    font-size: 2rem;
    margin: 9rem;
}

.scr{
    grid-column: 1 / 5;
    background: lightslategrey;
}

.cal > div{
    margin: 0.3rem;
}

.endl{
    grid-column: 1 / 4;
}

button{
    width: 100%;
    height: 3rem;
    
}


</style>



