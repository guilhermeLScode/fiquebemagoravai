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
                 <Mapbox
                    accessToken="pk.eyJ1IjoibHVpc2VkdGVpeGVpIiwiYSI6ImNqb3RqMmxpaTExeTUzcXBpZjBjeGtxcmwifQ.AqUCsWIMZoHRbUIv4NHM5A"
                    mapStyle="traffic_day"
                    latitude='-29.8142167'
                    longitude='-51.1533123'
                    hideCompass="true"
                    zoomLevel="12"
                    showUserLocation="false"
                    disableZoom="false"
                    disableRotation="false"
                    disableScroll="false"
                    disableTilt="false"
                    @mapReady="onMapReady($event)">
                </Mapbox>
            </StackLayout>
            <StackLayout class="conteudo" v-else-if="this.tela == 2" dock="right">
                <Label class="titulo" text="eae" dock="right" width="40" backgroundColor="#ccffff"/>
                <FlexboxLayout class="artigo" :key="artigo.id" v-for="artigo in artigosList" flexDirection="column">
                                      <Label class="artigo-titulo" flexGrow="1" :text="artigo.titulo"/>
                    <TextView class="artigo-conteudo" flexGrow="5" v-model="artigo.descricao"/>
                </FlexboxLayout>    
            </StackLayout>
            <StackLayout class="conteudo" v-else text="eae" dock="right">
                <Label class="titulo" text="eae" dock="right" width="40" backgroundColor="#000000"/>
                <StackLayout class="artigo" :key="habito.id" v-for="habito in artigosList">
                </StackLayout>
            </StackLayout>
        </DockLayout>
    </Page> 
</template> 
<script>
    export default {
        name: 'Map',
        data() {
            return {
                artigosList: [
                {
                    titulo: 'Puta merda quero dar o cu',
                    descricao: 'daocu daocu daocu daocu'
                            +'daocu daocu daocu daocu' 
                            +'daocu daocu daocu daocu' 
                            +'daocu daocu daocu daocu'
                },
                {
                titulo: 'Puta merda quero dar o cu',
                descricao: 'daocu daocu daocu daocu'
                            +'daocu daocu daocu daocu' 
                            +'daocu daocu daocu daocu' 
                            +'daocu daocu daocu daocu'
                }],
                tela: 1,
                latitude: '-29.8587727',
                longitude: '-51.1599591,17'
            }
        },
       methods: {
            onMapReady(args) {
                       
                var geolocation = require("nativescript-geolocation");
                geolocation.isEnabled().then(function (isEnabled) {
                    if (!isEnabled) {
                        geolocation.enableLocationRequest().then(function () {
                            
                        }, function (e) {
                            console.log("Error: " + (e.message || e));
                        });
                    } else {
                         let location = geolocation.getCurrentLocation({desiredAccuracy: 3, updateDistance: 10, maximumAge: 20000, timeout: 20000})
                            .then(function(resp) {

                                let http = require('http');
                                http.getJSON('http://192.168.15.12:8080/getAllpoints')
                                    .then(function(points) {
                                        let pointsToAdd = [];
                                        points.map(point => {
                                            let pointToAdd = {
                                                lat: point.coordenadas.coordinates[0],
                                                lng: point.coordenadas.coordinates[1],
                                                title: point.nome,
                                                subtitle: point.endereco + ' ' + point.telefone,
                                                onCalloutTap: () => {
                                                    utils.openUrl("https://www.thepolyglotdeveloper.com");
                                                }
                                            }
                                            pointsToAdd.push(pointToAdd);
                                        })  
                                        args.map.addMarkers(pointsToAdd);
                                    }, function() {})
                            
                        }, function (e) {
                            console.log("Error: " + (e.message || e));
                        });
                    }
                });
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

    .artigo{
        height: auto;
        margin-left: 50px;
        margin-right: 50px;
        box-shadow: 0 0 10px black;
        background: #3CA7CC;
        margin-top: 30px;

    }

    .titulo{
        margin-top: 30px;
        font-size: 16em;
        color: black;
        min-width: 50px;
        min-height: 50px;
        background: #3ca7cc;
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