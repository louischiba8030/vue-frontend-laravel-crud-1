<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-sm-6">
                <form>
                    <div class="form-group row border-bottom">
                        <label for="id" class="col-sm-3 col-form-label">ID</label>
                        <input type="text" class="col-sm-9 form-control-plaintext" readonly id="id"
                               v-model="task.id">
                    </div>
                    <div class="form-group row border-bottom">
                        <label for="title" class="col-sm-3 col-form-label">Title</label>
                        <input type="text" class="col-sm-9 form-control-plaintext" readonly id="title"
                               v-model="task.title">
                    </div>
                    <div class="form-group row border-bottom">
                        <label for="year" class="col-sm-3 col-form-label">Year</label>
                        <input type="text" class="col-sm-9 form-control-plaintext" readonly id="year"
                               v-model="task.year">
                    </div>
                    <div class="form-group row border-bottom">
                        <label for="country" class="col-sm-3 col-form-label">Country</label>
                        <input type="text" class="col-sm-9 form-control-plaintext" readonly id="country"
                               v-model="task.country">
                    </div>
                    <div class="form-group row border-bottom">
                        <label for="description" class="col-sm-3 col-form-label">Description</label>
                        <input type="text" class="col-sm-9 form-control-plaintext" readonly id="description"
                               v-model="task.description">
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            taskId: String
        },
				data: {
					function () {
						return {
							task: {}
						}
					}
				},
				methods: {
					getTask() {
						axios.get('/api/tasks/' + this.taskId)
							.then((res) => {
								this.task = res.data;
							});
					}
				},
				mounted () {
					this.getTask();
				}
    }
</script>