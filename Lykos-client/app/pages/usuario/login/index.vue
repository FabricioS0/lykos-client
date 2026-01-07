<script>
</script>

<template>
    <div class="flex flex-col items-center ">
        <h1 class="text-black mt-20">Entre na sua conta</h1>
        <UFormField label="Email" class="text-black w-3/12">
            <UInput label="Email" type="email" placeholder="Entrar com seu email" class="border border-[var(--color-dourado)] pl-2 py-4 w-full rounded placeholder-[var(--color-dourado)]" />
        </UFormField>
        <UFormField label="Senha" class="text-black w-3/12 mt-5">
            <UInput label="Senha" type="email" placeholder="Entrar com sua senha" class="border border-[var(--color-dourado)] pl-2 py-4 w-full rounded placeholder-[var(--color-dourado)]" />
        </UFormField>

        <a href="" class="text-[var(--color-dourado)] mt-5">Esqueceu a senha?</a>
        <div class="w-3/12">
            <button class="bg-[var(--color-dourado)] text-white  py-2 rounded-full  rounded mt-10 mb-10 cursor-pointer w-full">
            Entrar  
        </button>
        </div>
        <p class="text-[var(--color-dourado)] mt-5">Ja tem uma conta?</p>

            <button class="border border-[var(--color-dourado)] text-[var(--color-dourado)] bg-white p-2   rounded mt-10 mb-10 cursor-pointer ">
            Criar Conta 
        </button>

        
    </div>
</template>