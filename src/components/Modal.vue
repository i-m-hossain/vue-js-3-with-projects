<template>
    <div class="back-drop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme=== 'sale', dark: theme ==='dark'}" >
           <slot>Default content</slot>
           <div class="actions">  
                <slot name="links"></slot>
                <slot name="sign"></slot>
           </div>
        </div>
        
        <div>
            
            <button v-if="!(theme == 'sale')" @click="theme='sale'"> Light </button>
            <button v-if="!(theme == 'dark')" @click="theme= 'dark'"> Dark </button>
            <button v-if="!(theme == '')" @click="theme= ''"> Default </button>
            
        </div>
    </div>
</template>


<script>

export default {
    
    props: ['theme'],
    methods: {
        closeModal(){
            this.$emit('close')
        },
        
    },

}
</script>


<style >
    .back-drop{
       
        width:100%;
        height:100%;
        top: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.5);

        

    }
    .modal{
        width: 400px;
        background:#fff;
        margin: 100px auto;
        padding: 20px;
        border-radius: 10px;

    }
    .modal h1{
        text-align:center;
        color: rgb(21, 126, 126);
    }
    .modal p{
        text-align:center;
    }
    .modal.sale{
        background: crimson ;
        color: white;
    }

    .sale h1{
        color: #fff;
    }
    .modal.dark{
        background: #112233;
        color: white;
    }
    .dark h1{
        color: white;
    }
    .modal .actions{
        text-align: center;
        margin: 30px 0 10px 0;
    } 
    .modal .actions a{
        text-decoration: none;
        padding: 10px;
        margin: 0 5px;
        border: 1px solid #eee;
        border-radius: 5px;
        color: #333
    }
    
    .dark .actions a{
        text-decoration: none;
        padding: 10px;
        margin: 0 5px;
        border: 1px solid #eee;
        border-radius: 5px;
        color: #fff
    }
    
    .sale .actions a{
        text-decoration: none;
        padding: 10px;
        margin: 0 5px;
        border: 1px solid #eee;
        border-radius: 5px;
        color: #fff
    }
    .change-modal{
        margin-bottom: 30px;

    }
</style>