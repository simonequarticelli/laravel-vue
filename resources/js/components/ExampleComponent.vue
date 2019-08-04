<template>

        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">All todos</div>

                    <div class="card-body">
                        <ul>
                          <li v-for="single_todo in todos"><strong>Title: </strong>{{ single_todo.title }}<br>
                            <strong>Completed: </strong>{{ single_todo.completed }}</li>
                        </ul>
                
                    </div>
                </div>
            </div>
        </div>

</template>

<script>
    export default {
      data: function() {
        return {
          //passo l'array ricevuto dalla chiamata
          todos: []
        }
      },
        mounted() {
            //console.log('Component mounted.')

            // Make a request for a user with a given ID
            axios.get('https://jsonplaceholder.typicode.com/todos')
              .then(response => {
                // handle success
                this.todos = response.data
                console.log(response.data);
              })
              .catch(function (error) {
                // handle error
                console.log(error);
              })
              .finally(function () {
                // always executed
              });
        }
    }
</script>
