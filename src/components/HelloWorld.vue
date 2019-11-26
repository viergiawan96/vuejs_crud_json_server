<template>
  <div>
      <div class="d-flex flex-row" style="margin-left: 15px; margin-bottom: 15px;">
        <button id="show-modal" href="/#Tambah" @click.prevent="show" type="button" class="btn btn-success float-left p-2">Tambah</button>
      </div>
      <div style="margin-top: 15px;">
          <table class="table table-hover">
          <thead>
            <tr>
              <th>Nama</th>
              <th>Email</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" :key="user.idd">
              <td>{{user.name}}</td>
              <td>{{user.email}}</td>
              <td>
                <button style="margin-right: 10px" type="button" class="btn btn-outline-info">Tampilkan</button>
                <button style="margin-right: 10px" type="button" class="btn btn-outline-primary">Ubah</button>
                <button type="button" class="btn btn-outline-danger">Hapus</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <modal name="modal-tambah" :adaptive="true" :width="400">
            <div class="modal-header">
                <h4 class="modal-title">Tambah Siswa</h4>
            </div>
            <div class="modal-body">
                <form @submit.prevent="add">
                    <input type="hidden" v-model="form.id">
                    <div class="form-group">
                        <label for="email">Email address:</label>
                        <input v-model="form.name" name="email" type="email" class="form-control" id="email">
                    </div>
                    <div class="form-group">
                        <label for="name">name:</label>
                        <input v-model="form.email" name="name" type="text" class="form-control" id="name">
                    </div>
                    <button style="margin:auto; display:block;" type="submit" class="btn btn-outline-success">Submit</button>
                 </form>     
            </div>
        </modal>
  </div>
</template>

<script>
/* eslint-disable */ 
import axios from 'axios'

export default {
  data(){
    return{
        form: {
          id: '',
          name: '',
          email: ''
        },
        users: ''
    }
  },
  mounted() {
    this.load()
  },
  methods: {
      load(){
          axios.get('http://localhost:3000/users').then(res => {
          this.users = res.data
        }).catch ((err) => {
          console.log(err);
          
        })
      },
      show() {
              this.$modal.show('modal-tambah')
          },
      hide() {
              this.$modal.hide('modal-tambah')
          }, 
      add(){
          axios.post('http://localhost:3000/users/', this.form).then(res => {
              this.load()
              this.form.name = ''
              this.form.email=''
              this.$modal.hide('modal-tambah')
          })
          }
     }
}
</script>