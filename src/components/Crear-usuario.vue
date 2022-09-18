<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                Nuevo Usuario
            </div>
            <div class="card-body">
                
                <form v-on:submit.prevent="agregarRegistro">
                        <div class="form-group">
                          <label for="nombre">Nombre:</label>
                          <input type="text" name="nombre" id="nombre" v-model="usuario.nombre" class="form-control" placeholder="Nombre" aria-describedby="helpId">
                          <small id="helpId" class="text-muted">Escribe el nombre de usuario</small>
                        </div>
                        <div class="form-group">
                          <label for="apellido">Apellido:</label>
                          <input type="text" name="apellido" id="apellido" v-model="usuario.apellido" class="form-control" placeholder="Apellido" aria-describedby="helpId">
                          <small id="helpId" class="text-muted">Escribe el apellido de usuario</small>
                        </div>
                        <div class="form-group">
                          <label for="apodo">Apodo:</label>
                          <input type="text" name="apodo" id="apodo" v-model="usuario.apodo" class="form-control" placeholder="Apodo" aria-describedby="helpId">
                          <small id="helpId" class="text-muted">Escribe el apodo de usuario</small>
                        </div>
                        <div class="form-group">
                        <label for="correo">Correo electrónico:</label>
                        <input type="email" name="correo" id="correo" v-model="usuario.correo" class="form-control" placeholder="Correo@electronico.com" aria-describedby="helpId">
                        <small id="helpId" class="text-muted">Escribe el correo electrónico</small>
                        </div>

                        <div class="btn-group" role="group" aria-label="">
                            <button type="submit" class="btn btn-success">Agregar</button>
                            <button type="button" class="btn btn-warning">Cancelar</button>
                            
                        </div>

                </form>

            </div>
            
        </div>

    </div>
</template>
<script>
export default {
    data(){
            return{
                usuario:{}
            }
    },
    methods:{
        agregarRegistro(){
            console.log(this.usuario);
            var datosEnviar={
                            nombre:this.usuario.nombre, 
                            apellido:this.usuario.apellido,
                            apodo:this.usuario.apodo,
                            correo:this.usuario.correo
                        }
            
            fetch('http://localhost/usuarios.php/?insertar=1',{
                method:"POST",
                body:JSON.stringify(datosEnviar)
            })
            
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta=>{
                    console.log(datosRespuesta);
                    window.location.href='listar';
            }))
        }
    }

}
</script>