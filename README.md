# app-autenticacao-login

Aplicação frontend em React para autenticação simples com tela de login, contexto de autenticação, rota privada e página interna protegida.

O projeto utiliza Create React App, React Router, Context API, LocalStorage e Styled Components para simular um fluxo básico de login. Ele pode servir como base inicial para telas internas, protótipos de autenticação ou estudos de proteção de rotas no frontend.

> Nome anterior/repositório de origem: `React-login`.

## O que este projeto faz

- Sobe uma aplicação frontend em React.
- Utiliza Create React App como base de execução e build.
- Utiliza React Router DOM para controle de rotas.
- Utiliza Context API para controlar o estado de autenticação.
- Utiliza hook customizado `useAuth` para acessar autenticação.
- Utiliza LocalStorage para armazenar token simulado.
- Exibe tela de login na rota `/`.
- Exibe página interna protegida na rota `/home`.
- Redireciona usuário não autenticado para a tela de login.
- Permite encerrar sessão pelo botão `Sair`.
- Utiliza Styled Components para estilização.
- Possui componentes reutilizáveis de input e botão.
- Possui estrutura simples para evolução futura com autenticação real via API.
- Está preparado para ser usado como base de estudo, protótipo ou tela inicial de sistemas internos.

## Módulos disponíveis

### Tela de login

Rota:

```text
/
```

Arquivo principal:

```text
src/pages/Signin/index.js
```

Objetivo:

- exibir formulário de login;
- capturar usuário e senha;
- validar se os campos foram preenchidos;
- chamar função `signin`;
- exibir mensagem de erro quando necessário;
- redirecionar para `/home` após login válido.

Campos atuais:

```text
Usuário
Senha
```

Mensagem de erro possível:

```text
Preencha todos os campos
Usuário não cadastrado
Usuário ou senha incorretos
```

---

### Página interna protegida

Rota:

```text
/home
```

Arquivo principal:

```text
src/pages/Home/index.js
```

Objetivo:

- exibir página interna após autenticação;
- permitir logout;
- redirecionar usuário para `/` após sair.

---

### Controle de rotas

Arquivo principal:

```text
src/routes/index.js
```

Objetivo:

- configurar rotas da aplicação;
- proteger rota `/home`;
- renderizar `Signin` quando usuário não estiver autenticado;
- redirecionar rotas desconhecidas para login.

Rotas atuais:

```text
/       Login
/home   Página protegida
*       Login
```

---

### Contexto de autenticação

Arquivo principal:

```text
src/contexts/auth.js
```

Objetivo:

- criar contexto de autenticação;
- armazenar usuário autenticado no estado;
- verificar token salvo no LocalStorage;
- executar login;
- executar logout;
- disponibilizar `user`, `signed`, `signin` e `signout` para a aplicação.

---

### Hook de autenticação

Arquivo principal:

```text
src/hooks/useAuth.js
```

Objetivo:

- encapsular o uso do `AuthContext`;
- facilitar o acesso ao estado de autenticação em qualquer componente.

---

### Componentes reutilizáveis

Arquivos principais:

```text
src/components/Input/index.js
src/components/Button/index.js
```

Objetivo:

- padronizar campos de entrada;
- padronizar botão principal;
- manter os estilos isolados em arquivos próprios.

## Fluxo operacional

O fluxo principal segue esta sequência:

```text
usuário acessa /
→ informa usuário e senha
→ Signin chama signin()
→ AuthContext valida as credenciais locais
→ sistema gera token simulado
→ token é salvo no localStorage
→ usuário é redirecionado para /home
→ rota privada verifica signed
→ Home é exibida
→ usuário clica em Sair
→ signout remove token do localStorage
→ usuário volta para /
```

## Estrutura do usuário autenticado

Exemplo simplificado do usuário usado no contexto:

```json
{
  "email": "SuporteReact",
  "password": "senha_exemplo"
}
```

Atenção:

```text
no código atual, o campo usado como login é chamado de email, mas o valor real representa um usuário
```

## Estrutura do token local

Exemplo simplificado do token salvo no LocalStorage:

```json
{
  "email": "SuporteReact",
  "token": "abc123token"
}
```

Chave usada no LocalStorage:

```text
user_token
```

Atenção:

```text
o token atual é apenas uma string aleatória gerada no frontend
ele não representa uma sessão segura
não há validação em servidor
não há expiração
não há assinatura
não há refresh token
```

## Credencial local de teste

O projeto possui uma credencial local fixa no código.

Arquivo:

```text
src/contexts/auth.js
```

Uso atual:

```text
login local de demonstração
```

Atenção:

```text
não usar credenciais fixas no frontend em produção
não publicar usuários e senhas reais no GitHub
substituir por autenticação via backend, Supabase, Firebase, OAuth, JWT ou outro provedor seguro
```

