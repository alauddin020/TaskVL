<template>
<div>
    <div class="card card-default">
        <div class="card-header"><strong>{{user.name}} Information</strong></div>
        <div class="card-body">
            <table class="table">
                <tr>
                    <th scope="col">Id</th>
                    <th scope="col">Nom</th>
                    <th scope="col">Email</th>
                    <th scope="col">Created At</th>
                </tr>
                <tr style="margin-bottom: 5px;">
                    <th scope="row">{{user.id }}</th>
                    <td>{{ user.name }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.created_at}}</td>
                </tr>
            </table>
        </div>
    </div>
    <div class="alert alert-danger" v-if="has_error">
        <p></p>
    </div>
</div>
</template>
<script>
  export default {
    data() {
      return {
        has_error: false,
        users: null,
        user:{}
      }
    },
    mounted() {
      this.getUsers()
    },
    methods: {
      getUsers() {
        this.$http({
          url: `user`,
          method: 'GET'
        }).then((res) => {
            this.user = res.data.user
            }, () => {
              this.has_error = true
            })
      }
    }
  }
</script>
