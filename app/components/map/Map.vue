<template>
    <Page>
        <DockLayout stretchLastChild='true'>
            <DockLayout stretchLastChild='true' class="header" dock="top">
                <Image v-if="this.tela == 1" src="~/assets/images/CentrosAjudaHeader.png" dock="top" class="fundo" stretch="fill"/>
                <Image v-else-if="this.tela == 2" src="~/assets/images/PsicotropédiaHeader.png" dock="top" class="fundo" stretch="fill"/>
                <Image v-else src="~/assets/images/HábitosHeader.png" dock="top" class="fundo" stretch="fill"/>
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
            <StackLayout class="conteudo" v-if="this.tela == 1" dock="right">
                <Label class="titulo" text="oi" dock="right" width="40" backgroundColor="#43b883"/>
            </StackLayout>
            <StackLayout class="conteudo" v-else-if="this.tela == 2" dock="right">
                <Label class="titulo" text="hehe" dock="right" width="40" backgroundColor="#ffffff"/>
            </StackLayout>
            <StackLayout class="conteudo" v-else text="eae" dock="right">
                <Label class="titulo" text="eae" dock="right" width="40" backgroundColor="#000000"/>
            </StackLayout>
        </DockLayout>
    </Page> 
</template> 
<script>
    export default {
        name: 'Map',
        data() {
            return {
                tela: 1
            }
        },
        methods: {
            view(i){
                this.tela = i;
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
        font-size: 16em;
        color: #005876;
        min-width: 50px;
        min-height: 50px;
        background: black;
        margin-left: 30px;
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

    .conteudo{
        height: 100%;
        width: 100%;
    }
</style>