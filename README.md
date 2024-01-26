![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D)

## Dashboard | Teste Técnico

O projeto aqui encontrado se trata de um desafio técnico em Vue.js e foi desenvolvido com base em requisitos pré-estabelecidos pela empresa. Ele foi realizado utilizando as seguintes tecnologias, conforme a própria documentação do desafio:

![Nuxtjs](https://img.shields.io/badge/Nuxt-002E3B?style=for-the-badge&logo=nuxtdotjs&logoColor=#00DC82)

![SASS](https://img.shields.io/badge/SASS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white)
## Deploy

https://frontend-case-nu.vercel.app/

## Instalação de dependências
Certifique-se de ter o Node instalado em sua máquina. Clone o repositório e, no diretório do projeto, execute um dos seguintes comandos pelo terminal, de acordo com o gerenciador de pacotes de sua preferência:
```bash
  npm install
```
```bash
  yarn install
```
    
## Rodando o Ambiente de Desenvolvimento
Para iniciar a aplicação em modo de desenvolvimento, utilize um dos comandos a seguir:
```bash
  npm run dev
```
```bash
  yarn dev
```
Em seguida, abra seu navegador e acesse http://localhost:3000


## Estrutura do Projeto
Abaixo, algumas informações sobre minhas escolhas e tomadas de decisão durante o andamento do projeto:

* Elementos SVG que ocupariam linhas e dificultariam a legibilidade do código foram componentizados e movidos para as pastas /icons e /emojis em /components
* Todos os componentes do projeto encontram-se devidamente isolados, recebendo props vindas do index, garantindo assim que sejam carregados dinamicamente
* Adicionei o máximo possível de interatividade aos componentes, dado meu tempo disponível para o desafio:
    - Rastreador de Tempo: cronômetro funcional, com opções de parar, pausar, retomar e iniciar. Ao parar uma gravação, a mesma é registrada e aparece no topo das 'Tarefas Anteriores'
    - Horas diárias: poderia fazer um preenchimento dinâmico das barrinhas em CSS, mas me tomaria tempo desnecessariamente. O botão de exibir detalhes apenas imprime no console o ato de clique
    - Cursos - Progresso: novamente, um preenchimento dinâmico aqui me tomaria tempo, portanto, apenas criei funções para imprimir no console ao clicar nos botões
    - Destaque Colaboradores: na aba de 'Comentários' é possível curtir ou descurtir os comentários. Também é possível adicionar um comentário com o usuário atual, que ficará exibido no topo da lista
    - Cursos: o campo de pesquisa irá filtrar pelo nome do curso. O clique no botão irá imprimir na tela que o usuário deseja visualizar todos os cursos
    - Feedback diário: é possível escolher um mood e adicionar um comentário
## Autor

- [@zaqueu-1](https://www.github.com/zaqueu-1)
Acesse também meu [LinkedIn](https://linkedin.com/in/zaqueu1) e dê uma olhada em meu [portfolio](https://zaqueu.tech)!

