# Client

# Collections: Logs, Tasks, Users

# npm start ---> carrega no navegador (http://localhost:3000/)

# api::::::::::::::::::::::::::::::::::::::::

==>>api.js (70)
....configura o AXIOS PARA api.xxx
....insere token de localStorage para headers de cada requisição
....ajusta a URL para development ou production, conforme o caso

# components::::::::::::::::::::::::::::::::::::::::

==>>EditUser.js (71)
#put("/user/edit")
....Modal - Formulario - Editar nome do usuário

==>>NavBar.js (73)
....TODOS Links (logado/s-n)
..../ -> Pagina Inicial
..../profile -> Perfil
..../tasks -> Minhas Tarefas
..../notificacoes -> Notificações
..../login -> Login
..../sign-up -> Cadastre-se

==>>ProtectRoute.js (74)
....Recebe como parametro um componente
....Executa componente se logado
....navega para /login se não estiver logado

# contexts::::::::::::::::::::::::::::::::::::::::

==>>authContext.js (75)
....cria um ambiente de contexto com dados que abraçam todo app
....na primeira execução pega os dados de localStorage
....loggedInUser, setLoggedInUser

# pages::::::::::::::::::::::::::::::::::::::::

==>>ErrorPage.js (76)
....Retorna uma div com uma mensagem "página não existe"

==>>HomePage.js (77)
....Mostra na tela três botões ( CADASTRAR, ENTRAR, PERFIL )
....Os botões referem-se a links ( /sign-up, /login, /profile)

==>>LoginPage.js (78)
#post("/user/login")
....Pede em FORMULÁRIO email, senha -> valida no BD
....Se ok: ajusta localStorage e setLoggedInUser
....Mostra link para novo cadastro (/sign-up)

==>>NotificationPage.js (80)
#get("/log/my-logs")
....Mostra todas as notificações do BD (alterações da BD)

==>>ProfilePage.js (81)
#get("/user/profile")
#delete("/user/delete")
....Permite Logout (signOut)
....Permite Deletar o usuário \***\*\*\*\*\*\*\*** CONFERIR QUAL É EXCLUIDO
....Permite clicar Link /tasks (Minhas Tarefas)
....Mostra dados e foto do usuário logado
....Insere no corpo desta página um componente: EditUser (passando parametros)

==>>SignUpPage.js (83)
#post("/uploadImage/upload")
#post("/user/sign-up")
....Pede em FORMULÁRIO nome,email,senha,confirma senha,foto
....Tem link para /login (se já possuir cadastro)

==>>TasksPage.js (86)
#get("/task/my-tasks")
#post("/task/create-task")
#put("/task/edit/${idTask}")
#delete("/task/delete/${idTask}")
#put("/task/complete/${idTask}")
....Pede em FORMULÁRIO descrição da tarefa, data de finalização
....Mostra lista de tarefas com botões EXCLUIR, FINALIZAR, ALTERAR STATUS

# / ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

==>>App.js (89)
....Contexto de ambiente (dados do usuário logado) - ABRAÇA TUDO
....Chama todas as rotas (protegidas e não protegidas)
....Chama componente NavBar dentro Contexto e acima das Rotas
....Chama rota de exceção para mensagem de erro

==>>index.js (90)
....Padrão, chamando apenas componente App
