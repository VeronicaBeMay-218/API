
<script>


export default {


props:{
    personaje:obeject

},
data(){

    return{

    }

},

computed: {
    traducirSolicitud(){
        switch (this.personajes.status){
            case 'alive':
            return 'vivo'
            break;

            case 'Unknow':
            return 'desconocido'
            break;
            case 'Dead':
            return 'muerto'
            break;
            default:
                break;


        }


    }
},
}


</script>

<template>
    <div>
        <img v.bind:src="personajes.image" v.bind:alt="personajes.name">

    </div>
</template>