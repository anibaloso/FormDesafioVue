<script>
export default {
    name: 'FormComponent',
    data() {
        return {
            background: '',
            colorText: '',
            textoVisible: true,
            borde: '',
            contenido: '',
            tipografia: ['Courier New', 'Franklin Gothic Medium', 'Times New Roman', 'cursive', 'Arial'],
            tipSelect: '',
            textoOpaco: false,
            sizes: [
                    {'label':'Pequeño', 'value': 'small'},
                    {'label':'Mediano', 'value': 'medium'},
                    {'label':'Grande', 'value': 'large'}
                
            ],
            sizeSelected: 'medium'
        }
    }
}
</script>
<template>
    <div class="container">
        <div id="izq">
            <label>Color de Fondo</label>
            <input type="text" v-model="background">
            <label>Color de texto</label>
            <input type="text" v-model="colorText">
            <label>Mostrar Texto
                <input type="checkbox" v-model="textoVisible">
            </label>
            <label>Borde</label>
            <input type="range" v-model="borde">
            <label>Contenido textual</label>
            <input type="textarea" v-model="contenido">
            <label for="">Tipografia</label>
            <select v-model="tipSelect" id="">
                <option v-for="tipo in tipografia" :key="tipo" :value="tipo">{{ tipo }}</option>

            </select>
            <label>Opaco
                <input type="checkbox" v-model="textoOpaco">
            </label>

            <label>Tamaño de letra</label>
            <div v-for="size in sizes" :key="size">
                <label :for="size.value">{{ size.label }}</label>
                    <input 
                    type="radio" 
                    :name="size.value"
                    :value="size.value"
                    :id="size.value" 
                    v-model="sizeSelected">
                                    
            </div>

        </div>
        <br><br>
        <div id="cuadrado" :style="{
            borderRadius: borde + '%',
            background: background,
            color: colorText,
            fontFamily: tipSelect,
            fontSize:sizeSelected
        }">
            <div v-show="textoVisible" :class="{ 'opaco': textoOpaco }">{{ contenido }}</div>
        </div>


    </div>
</template>
<style scoped>
.container {
    display: flex;
    margin-top: 10%;

}

#izq {
    display: flex;
    flex-direction: column;
    width: 30%;
    background-color: #304f51;
    color: white;
    padding: 2rem;
}

#cuadrado {
    height: 200px;
    width: 200px;
    background-color: cornflowerblue;
    display: flex;
    text-align: center;
    justify-content: center;
    align-items: center;
    margin-left: 20%;
}

.opaco {
    opacity: 0.2;
}
</style>