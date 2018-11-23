<template>
    <Page>
        <DockLayout stretchLastChild='true'>
            <DockLayout stretchLastChild='true' class="header" dock="top">
                <Image src="~/assets/images/Fundo.png" dock="top" class="fundo" stretch="fill"/>
            </DockLayout>
            <DockLayout stretchLastChild='true' class="footer" dock="bottom">
                <Image src="~/assets/images/footerBorda.png" dock='left' class="borda"/>
                <Image src="~/assets/images/footerBorda.png" dock='right' class="borda reverso"/>
                <FlexboxLayout dock= "bottom" justifyContent="space-around" class="conteudo-footer">
                    <Image src="~/assets/images/Ping.png" class= "imagem"/>
                    <Image src="~/assets/images/Divisão.png" class= "imagem"/>
                    <Image src="~/assets/images/Livro.png" class= "imagem"/>
                    <Image src="~/assets/images/Divisão.png" class= "imagem"/>
                    <Image src="~/assets/images/Hábitos.png" class= "imagem"/>
                </FlexboxLayout>
            </DockLayout>
            <Label text="teste" dock="right" width="40" backgroundColor="#43b883"/>
        </DockLayout>
    </Page> 
</template> 
<script>
    export default {
        name: 'Map',
        data() {
            return {
                msg: 'foda te etero!'
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