## Como executar

### 1. Instalar dependências

Na raiz do projeto:

```bash
npm install
```

Ou, se optar por Yarn:

```bash
yarn install
```

### 2. Executar em ambiente local

Com npm:

```bash
npm start
```

Com Yarn:

```bash
yarn start
```

A aplicação ficará disponível em:

```text
http://localhost:3000
```

### 3. Executar testes

Com npm:

```bash
npm test
```

Com Yarn:

```bash
yarn test
```

### 4. Gerar build de produção

Com npm:

```bash
npm run build
```

Com Yarn:

```bash
yarn build
```

O build final será salvo em:

```text
build/
```

## Scripts disponíveis

### `npm start`

Executa a aplicação em modo desenvolvimento.

```bash
npm start
```

### `npm run build`

Gera a versão de produção.

```bash
npm run build
```

### `npm test`

Executa o ambiente de testes padrão do Create React App.

```bash
npm test
```

### `npm run eject`

Remove a abstração do Create React App.

```bash
npm run eject
```

Atenção:

```text
não executar npm run eject sem necessidade real
essa ação é difícil de reverter
```

## Arquivos principais

```text
app-autenticacao-login/
├── .gitignore
├── README.md
├── package.json
├── package-lock.json
├── yarn.lock
├── public/
│   └── index.html
└── src/
    ├── App.js
    ├── index.js
    ├── components/
    │   ├── Button/
    │   │   ├── index.js
    │   │   └── styles.js
    │   └── Input/
    │       ├── index.js
    │       └── styles.js
    ├── contexts/
    │   └── auth.js
    ├── hooks/
    │   └── useAuth.js
    ├── pages/
    │   ├── Home/
    │   │   ├── index.js
    │   │   └── styles.js
    │   └── Signin/
    │       ├── index.js
    │       └── styles.js
    ├── routes/
    │   └── index.js
    └── styles/
        └── global.js
```

### `package.json`

Arquivo de configuração do projeto React.

Nome atual observado:

```text
react-login
```

Ajuste recomendado:

```json
{
  "name": "app-autenticacao-login"
}
```

Principais dependências:

```text
react
react-dom
react-router-dom
react-scripts
styled-components
web-vitals
@testing-library/react
@testing-library/jest-dom
@testing-library/user-event
```

### `src/App.js`

Arquivo principal da aplicação.

Responsável por:

- envolver rotas com `AuthProvider`;
- carregar rotas da aplicação;
- aplicar estilo global.

Estrutura atual:

```text
AuthProvider
→ RoutesApp
→ GlobalStyle
```

### `src/index.js`

Arquivo de entrada do React.

Responsável por:

- criar root da aplicação;
- renderizar o componente `App`.

### `src/contexts/auth.js`

Arquivo central de autenticação.

Responsável por:

- criar `AuthContext`;
- verificar usuário salvo no LocalStorage;
- executar login;
- salvar token no LocalStorage;
- executar logout;
- remover token do LocalStorage.

### `src/hooks/useAuth.js`

Hook customizado de autenticação.

Responsável por:

- consumir `AuthContext`;
- retornar dados e funções de autenticação.

### `src/routes/index.js`

Arquivo de rotas.

Responsável por:

- configurar `BrowserRouter`;
- configurar `/`;
- configurar `/home`;
- proteger rota privada;
- redirecionar rotas desconhecidas para login.

### `src/pages/Signin/index.js`

Tela de login.

Responsável por:

- controlar estado dos campos;
- validar preenchimento;
- chamar login;
- exibir erro;
- navegar para `/home`.

### `src/pages/Home/index.js`

Tela interna protegida.

Responsável por:

- exibir página inicial;
- executar logout;
- redirecionar para login.

### `src/components/Input/`

Componente reutilizável de input.

Responsável por:

- receber tipo;
- receber placeholder;
- receber valor;
- receber função `onChange`.

### `src/components/Button/`

Componente reutilizável de botão.

Responsável por:

- receber texto;
- receber evento de clique;
- receber tipo do botão.

### `src/styles/global.js`

Estilos globais.

Responsável por:

- resetar margem e padding;
- aplicar `box-sizing`;
- definir altura e largura do body;
- definir fonte padrão;
- definir cor de fundo.

## Fontes de dados utilizadas

O projeto não consulta API externa.

A autenticação atual usa lista local fixa em:

```text
src/contexts/auth.js
```

Fonte atual:

```text
array local de usuários
```

Persistência local:

```text
localStorage
```

Chave de persistência:

```text
user_token
```

## Arquivos gerados

Ao executar:

```bash
npm run build
```

o projeto gera:

```text
build/
```

Principais saídas:

