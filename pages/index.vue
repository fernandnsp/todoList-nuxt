<template>
	<div>
		<v-container style="max-width: 760px; min-width: 320px">
			<h1 class="mt-8 mb-4">ToDo List</h1>
			<v-row>
				<v-col cols="12" class="pb-0 d-flex">
					<v-text-field
						v-model.trim="novaTask"
						type="text"
						background-color="white"
						filled
						@keyup.enter.prevent="enviarTask"
						label="Insira aqui a tarefa"
						class="d-flex"
						elevation="2"
					></v-text-field>

					<v-btn
						small
						height="57px"
						class="rounded-l-0"
						light
						elevation="0"
						color="primary"
						@click="enviarTask"
					>
						Adicionar
					</v-btn>
				</v-col>
			</v-row>

			<v-divider class="my-4 mt-2"></v-divider>

			<v-row>
				<v-col cols="12">
					<Task />
				</v-col>
			</v-row>
		</v-container>
	</div>
</template>

<script>
	export default {
		name: 'IndexPage',
		computed: {
			novaTask: {
				get(){
					return this.$store.state.newTask
				},
				set(value){
					this.$store.commit('READ_TASK', value)
				}
			}
		},
		methods: {
			enviarTask(){
				if(this.novaTask){
					this.$store.dispatch('setTask', this.novaTask)
					this.novaTask = ''
				}
			}
		},
	}
</script>