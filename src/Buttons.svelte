<script>
  export let value = 0;
  export let action;
  export let btnclass;
  export let wide;
</script>

<style>
*{
  box-sizing: border-box;
}
button{
  cursor: pointer;
  color:#fff;
  margin:0px;
  padding: 20px;
  border-radius: 0px;
  border: none;
  outline:none;
  display: block;
  width: 100%;
}
.btn-container{
  flex: 0 0 25%;
  padding: 1px;
}
.two-columns{
  flex:2;
}
.dark-gray{
  background-color: #3e3f41;
}
.light-gray{
  background-color: #5e5e60;
}
.orange{
  background-color: #fd9e17;
}
</style>
<div class="btn-container" class:two-columns={wide}><button class={btnclass} {value} on:click={(e)=>action(e.target.value)}>{value}</button></div>