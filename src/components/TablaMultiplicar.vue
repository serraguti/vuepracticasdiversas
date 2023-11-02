<template>
    <div>
        <h1>Tabla multiplicar</h1>
        <label>Introduzca número</label>
        <input type="number" v-model="numero"/>
        <hr/>
        <table border="1" style="background-color: blue; color:white">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="num in 10" :key="num">
                    <td>
                        {{ $filters.getOperacion(numero, num)}}
                    </td>
                    <td>
                        {{ $filters.getMultiplicacion(numero, num)}}
                    </td>
                </tr>
            </tbody>
        </table> 
        <hr/>
        <table border="1" style="background-color:lightgreen"
        v-if="numero != 0">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>            
            <tbody>
                <tr v-for="num in 10" :key="num">
                    <td>{{numero + " * " + num}}</td>
                    <td>{{ numero * num}}</td>
                </tr>
            </tbody>
        </table>
        <button @click="generarTablaMultiplicar()">
            Tabla Multiplicar
        </button>
        <hr/>
        <table border="1" style="background-color:yellow">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody v-html="html"></tbody>
        </table>
    </div>
</template>

<script>
    export default   {
        name: "TablaMultiplicar", 
        data() {
            return {
                html: "",
                numero: 0
            }
        }, 
        methods: {
            generarTablaMultiplicar() {
                this.html = "";
                for (var i = 1; i <= 10; i++){
                    var resultado = this.numero * i;
                    var operacion = this.numero + " * " + i;
                    this.html += "<tr>";
                    this.html += "<td>" + operacion + "</td>";
                    this.html += "<td>" + resultado + "</td>";
                    this.html += "</tr>";
                }
            }
        }
    }
</script>