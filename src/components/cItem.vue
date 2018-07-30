<template>
    <tr>
      <td>{{id}}</td>
      <td>{{nombre}}</td>
    </tr>
</template>
<script>
export default {
    props: {
        id:{
            type: Number,
            required:true
        },
        nombre:{
            type: String,
            required:true
        }
    }
}
</script>