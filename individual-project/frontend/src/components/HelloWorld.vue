<template>
  <div class="hello">
   <!-- <nav class="navbar navbar-dark bg-primary">
      <div class="container">
        <div class="navbar-header">
          <ul class="nav  nav-pills justify-content-center">
            <h1>Accounts System</h1>
               <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button" aria-haspopup="true" aria-expanded="false">Accounts</a>
               <div class="dropdown-menu">
              <a class="dropdown-item" href="#">Add Accounts</a><br>
              <a class="dropdown-item" href="#">Get Accounts</a>
              </div>
            </li>
          </ul>
        </div>
        </div>
      </nav> -->
    <form method='post' @submit.prevent='postaccount'>
      <div class="form-group">
      <label>FirstName</label>
      <input type="text" class="form-control" v-model="firstName" id="firstName">
      </div>
      <div class="form-group">
      <label>Lastname</label>
      <input type="text" class="form-control" v-model="lastName" id="lastName">
      </div>
      <div class="form-group">
      <label for="accountnumberinput">Account Number</label>
      <input type="text" class="form-control" v-model="accountnumber" id="accountnumberinput" placeholder="Enter Account number">
      </div>
      <div id="addaccounts">
      <button type='submit' class='submit' vclass=â€�Search__buttonâ€� @click="postaccount()">Addaccounts</button>
      </div>
    </form>
    <form>
        <div id="getaccounts">
      <button  vclass=â€�Search__buttonâ€� @click="test()">Get Accounts</button>
      </div>
       <input type="text" id="inputid" class="form-control" placeholder="Enter ID Number">
      <button  vclass=â€�Search__buttonâ€� @click="getbyId()">Search by ID</button>
      </form>
      <table class="table table-hover table-bordered table-striped">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>First Name</th>
                                <th>Last Name</th>
                                <th>Account Number</th>
                            </tr>
                        </thead>
                        <tbody>
                               <tr v-for="detail in details" :key="detail-id">
                                 <td>{{detail.id}}</td>
                                <td>{{detail.firstName}}</td>
                                <td>{{detail.lastName}}</td>
                                <td>{{detail.accountnumber}}</td>
                                <td><button type="button" class="btn btn-default btn-sm">
          <span class="glyphicon glyphicon-edit" style="color:green;" @click="putaccount(detail,detail.id)"></span></button></td>
                                <td> <button type="button" class="btn btn-default btn-sm">
          <span class="glyphicon glyphicon-remove-circle" style="color:red;" @click="deleteaccount(detail, detail.id)"></span></button></td></tr>
                        </tbody>
       </table>
 </div>
</template>

<script>
/* eslint-disable */
import axios from 'axios'
export default {
 name: 'HelloWorld',
  data () {        
    return {
          details:[],
          firstName: '',
          lastName:'',
          accountnumber:''
        }
      },
     methods: {
      test:function() {
        axios.get('http://localhost:8080/AccountDetails')
          .then(response => {
             this.details = response.data
             console.log(JSON.stringify(response.data))
          })
          .catch(error => {
            console.log = error.response

      });
      },
      getbyId:function () {
          axios.get('http://localhost:8080/AccountDetails/' + inputid)
            .then(response => {
              this.details = response.data
            })
            .catch(error => {
             console.log = error.response 
            });
      },
      postaccount: function () {
        axios.post('http://localhost:8080/AccountDetails',{firstName:this.firstName,lastName:this.lastName,accountnumber:this.accountnumber,
          }).then(response =>{
          console.log = ('response',JSON.stringify(response))
      })
    },
      deleteaccount: function(details, id) {
        axios.delete('http://localhost:8080/AccountDetails/'+ id)
          .then(response => {
            this.details = response.data
          });
      },
      editaccount: function(details, id) {
        axios.put('http://localhost:8080/AccountDetails/' + id, {firstName:this.firstName,lastName:this.lastName,accountnumber:this.accountnumber,
           }).then(response =>{
                this.details = response.data
        })
      } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