```text
build/index.html
build/static/js/
build/static/css/
build/static/media/
```

A pasta `build/` é a versão final para publicação em servidor web.

## CSVs incrementais

Este projeto não gera CSVs incrementais.

Não há processamento de dados, exportação de relatórios ou rotina ETL.

## Fluxo piloto completo

Para validar o projeto com segurança, siga esta sequência.

### 1. Renomear o repositório

Nome recomendado:

```text
app-autenticacao-login
```

### 2. Ajustar o nome no `package.json`

Alterar:

```json
{
  "name": "react-login"
}
```

Para:

```json
{
  "name": "app-autenticacao-login"
}
```

### 3. Definir gerenciador de pacotes

O projeto possui:

```text
package-lock.json
yarn.lock
```

Escolher apenas um padrão:

```text
npm  → manter package-lock.json e remover yarn.lock
yarn → manter yarn.lock e remover package-lock.json
```

Recomendação prática:

```text
usar npm, porque package-lock.json já está presente e os scripts do package.json seguem padrão npm
```

### 4. Instalar dependências

```bash
npm install
```

### 5. Executar localmente

```bash
npm start
```

Acessar:

```text
http://localhost:3000
```

### 6. Validar login inválido

Testar:

```text
campo vazio
usuário inexistente
senha incorreta
```

Resultado esperado:

```text
mensagem de erro exibida na tela
usuário permanece no login
```

### 7. Validar login válido

Usar a credencial local configurada no código.

Resultado esperado:

```text
usuário é redirecionado para /home
token é salvo no localStorage
página Home é exibida
```

### 8. Validar rota privada

Abrir diretamente:

```text
http://localhost:3000/home
```

Sem login:

```text
deve exibir a tela de login
```

Com login:

```text
deve exibir a Home
```

### 9. Validar logout

Na tela `/home`, clicar em:

```text
Sair
```

Resultado esperado:

```text
token removido do localStorage
usuário volta para /
```

### 10. Gerar build

```bash
npm run build
```

### 11. Validar build local

Opcionalmente, instalar servidor estático:

```bash
npm install -g serve
```

Executar:

```bash
serve -s build
```

Acessar o endereço exibido no terminal.

## Validação sem backend

Este projeto não possui backend.

Validações possíveis:

```text
login local
logout
persistência temporária no localStorage
rota privada
layout
componentes
build
```

Limitações:

```text
não valida credencial real
não consulta banco de dados
não valida sessão no servidor
não possui regra de perfil
não possui expiração de token
não possui refresh token
```

## Análise com IA

Este projeto não executa análise com IA diretamente.

No futuro, pode ser integrado a uma camada de IA apenas em contexto de produto maior, por exemplo:

```text
auditoria de tentativas de login
detecção de comportamento anômalo
sugestão de mensagens de erro mais claras
análise de acessos por perfil
resumo de eventos de autenticação
```

Fluxo sugerido para evolução futura:

```text
frontend React
→ backend de autenticação
→ banco de usuários
→ geração de token seguro
→ logs de acesso
→ análise opcional com IA
```

## Importante

- O projeto é um frontend React baseado em Create React App.
- O projeto usa React Router DOM.
- O projeto usa Styled Components.
- O projeto usa Context API para autenticação.
- O projeto usa LocalStorage para persistir token simulado.
- O nome atual no `package.json` está como `react-login`.
- Nome recomendado do repositório: `app-autenticacao-login`.
- O README original é o README padrão do Create React App.
- O usuário e a senha estão fixos em `src/contexts/auth.js`.
- O token é gerado no frontend com `Math.random()`.
- O token não é validado por servidor.
- O token não possui expiração.
- A autenticação atual não é segura para produção.
- A rota privada protege apenas a navegação visual no frontend.
- Qualquer regra crítica precisa ser validada em backend.
- O projeto possui `package-lock.json` e `yarn.lock` ao mesmo tempo.
- É melhor escolher um único gerenciador de pacotes.
- O campo se chama `email`, mas o placeholder fala em usuário.
- O código mistura `user` e `email` na validação do LocalStorage.
- A restauração de sessão pode falhar por inconsistência entre `user` e `email`.
- A validação de campos usa operador `|` em vez de `||`.
- O componente `Button` recebe children em `Home`, mas renderiza apenas a prop `Text`.
- O arquivo `Signin/index.js` importa `Link`, mas não utiliza.
- O projeto não possui backend.
- O projeto não possui `.env.example`.
- O projeto não possui controle de perfis.
- O projeto não possui tratamento de sessão expirada.
- O projeto não possui testes específicos do fluxo de login.
- O projeto deve ser tratado como base de estudo, protótipo ou esqueleto inicial.

## Ajustes pendentes na arquitetura

