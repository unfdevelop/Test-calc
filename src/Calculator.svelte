<script>
  import Buttons from './Buttons.svelte';
  let value;
  let result ="";
  let input ="0";
  let operation = "";

  function action(value) {
    console.log(operation);
    let isNumeric = !isNaN(value);
      if(!isNumeric){
        if(value===","){
        if(input.indexOf('.') < 0 && input.charAt(0) !==""){
          console.log("QWEQWE");
          input +=".";
        }}
        if(operation !=="" && value !=="," && value !=="±" && input !=="" && result !==""){
          calculate(operation);
        }
      }
      if(isNumeric){
        if(input === "0"){
          input = "";
        }
        if(result ==="" || operation !=="")
        {
        input = input + value;
        }
      } else if (value ==="AC"){
        input = "0";
        result = "";
      } else if (value ==="+"){
        if(result ===""){
        result = input;
        input = "";
        }
        operation = "+";
      } else if (value ==="-"){
        if(result ===""){
        result = input;
        input = "";
        }
        operation = "-";
      } else if (value ==="÷"){
        if(result ===""){
        result = input;
        input = "";
        }
        operation = "÷";
      } else if (value ==="×"){
        if(result ===""){
        result = input;
        input = "";
        }
        operation = "×";
      } else if (value ==="%"){
        if(result ===""){
        result = input;
        input = "";
        }
        operation = "%";
      } else if (value ==="="){
        if(result !==""){calculate(operation);}
      } else if (value ==="±"){
        if(input !==""){input *= -1;}
      }
  }
  function calculate(action){
    switch (action) {
      case "+":
        result = parseFloat(result) + parseFloat(input);
        break;
      case "-":
        result = parseFloat(result) - parseFloat(input);
        break;
      case "÷":
        result = parseFloat(result) / parseFloat(input);
        break;
      case "×":
        result = parseFloat(result) * parseFloat(input);
        break;
      case "%":
        result = parseFloat(result) % parseFloat(input);
        break;
    }
    input = result;
    result ="";
    operation = "";
  }
</script>

<style>
  *, *::after,*::before{
  	box-sizing: border-box;
  }
  	.calculator__container{
  		display: flex;
  		justify-content: center;
  		align-items: center;
  	}
  	.calculator__form{
  		font-family: sans-serif;
  		display: flex;
  		flex-direction: column;
  		color:#fff;
  		font-size: 2em;
  		position: relative;
  		overflow: hidden;
  		border-radius: 10px;
  		background-color: #2c2c2e;
  		border: 1px solid #2c2c2e;
  		max-width: 390px;
  	}
  	.calculator__form::after{
  		content: "";
  		position: absolute;
  		top: 0;
  		left: 0;
  		right: 0;
  		bottom: 0;
  		box-shadow: 0px 0px 4px	#f5f5f5 inset;
  		pointer-events: none;
  	}
  	.calculator__buttons{
  		display: flex;
  		flex-wrap: wrap;
  	}
  	.calculator__header{
  		text-align: right;
  		font-size: 2em;
  		padding: 0px 10px;
  	}
  	.calculator__top{
  		padding: 10px;
  		display: flex;
  	}
  	.calculator__top > button + button{
  		margin-left: 15px;
  	}
  	.calculator__top > button{
  		border-radius: 50%;
  		font-size: 27px;
  		margin: 0px;
  		border: none;
  		outline: none;
  	}
  	.calculator__top > button:nth-child(1) {
  		background-color: #ff5851;
  	}
  	.calculator__top > button:nth-child(2){
  		background-color: #e4bf2e;
  	}
  	.calculator__top > button:nth-child(3){
  		background-color: #4db631;
  	}
    .result{
      display: block;
      min-height: 16px;
      font-size: 13px;
    }
    .input{
      display: block;
      min-height: 75px;
    }
</style>
<div class="calculator__container">
	<div class="calculator__form">
		<div class="calculator__top">
			<button></button>
			<button></button>
			<button></button>
		</div>
		<div class="calculator__header">
		  <span class="result"> {result}</span>
		  <span class="input">{input}</span>
		</div>
		<div class="calculator__buttons">
      <Buttons btnclass={"dark-gray"} value={"AC"} {action}/>
      <Buttons btnclass={"dark-gray"} value={"±"} {action}/>
      <Buttons btnclass={"dark-gray"} value={"%"} {action}/>
      <Buttons btnclass={"orange"} value={"÷"} {action}/>
      <Buttons btnclass={"light-gray"} value={"7"} {action}/>
      <Buttons btnclass={"light-gray"} value={"8"} {action}/>
      <Buttons btnclass={"light-gray"} value={"9"} {action}/>
      <Buttons btnclass={"orange"} value={"×"} {action}/>
      <Buttons btnclass={"light-gray"} value={"4"} {action}/>
      <Buttons btnclass={"light-gray"} value={"5"} {action}/>
      <Buttons btnclass={"light-gray"} value={"6"} {action}/>
      <Buttons btnclass={"orange"} value={"-"} {action}/>
      <Buttons btnclass={"light-gray"} value={"1"} {action}/>
      <Buttons btnclass={"light-gray"} value={"2"} {action}/>
      <Buttons btnclass={"light-gray"} value={"3"} {action}/>
      <Buttons btnclass={"orange"} value={"+"} {action}/>
      <Buttons wide={"true"} btnclass={"light-gray"} btnvalue={"0"} {action}/>
      <Buttons btnclass={"light-gray"} value={","} {action}/>
      <Buttons btnclass={"light-gray"} value={"="} {action}/>
		</div>
	</div>
</div>

