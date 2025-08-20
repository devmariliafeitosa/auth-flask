# Autenticação + Gerenciamento de Usuários (Flask)

## Sobre o Sistema
Esse é um sistema feito em Flask que serve pra gerenciar usuários e controlar quem pode acessar o quê. Ele tem alguns tipos de login, proteção de páginas e registro de atividades pra facilitar o acompanhamento do que acontece na aplicação.

## O que ele faz

### Login de usuários
O sistema tem três jeitos de entrar:

- Sessão: mantém você logado enquanto navega pelas páginas.

- JWT (JSON Web Token): gera um token que serve pra validar você sem precisar de sessão.

- Basic Auth: login simples usando o cabeçalho HTTP.

### Gerenciamento de usuários
Os usuários ficam guardados em um arquivo src/users.json, o que facilita criar, alterar ou remover usuários. Cada usuário tem nome, senha e uma role (tipo de acesso).

### Páginas protegidas e controle de acesso
Nem todo mundo pode acessar todas as páginas. Dependendo da role do usuário, algumas rotas ficam bloqueadas, garantindo que só quem tem permissão consiga ver ou mexer em certas coisas.

### Logs em DEBUG
O sistema registra tudo em nível DEBUG, mostrando:

- Tentativas de login e se deram certo ou errado.

- Quando um JWT é gerado (o payload aparece sem segredo, só pra teste).

- Quando alguém tenta acessar páginas protegidas.

### Pra ativar os logs, é só colocar:

LOG_LEVEL=DEBUG

### Por que é legal

- Segurança: só quem tem permissão consegue acessar certas páginas.

- Prático: dá pra gerenciar usuários de forma simples pelo arquivo JSON.

- Transparente: os logs ajudam a ver tudo que tá rolando, o que é ótimo pra estudar ou depurar o sistema.

## Como Executar
```bash
git clone <repo-url>
cd web1-auth-<seunome>
python -m venv venv
# Linux/Mac
source venv/bin/activate
# Windows
# venv\Scripts\activate

pip install -r requirements.txt
cp .env.example .env
# edite .env e defina seus valores (principalmente JWT_SECRET e SECRET_KEY_SESSION)

flask run
