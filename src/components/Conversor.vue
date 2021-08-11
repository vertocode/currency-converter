<template>
  <div class="conversor">
    <h2>

        <select name="select" id="select">
            <option value="USD">USD</option>
            <option value="BRL">BRL</option>
            <option value="EUR">EUR</option>
            <option value="GBP">GBP</option>
            <option value="ARS">ARS</option>
            <option value="BTC">BTC</option>
            <option value="LTC">LTC</option>
            <option value="JPY">JPY</option>
            <option value="CHF">CHF</option>
            <option value="AUD">AUD</option>
            <option value="CNY">CNY</option>
            <option value="ILS">ILS</option>
            <option value="ETH">ETH</option>
            <option value="XRP">XRP</option>
            <option value="DOGE">DOGE</option>
        </select> 

        Para

         <select name="select2" id="select2">
            <option value="BRL">BRL</option>
            <option value="USD">USD</option>
            <option value="EUR">EUR</option>
            <option value="GBP">GBP</option>
            <option value="ARS">ARS</option>
            <option value="BTC">BTC</option>
            <option value="LTC">LTC</option>
            <option value="JPY">JPY</option>
            <option value="CHF">CHF</option>
            <option value="AUD">AUD</option>
            <option value="CNY">CNY</option>
            <option value="ILS">ILS</option>
            <option value="ETH">ETH</option>
            <option value="XRP">XRP</option>
            <option value="DOGE">DOGE</option>
         </select>

    </h2>
    <input type="text"  id="USD">
    <input type="button" value="Converter" v-on:click="converter()">
    <h2 id="igual"></h2>
    <h2 id="resultado">{{moedaB_value}}
    <p id="data"></p>
    </h2>
    <div class="center">
        <h3>Moedas disponiveis para conversão</h3>
        <ul>
            <li>BRL = Real Brasileiro</li>
            <li>USD = Dólar americano</li>
            <li>EUR = Euro</li>
            <li>GBP = Libra esterlina</li>
            <li>ARS = Peso argentino</li>
            <li>BTC = Bitcoin</li>
            <li>LTC = Litecoin</li>
            <li>JPY = Iene japonês</li>
            <li>CHF = Franco suíço</li>
            <li>AUD = Dólar australiano </li>
            <li>CNY = Remimbi</li>
            <li>ILS = Novo shekel israelense</li>
            <li>ETH = Ethereum</li>
            <li>XRP = XRP (Ripple)</li>
            <li>DOGE = Dogecoin</li>
        </ul>
        <p style="margin: 15px">OBS: Se alguma conversão de moedas não funcionar, pode ser que a API usada está em manutenção.</p>
    </div>
    <div class="credit">
        <h2>Feito por <strong><a href="https://vertocode.github.io/" target="_blank">vertocode</a></strong></h2>
    </div>

  </div>

</template>

<script>
export default {
    name: "Conversor",
    props: ["moedaA","moedaB"],
        data()
        {
            return {
                moedaA_value: "Digite um valor aqui",
                moedaB_value: 0
            }
        },
    methods:{
        converter(){
            let select = document.getElementById("select")
            let select2 = document.getElementById("select2")
            if(select.value == select2.value)
            {
                alert(select.value + " é igual a " + select2.value)
            }
            else
            {
                let link = select.value + "-" + select2.value
                let url = "https://economia.awesomeapi.com.br/json/daily/" + link
        
                fetch(url).then(res=>{
                    return res.json()
                    }).then(json=>{
                    console.log("API usada para essa conversão:" + url);
                    let input = document.getElementById("USD")
                    let res = document.getElementById("resultado")
                    let igual = document.getElementById("igual")
                    let entrada = document.getElementById("USD")
                    let data = document.getElementById("data")
                    let dolar = json[0].low
                    let result = dolar * entrada.value
                    if ((input.value >= 'a') && (input.value <= 'z'))
                    {
                        alert("[ERRO]Impossivel converter moedas em caracteres!")
                    }
                    if ((input.value >= 'A') && (input.value <= 'Z'))
                    {
                        alert("[ERRO]Impossivel converter moedas em caracteres!")
                    }
                    if (input.value < "0")
                    {
                        alert("[ERRO]Impossivel converter valores negativos!")
                    }
                    else if (select2.value == "BRL")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "R$"+parseFloat(result).toFixed(2)
                        data.innerHTML = ``
                    }
                    else if (select2.value == "USD")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "$"+parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "EUR")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "€" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "GBP")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "£" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "ARS")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "AR$" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "BTC")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "₿" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "LTC")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "Ł" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "JPY")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "¥" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "CHF")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "SFr" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "AUD")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "A$" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "CNY")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "元" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "ILS")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "₪" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "ETH")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "Ξ" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "XRP")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "XRP$" + parseFloat(result).toFixed(2)
                    }
                    else if (select2.value == "DOGE")
                    {
                        igual.innerHTML = `${entrada.value} ${select.value} é igual a:`
                        res.innerHTML = "Ð" + parseFloat(result).toFixed(2)
                    }
                    else
                    {
                        res.innerHTML == "Não é possivel converter esses 2 tipos de moedas, desculpe!"
                    }
                 })
            }

    }
}
}
</script>

<style scoped>

.center
{
    width: 400px;
    margin-left: 10px;
    text-align: initial;
    border: 2px solid;
    border-style: dashed;
}
.center h3 
{
    text-align: center;
    text-decoration: underline;
}
</style>>