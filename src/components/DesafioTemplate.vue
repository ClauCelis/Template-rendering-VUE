<template>
    <div>
        <h1>Desafío Template y Rendering</h1>
    </div>
    <div style="display:flex;">
        <div class="container">
            <form>
                <!-- Campo de texto para especificar el color de fondo -->
                <div>
                    <label class="form-label" title="Colores recomendados: red, blue, green, yellow, pink, purple, orange, black, gray, brown, cyan, magenta, lime, teal">Color de fondo (texto o hexadecimal)</label>
                    <br>
                    <!-- Enlaza el valor del input al dato "fondo" con v-model -->
                    <input style="width: 100%;" v-model="fondo" type="text" placeholder="Escribe un color en inglés">
                    </input>
                </div>
                <br>

                <!-- Campo para seleccionar el color del texto -->
                <div>
                    <label class="form-label">Color de texto</label>
                    <br>
                    <!-- Enlaza el valor seleccionado al dato "texto" -->
                    <select style="width: 100%;" v-model="texto">
                        <!-- Genera las opciones de colores usando v-for -->
                        <option v-for="color in colortxt" :key="color">{{ color }}</option>
                    </select>
                    <br>
                    <!-- Checkbox para controlar la visibilidad del texto -->
                    <label class="form-label">Mostrar texto</label>
                    <input type="checkbox" v-model="mostrar">
                </div>
                <br>

                <!-- Control deslizante para ajustar el radio del borde -->
                <div>
                    <label class="form-label">Borde</label>
                    <br>
                    <!-- Enlaza el valor del input al dato "borde" -->
                    <input style="width: 100%;" type="range" v-model="borde">
                </div>
                <br>

                <!-- Área de texto para el contenido textual -->
                <div>
                    <label class="form-label">Contenido textual</label>
                    <br>
                    <!-- Enlaza el valor del área de texto al dato "textoArea" -->
                    <textarea style="width: 100%;" v-model="textoArea"></textarea>
                </div>
                <br>

                <!-- Selección de la tipografía del texto -->
                <div>
                    <label class="form-label">Tipografía</label>
                    <br>
                    <!-- Enlaza el valor seleccionado al dato "tipografia" -->
                    <select style="width: 100%;" v-model="tipografia">
                        <!-- Genera las opciones de estilos de texto usando v-for -->
                        <option v-for="estilo in estilos" :key="estilo">{{ estilo }}</option>
                    </select>
                    <br>
                    <!-- Checkbox para controlar la opacidad de la forma -->
                    <label class="form-label">Opaco</label>
                    <input type="checkbox" v-model="opaco">
                </div>
                <br>

                <!-- Selección del tamaño de la letra mediante botones de opción -->
                <div>
                    <label class="form-label">Tamaño de letra</label>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="flexRadioDefault" v-model="tamaño" value="12px" id="tamañoPequeño">
                        <label class="form-check-label" for="tamañoPequeño">Pequeño</label>

                        <input class="form-check-input" type="radio" name="flexRadioDefault" v-model="tamaño" value="18px" id="tamañoMediano">
                        <label class="form-check-label" for="tamañoMediano">Mediano</label>

                        <input class="form-check-input" type="radio" name="flexRadioDefault" v-model="tamaño" value="25px" id="tamañoGrande">
                        <label class="form-check-label" for="tamañoGrande">Grande</label>
                    </div>
                </div>
            </form>
        </div>

        <!-- Div con estilo dinámico para modificar su apariencia -->
        <div class="formaModificable" 
            :style="{ 
                background: fondo, 
                borderRadius: borde + 'px',
                opacity: opaco ? 1 : 0.5  // Cambia la opacidad según el valor de 'opaco'
            }">
            
            <!-- El párrafo se muestra si 'mostrar' es true -->
            <p :style="{
                color: texto,
                fontStyle: tipografia,
                fontSize: tamaño
            }" v-if="mostrar">{{ textoArea }}</p>

        </div>
    </div>
</template>

<style>
/* Estilos de la caja de configuración */
.container {
    justify-content: left;
    width: 300px;
    height: 400px;
    border: 1px solid darkolivegreen;
    border-radius: 3%;
    margin-inline-end: 5rem;
    background-color: rgb(38, 70, 30);
    color: white;
    padding: 1rem;
}

/* Estilos de la forma modificable */
.formaModificable {
    width: 250px;
    height: 250px;
    text-align: center;
    align-content: center;
    text-size-adjust: auto;
    padding: 1rem;
    align-self: center;
}
</style>

<script>
export default {
    data() {
        return {
            mostrar: false, // Controla si el texto se muestra
            fondo: '', // Color de fondo de la forma
            texto: '', // Color del texto
            colortxt: ["white", "black", "pink", "blue", "yellow"], // Opciones de colores para el texto
            borde: '0', // Tamaño del borde
            textoArea: 'Ingresar texto', // Contenido del área de texto
            tipografia: '', // Estilo de la tipografía
            estilos: ["normal", "italic"], // Opciones de estilos de tipografía
            opaco: true, // Controla la opacidad de la forma
            tamaño: '', // Tamaño del texto
        }
    }
}
</script>