- Renomear repositório para `app-autenticacao-login`.
- Ajustar `"name"` no `package.json`.
- Substituir README padrão do Create React App.
- Escolher npm ou Yarn como gerenciador oficial.
- Remover `yarn.lock` se o padrão for npm.
- Remover `package-lock.json` se o padrão for Yarn.
- Remover usuário e senha fixos do frontend.
- Criar backend de autenticação.
- Criar endpoint de login.
- Criar validação real de usuário e senha.
- Criar token seguro no backend.
- Implementar expiração de sessão.
- Implementar logout com invalidação real, se aplicável.
- Substituir LocalStorage por estratégia mais segura conforme arquitetura.
- Corrigir validação `!email | !senha` para `!email || !senha`.
- Padronizar campo como `usuario` ou `email`.
- Corrigir restauração de sessão no `useEffect`.
- Padronizar objeto do usuário salvo no LocalStorage.
- Ajustar `Private` para usar boolean diretamente.
- Remover import não utilizado de `Link`.
- Ajustar componente `Button` para aceitar `children` ou remover children no uso.
- Criar tela de erro ou loading durante verificação da sessão.
- Criar testes do fluxo de login.
- Criar testes do fluxo de logout.
- Criar testes da rota privada.
- Criar layout com identidade visual oficial da Emex, caso o projeto seja usado internamente.
- Criar documentação de integração com backend real.
- Criar `.env.example` caso sejam usadas URLs de API no futuro.
- Criar política de versionamento.

## Sugestão de `.env.example`

O projeto atual não usa variáveis de ambiente.

Caso evolua para autenticação via API, criar:

```env
REACT_APP_API_URL=
REACT_APP_AUTH_LOGIN_PATH=/auth/login
REACT_APP_AUTH_ME_PATH=/auth/me
```

Atenção:

```text
não inserir senha
não inserir token
não inserir segredo
não inserir chave privada
variáveis REACT_APP_* ficam embutidas no build do frontend
```

## Sugestão de `.gitignore`

O `.gitignore` atual já cobre boa parte do necessário.

Recomendação de ajuste:

```gitignore
# Dependências
/node_modules
/.pnp
.pnp.js

# Testes
/coverage

# Build
/build

# Ambiente
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# Logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*

# Sistema operacional
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
```

## Sugestão de estrutura futura

Estrutura recomendada para evolução:

```text
app-autenticacao-login/
├── public/
│   └── index.html
├── src/
│   ├── App.js
│   ├── index.js
│   ├── components/
│   │   ├── Button/
│   │   ├── Input/
│   │   └── Loading/
│   ├── contexts/
│   │   └── auth.js
│   ├── hooks/
│   │   └── useAuth.js
│   ├── pages/
│   │   ├── Home/
│   │   └── Signin/
│   ├── routes/
│   │   └── index.js
│   ├── services/
│   │   └── authApi.js
│   ├── styles/
│   │   └── global.js
│   └── utils/
│       └── storage.js
├── .env.example
├── .gitignore
├── package.json
└── README.md
```

## Sugestão de fluxo futuro com backend

Fluxo recomendado para autenticação real:

```text
usuário informa login e senha
→ frontend envia para API /auth/login
→ backend valida credenciais
→ backend gera token seguro
→ frontend armazena sessão conforme estratégia definida
→ rota privada consulta estado autenticado
→ backend valida permissões em cada recurso protegido
```

## Manutenção recomendada

Antes de evoluir este projeto, validar:

```text
se ele será apenas protótipo ou sistema real
qual backend será usado
qual regra de autenticação será adotada
se haverá perfis de acesso
se o login será por e-mail, usuário ou CPF
se haverá recuperação de senha
se haverá expiração de sessão
se a proteção será apenas frontend ou também backend
se a identidade visual da Emex será aplicada
```

## Checklist antes de publicar no GitHub

- [ ] Repositório renomeado para `app-autenticacao-login`.
- [ ] `package.json` ajustado.
- [ ] README padrão substituído.
- [ ] Gerenciador de pacotes definido.
- [ ] Lockfile duplicado removido.
- [ ] Usuário e senha fixos removidos ou marcados como exemplo.
- [ ] Validação `|` corrigida para `||`.
- [ ] Restauração de sessão revisada.
- [ ] Import não utilizado removido.
- [ ] Componente `Button` revisado.
- [ ] Aplicação testada com `npm start`.
- [ ] Login válido testado.
- [ ] Login inválido testado.
- [ ] Logout testado.
- [ ] Rota `/home` testada sem login.
- [ ] Rota `/home` testada com login.
- [ ] Build validado com `npm run build`.
- [ ] Responsável técnico definido.
- [ ] Objetivo do projeto definido: protótipo, base reutilizável ou sistema real.
