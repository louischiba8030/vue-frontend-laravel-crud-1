<template>
	<div class="container">
		<table class="table table-hover">
			<thead class="thead-light">
				<tr>
					<th scope="col">#</th>
					<th scope="col">Title</th>
					<th scope="col">Year</th>
					<th scope="col">Country</th>
					<th scope="col">Description</th>
					<th scope="col">Show</th>
					<th scope="col">Edit</th>
					<th scope="col">Deltete</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="(task, index) in tasks" :key="index">
					<th scope="row">{{ task.id }}</th>
					<td>{{ task.title }}</td>
					<td>{{ task.year }}</td>
					<td>{{ task.country }}</td>
					<td>{{ task.description }}</td>
					<td>
						<router-link v-bind:to="{name: 'task.details', params: { taskId: task.id.toString() }}">
							<button class="btn btn-primary">Show</button>
						</router-link>
					</td>
					<td>
						<router-link v-bind:to="{name: 'task.edit', params: { taskId: task.id.toString() }}">
							<button class="btn btn-success">Edit</button>
						</router-link>
					</td>
					<td>
						<button class="btn btn-danger">Delete</button>
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
export default {
	data: function () {
		return {
			tasks: []
		}
	},
	methods: {
		getTasks() {
			axios.get('/api/tasks')
				.then((res) => {
					this.tasks = res.data;
				});
		},
		deleteTask(id) {
			axios.delete('/api/tasks/' + id)
				.then((res) => {
					this.getTask();
				});
		}
	},
	mounted() {
		this.getTasks();
	}
}
</script>
