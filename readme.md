<!DOCTYPE html>

<html>


 

<head>

    <meta charset='utf-8'>

    <meta http-equiv='X-UA-Compatible' content='IE=edge'>

    <title>Parametros</title>

    <meta name='viewport' content='width=device-width, initial-scale=1'>

    <style>

        body {

            font-family: Arial, Helvetica, sans-serif;

            display: flex;

            justify-content: center;

            align-items: center;

            height: 100vh;

            margin: 0;


 

        }


 

        .app {

            display: flex;

            justify-content: space-around;

            align-items: center;

            width: 100%;

        }


 

        .form-parameters {

            border: 1px solid #ccc;

            border-radius: 8px;

            padding: 20px;

            width: 300px;

            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

            background-color: #fff;

        }


 

        .input-data {


 

            margin-bottom: 15px;

        }


 

        .form-parameters label {

            display: flex;

            flex-direction: column;

            margin-bottom: 5px;

            font-weight: bold;

            align-items: center;

        }


 

        .form-parameters input {

            width: 40%;

            padding: 8px;

            border: 1px solid #ccc;

            border-radius: 5px;

        }


 

        button {

            padding: 10px;

            border: none;

            border-radius: 4px;

            background-color: #007bff;

            color: #fff;

            font-size: 16px;

            cursor: pointer;

        }


 

        button :hover {

            background-color: #0056b3;

        }


 

        .title {

            font-size: 1.1rem;

        }


 

        .text {

            font-size: 0.9;

        }


 

        .unidades_medida {

            font-size: 0.7rem;

        }

    </style>

</head>


 

<body>

    <div class="app">

        <form class="form-parameters">

            <div class="input-data"><label for="eta-1-vazao">

                    ETA 1:<input type="number" name="eta-1-vazao" id="eta-1-vazao">

                </label></div>

            <div class="input-data">

                <label for="eta-2-vazao">

                    ETA 2:<input type="number" name="eta-2-vazao" id="eta-2-vazao">

                </label>

            </div>

            <div class="input-data">

                <label for="eta-3-vazao">

                    ETA 3:<input type="number" name="eta-3-vazao" id="eta-3-vazao">

                </label>

            </div>

            <div class="input-data">

                <label for="cisterna">

                    Cisterna:<input type="number" name="cisterna" id="cisterna">

                </label>

            </div>


 

            <div class="input-data">

                <label for="turbidez-agua-tratada">

                    Turbidez água tratada:<input type="number" name="turbidez-agua-tratada" id="turbidez-agua-tratada">

                </label>

            </div>

            <div class="input-data">

                <label for="cloro-residual-agua-tratada">

                    Cloro residual água tratada:<input type="number" name="cloro-residual-agua-tratada"

                        id="cloro-residual-agua-tratada">

                </label>

            </div>

            <div class="input-data">

                <label for="turbidez-agua-bruta">

                    Turbidez água bruta:<input type="number" name="turbidez-agua-bruta" id="turbidez-agua-bruta">

                </label>

            </div>

            <div class="input-data">

                <label for="ph-agua-bruta">

                    pH água bruta:<input type="number" name="ph-agua-bruta" id="ph-agua-bruta">

                </label>

            </div>

            <button onclick="geracaoParametro()">Gerar</button>

        </form>


 

        <div class="text">

            <h1 class="title">ETA 1:</h1>

            <span id="result_eta1">0</span>

            <span class="unidades_medida">m³</span>


 

            <h1 class="title">ETA 2:</h1>

            <span id="result_eta2">0</span>

            <span class="unidades_medida">m³</span>


 

            <h1 class="title">ETA 3:</h1>

            <span id="result_eta3">0</span>

            <span class="unidades_medida">m³</span>


 

            <h1 class="title">Total Captado:</h1>

            <span id="result_totalcaptado">0</span>

            <span class="unidades_medida">m³</span>


 

            <h1 class="title">Reservatório elevado:</h1> 1100

            <span class="unidades_medida">m³</span>


 

            <h1 class="title">Cisterna:</h1>

            <span id="result_cisterna">0</span>

            <span class="unidades_medida">m³</span>

            <h1 class="title">Cloro residual água tratada:</h1>

            <span id="result_cloro_residual">0</span>


 

            <h1 class="title">Turbidez de água tratada:</h1>

            <span id="result_turb_agua_tratada">0</span>

            <span class="unidades_medida">NTU</span>

        </div>

    </div>



 

    <script>

        const ETA1V = document.getElementById("eta-1-vazao")

        const ETA2V = document.getElementById("eta-2-vazao")

        const ETA3V = document.getElementById("eta-3-vazao")

        const cisterna = document.getElementById("cisterna")

        const turbidezAguaTratada = document.getElementById("turbidez-agua-tratada")

        const cloroResidualAguaTratada = document.getElementById("cloro-residual-agua-tratada")

        const turbidezAguaBruta = document.getElementById("turbidez-agua-bruta")

        const phAguaBruta = document.getElementById("ph-agua-bruta")


 

        const result_eta1 = document.getElementById("result_eta1")

        const result_eta2 = document.getElementById("result_eta2")

        const result_eta3 = document.getElementById("result_eta3")

        const result_totalcaptado = document.getElementById("result_totalcaptado")

        const result_cisterna = document.getElementById("result_cisterna")

        const result_turb_agua_tratada = document.getElementById("result_turb_agua_tratada")

        const result_cloro_residual = document.getElementById("result_cloro_residual")


 

        function geracaoParametro() {


 

            event.preventDefault()

            const resultFinal = `

     * Status

    ETA 1: ${ETA1V.value || 0} m³

    ETA 2: ${ETA2V.value || 0} m³

    ETA 3: ${ETA3V.value || 0} m³

    Total Captado: ${Number(ETA1V.value || 0) + Number(ETA2V.value || 0) + Number(ETA3V.value || 0)} m³

    Reservatório elevado: 990 m³

    Cisterna: ${cisterna.value || 0}

    Turbidez de água tratada: ${turbidezAguaTratada.value || 0} NTU

    Cloro residual água tratada: ${cloroResidualAguaTratada.value || 0}

    `

            console.log(resultFinal)


 

            result_eta1.innerText = ETA1V.value || 0;

            result_eta2.innerText = ETA2V.value || 0;

            result_eta3.innerText = ETA3V.value || 0;

            result_totalcaptado.innerText = Number(ETA1V.value || 0) + Number(ETA2V.value || 0) + Number(ETA3V.value || 0)

            result_cisterna.innerText = cisterna.value || 0

            result_turb_agua_tratada.innerText = turbidezAguaTratada.value || 0

            result_cloro_residual.innerText = cloroResidualAguaTratada.value || 0


 

            navigator.clipboard.writeText(resultFinal).then(alert(`Copiado com sucesso!`)).catch(e => console.log(e))

        }

    </script>

</body>


 

</html> 
 