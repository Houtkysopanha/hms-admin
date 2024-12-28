<template>
    <div class="header">
        <div class="content">
            <h1>Header</h1>
        </div>
        
    </div>
</template>
<script>
export default {
    name: 'HeaderBar'
}
</script>
<style scoped>
.header{
    width: 100%;
    background-color: var(--secondary-color);
  height: 50px;
  padding: 10px;;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}
.content{
    margin: 0px 20px;
}
</style>