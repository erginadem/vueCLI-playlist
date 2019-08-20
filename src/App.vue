<template>
    <div id="app" class="container mt-4">
        <div class="col-sm-12">
            <h1 class="text text-dark">Playlist</h1>
            <hr />
            <form class="form-inline" @submit.prevent="addSong">
                <input type="text" placeholder="artist" class="form-control mr-1" v-model="newSong.artist">
                <input type="text"  placeholder="title" class="form-control mr-1" v-model="newSong.title">

                <button type="submit" class="btn btn-primary">Add to playlist</button>
            </form>
            <hr />
            <ul class="list-group">
                <li class="list-group-item" v-for="(song, index) in songs">
                    <button type="button" name="button" class="btn btn-warning btn-sm">Fav</button>
                    {{ song.artist }} - {{ song.title}}
                    <button type="button" class="btn btn-danger float-right btn-sm" @click="deleteSong(index)">X</button>
                </li>
            </ul>
            <playlist></playlist>
        </div>
    </div>
</template>


<script>
import Playlist from './components/Playlist.vue'

export default {
    name: 'app',

    components: { Playlist },

    methods: {

        addSong(){
            this.songs.splice(0, 0, { artist: this.newSong.artist, title: this.newSong.title });
            this.newSong.artist = '';
            this.newSong.title = '';
        },

        deleteSong(index){
            this.songs.splice(index, 1);
        }
    },

        data() {
            return {
                songs: [
                    { artist: 'Shania Twain', title: 'Feel Like A Woman'},
                    { artist: 'Celine Dion', title: 'It\'s All Coming Back To Me Now'},
                    { artist: 'Justin Bieber', title: 'What Do You Mean?'},
                    { artist: 'Shawn Mendes', title: 'Senorita'},
                    { artist: 'Bryan Adams', title: 'Please Forgive Me'},
                    { artist: 'Avril Lavigne', title: 'Complicated'},
                    { artist: 'The Weeknd', title: 'Starboy'}
                ],

                newSong: {
                    artist: '',
                    title: ''
                }
            }
        }
    }

</script>


<style lang="scss" scoped>

</style>
