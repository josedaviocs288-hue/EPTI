# Site do Evento EPTI

Projeto completo com:

- Frontend em HTML, CSS e JavaScript puro.
- Tela inicial de login.
- Tela de cadastro com nome, turma, email institucional e senha.
- Cache de login usando `localStorage`.
- Tela principal com cronograma em tabela, área de vendas e minicursos.
- Backend Node.js + Express.
- Banco SQLite.
- Cadastro/login com senha criptografada.
- Escolha de minicurso salva no banco.
- Cada usuário só pode escolher um minicurso.

## Estrutura

```txt
epti_site_evento/
  frontend/
    index.html
    styles.css
    script.js
    assets/img/
      fundo-epti.png
      logo-exemplo.png
  backend/
    src/
      server.js
      db.js
      auth.js
    data/
    package.json
    .env.example
```

## Como rodar o backend

Entre na pasta do backend:

```bash
cd backend
npm install
cp .env.example .env
npm run dev
```

Teste:

```bash
curl http://localhost:3000/api/health
```

Deve retornar:

```json
{"status":"UP","app":"EPTI Evento Backend"}
```

## Como rodar o frontend local

Você pode abrir o arquivo `frontend/index.html` direto no navegador, ou usar uma extensão como Live Server.

No arquivo `frontend/script.js`, a URL está assim:

```js
const API_URL = "http://localhost:3000/api";
```

Quando o backend estiver hospedado, troque para a URL real:

```js
const API_URL = "https://api.seudominio.com/api";
```

## Onde trocar as logos e imagens

### Logo principal

No `frontend/index.html`, procure por:

```html
<img src="./assets/img/logo-exemplo.png" alt="Logo EPTI" />
```

Troque pelo nome do seu PNG.

Exemplo:

```html
<img src="./assets/img/minha-logo.png" alt="Logo EPTI" />
```

Depois coloque o arquivo dentro de:

```txt
frontend/assets/img/
```

### Fundo

No `frontend/styles.css`, procure:

```css
url("./assets/img/fundo-epti.png")
```

Troque pelo fundo que você quiser.

### Imagens dos itens vendidos

No `frontend/index.html`, procure pelos blocos:

```html
<!-- <img src="./assets/img/item-1.png" alt="Item 1" /> -->
```

Remova o comentário e coloque a imagem real.

Exemplo:

```html
<img src="./assets/img/salgado.png" alt="Salgado" />
```

## Publicar frontend no GitHub Pages

1. Suba a pasta `frontend` para um repositório no GitHub.
2. Vá em `Settings > Pages`.
3. Em `Build and deployment`, selecione a branch principal.
4. Antes de publicar, troque no `script.js` a `API_URL` para a URL do backend hospedado.

## Publicar backend

Você pode hospedar o backend em AWS, Render, Railway, VPS ou outro serviço Node.js.

Variáveis de ambiente necessárias:

```env
PORT=3000
JWT_SECRET=coloque_uma_chave_grande_e_segura
FRONTEND_URL=https://seuusuario.github.io/seu-repositorio
DB_PATH=./data/epti.db
```

Em produção, se for usar domínio, o ideal é:

- Frontend: `https://seudominio.com`
- Backend: `https://api.seudominio.com`

Aí no frontend coloque:

```js
const API_URL = "https://api.seudominio.com/api";
```

## Observação sobre banco

Este projeto usa SQLite para facilitar. Para evento escolar e poucos acessos, funciona bem. Se depois você quiser usar PostgreSQL na AWS, dá para trocar o arquivo `backend/src/db.js` e manter as mesmas rotas.
# EPTI
