<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-sm-6">
                <form v-on:submit.prevent="submit">
                    <div class="form-group row">
                        <label for="title" class="col-sm-3 col-form-label">Title</label>
                        <input type="text" class="col-sm-9 form-control" id="title" v-model="task.title">
                    </div>
                    <div class="form-group row">
                        <label for="year" class="col-sm-3 col-form-label">Year</label>
                        <input type="text" class="col-sm-9 form-control" id="year" v-model="task.year">
                    </div>
                    <div class="form-group row">
                        <label for="country" class="col-sm-3 col-form-label">Country</label>
                        <input type="text" class="col-sm-9 form-control" id="country" v-model="task.country">
                    </div>
                    <div class="form-group row">
                        <label for="description" class="col-sm-3 col-form-label">Description</label>
                        <input type="text" class="col-sm-9 form-control" id="description" v-model="task.description">
                    </div>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
			data: function () {
				return {
					task: {}
				}
			},
			methods: {
				submit () {
					axios.post('/api/tasks', this.task)
						.then((res) => {
							this.$router.push({name: 'task.list'});
						});
				}
			}
		}
</script>