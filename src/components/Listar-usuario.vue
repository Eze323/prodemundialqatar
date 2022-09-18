<template>
    <div>
        Hola Listar es esta pagina


            <div v-for="usuario in usuarios" :key="usuario.id"> 
                <div>{{usuario.id}}</div>
                <div>{{usuario.nombre}}</div>
                <div>{{usuario.apellido}}</div>
                <div>{{usuario.apodo}}</div>
                <div>{{usuario.correo}}</div>
                <a name="" id="" class="btn btn-primary" href="#" role="button">editar</a>
                <a name="" id="" class="btn btn-primary" href="#" role="button">borrar</a>

            </div>


    </div>
</template>
<script>
export default {
        data(){
            return{
                usuarios:[]
            }
        },

    created:function(){
            this.consultarUsuarios();
    },
    methods:{
        //http://localhost/usuario.php
        consultarUsuarios(){
            fetch('http://localhost/usuarios.php/')
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta)=>{
                console.log(datosRespuesta)
                this.usuarios=[]
                if(typeof datosRespuesta[0].success==='undefined' ){
                    this.usuarios=datosRespuesta;
                }
            })
            .catch(console.log)
        }
    }
}
</script>