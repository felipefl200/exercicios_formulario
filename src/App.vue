<template>
	<div id="app">
		<h1>Registrar Reclamação</h1>
		<div class="conteudo">
			<form class="painel">
				<div class="cabecalho">Formulário</div>
				<Rotulo nome="E-mail">
					<!-- Modificadores do v-model => lazy, trim, number. ex: v-model.trim="usuario.email" -->
					<input type="text" v-model="usuario.email">
				</Rotulo>
				<Rotulo nome="Senha">
					<input type="password" v-model="usuario.senha">
				</Rotulo>
				<Rotulo nome="Idade">
					<input type="number" v-model="usuario.idade">
				</Rotulo>
				<Rotulo nome="Mensagem">					
					<textarea name="" cols="30" rows="5" v-model="mensagem"></textarea>
				</Rotulo>
				<Rotulo nome="Características do Problema">
					<span class="mr-4"><input type="checkbox" v-model="caracteristicas" value="reproduzivel"> Reproduzível</span>
					<span><input type="checkbox" v-model="caracteristicas" value="intermitente"> Intermitente</span>
				</Rotulo>
				<Rotulo nome="Qual produto?">
					<span class="mr-4"><input type="radio" v-model="produto" value="web"> Web</span>
					<span class="mr-4"><input type="radio" v-model="produto" value="mobile"> Mobile</span>
					<span><input type="radio" v-model="produto" value="outro"> Outro</span>
				</Rotulo>
				<Rotulo nome="Prioridade">
					<select name="" id="" v-model="prioridade">
						<!-- Se não for definido nenhum value e valor padrão é o nome da option -->
						<option v-for="prioridade in prioridades" :key="prioridade.codigo" :value="prioridade.codigo">{{prioridade.nome}}</option>
					</select>
				</Rotulo>
				<Rotulo nome="Primeira Reclamação?">
					<Escolha v-model="escolha"/>
				</Rotulo>
				<hr>
				<button>Enviar</button>
			</form>
			<div class="painel">
				<div class="cabecalho">Resultado</div>
				<Rotulo nome="E-mail">
					<span>{{usuario.email}}</span>
				</Rotulo>
				<Rotulo nome="Senha">
					<span>{{usuario.senha}}</span>
				</Rotulo>
				<Rotulo nome="Idade">
					<span>{{usuario.idade}}</span>
				</Rotulo>
				<Rotulo nome="Mensagem">
					<!-- Para preservar os espaços em branco e tambem as quebras de linha use o estilo "white-space: pre;" -->
					<span style="white-space: pre;">{{mensagem}}</span>
				</Rotulo>
				<Rotulo nome="Marque as Opções">
					<span>
						<ul>
							<li v-for="opcao in caracteristicas" :key="opcao">
								{{opcao}}
							</li>
						</ul>
					</span>
				</Rotulo>
				<Rotulo nome="Qual produto?">
					<span>{{produto}}</span>
				</Rotulo>
				<Rotulo nome="Prioridade">
					<span>{{prioridade}}</span>
				</Rotulo>
				<Rotulo nome="Primeira Reclamação?">
					<span>{{escolha}}</span>
				</Rotulo>
			</div>
		</div>
	</div>
</template>

<script>
import Rotulo from './components/Rotulo.vue'
import Escolha from './components/Escolha.vue'

export default {
	name: 'app',
	components: { Rotulo, Escolha },
	
	data(){
		return{
			prioridade: 1,
			prioridades: [
				{ codigo: 1, nome: 'Baixa'},
				{ codigo: 2, nome: 'Média'},
				{ codigo: 3, nome: 'Alta'}],
				mensagem: '',
				caracteristicas: [],				
				produto: '',				
				reclamacao: '',
			usuario: {
				email: '',
				senha: '',
				idade: ''				
			},
			escolha: true
		}
	}
}
</script>

<style>

body {
	background-color: #ECECEC;
}

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;

	display: flex;
	flex-direction: column;
}

.conteudo {
	display: flex;
}

.painel {
	flex: 1;
	background: #FFF;
	margin: 0px 10px;
	padding: 20px;
	border: 1px solid #AAA;
	border-radius: 5px;
}

.painel .cabecalho {
	width: 100%;
	background-color: #DDD;
	padding: 10px 0px;
	border-radius: 5px;
	font-size: 1.4rem;
}

#app form button {
	float: right;
	margin: 10px 0px;
	padding: 10px 20px;
	font-size: 1.4rem;
	border-radius: 5px;
	color: #FFF;
	background-color: #2196F3;
}

#app h1 {
	font-weight: 200;
	margin: 20px;
	padding: 0;
}

.mr-4 {
	margin-right: 40px;
}
</style>
