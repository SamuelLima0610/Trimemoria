<template>
    <div>
        <b-card no-body class="overflow-hidden" style="max-width: 740px; max-height: 500px">
            <b-row no-gutters>
                <b-col md="6">
                   <b-img :src="img" fluid alt="Responsive image"></b-img>
                </b-col>
                <b-col md="6">
                    <b-card-body :title="emocao">
                        <Media 
                            :kind="'audio'"
                            :controls="true"
                            :autoplay="true"
                            :src="audio"
                            slot="music"
                        >
                        </Media>
                    </b-card-body>
                </b-col>
            </b-row>
        </b-card>
    </div>
</template>

<script>
import Media from '@dongido/vue-viaudio'
export default {
    components:{Media},
    props:[
        'emocao',
        'img',
        'audio'
    ],
    mounted(){
        document.getElementById('tocar').play();
    }
}
</script>

<style scoped>
</style>