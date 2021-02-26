<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale', dark: theme === 'dark' }" >
            <slot>default content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['header', 'text', 'theme'],
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

<style>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    } 
    h1 {
        color: rgb(2, 182, 173);
        border: none;
        margin-bottom: 8px;
        padding: 0;
    }
    .modal p {
        font-style: normal;
        color: black;
    }
    .modal.sale {
        background: crimson;
        color: white;
    }
    .modal.sale h1 {
        color: white;
    }
    .modal.dark {
        background: rgb(32, 31, 41);
        color: white;
    }
    .modal.dark h1 {
        color: white;
    }
    .modal .actions {
        text-align: center;
        margin: 30px 0 20px 0;
    }
    .modal .actions a {
        color: black;
        padding: 8px;
        border: 1px solid black;
        border-radius: 4px;
        text-decoration: none;
        margin: 0px 10px 0px 10px;
        display: inline-block;
    }
    .modal.dark {
        color: white;
    }
    .modal.dark a {
        color: white;
        border: 1px solid white;
    }
    .modal.sale {
        color: white;
    }
    .modal.sale a {
        color: white;
        border: 1px solid white;
    }
</style>
