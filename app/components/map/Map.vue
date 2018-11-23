<template>
    <Page>
        <DockLayout stretchLastChild='true'>
            <DockLayout stretchLastChild='true' class="header" dock="top">
                <Image src="~/assets/images/Fundo.png" dock="top" class="fundo" stretch="fill"/>
                <Label :text="msg" dock="left" class="titulo"/>
            </DockLayout>
            <DockLayout stretchLastChild='true' class="footer" dock="bottom">
                <Image src="~/assets/images/footerBorda.png" dock='left' class="borda"/>
                <Image src="~/assets/images/footerBorda.png" dock='right' class="borda reverso"/>
                <FlexboxLayout dock= "bottom" justifyContent="space-around" class="conteudo-footer">
                    <Image @tap="view(1)" src="~/assets/images/Ping.png" class= "imagem"/>
                    <Image src="~/assets/images/Divisão.png" class= "imagem"/>
                    <Image @tap="view(2)" src="~/assets/images/Livro.png" class= "imagem"/>
                    <Image src="~/assets/images/Divisão.png" class= "imagem"/>
                    <Image @tap="view(3)" src="~/assets/images/Hábitos.png" class= "imagem"/>
                </FlexboxLayout>
            </DockLayout>
            <Label v-if="this.tela == 1" text="teste" dock="right" width="40" backgroundColor="#43b883"/>
            <Label v-else-if="this.tela == 2" text="teste" dock="right" width="40" backgroundColor="#ffffff"/>
            <Label v-else text="teste" dock="right" width="40" backgroundColor="#000000"/>
        </DockLayout>
    </Page> 
</template> 
<script>
    export default {
        name: 'Map',
        data() {
            return {
                msg: 'Pontos de ajuda',
                tela: 1
            }
        },
        methods: {
            view(i){
                this.tela = i;
                if(i == 1){
                    this.msg = "Pontos de ajuda"
                }
                else if(i == 2){
                    this.msg = "Psicotropédia"
                }
                else{
                    this.msg = "Hábitos"
                }
            }
        }
    }
</script>
<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .footer{
        background: #EFEFEF;
    }

    .titulo{
        font-size: 1.8em;
        color: #005876;
        text-decoration: underline;
    }

    .borda{
        height: 150px;
    }

    .reverso{
        transform: scaleX(-1)
    }

    .header{
        background: #EFEFEF;
        margin: 0;
        height: 150px;
    }

    .imagem{
        height: 103.125px;
        margin-top: 23.4385px;
    }
</style>
