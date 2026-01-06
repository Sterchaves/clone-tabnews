# Setup macOS (clone-tabnews)

Este guia configura o ambiente no macOS e define o fluxo diário para rodar o projeto.

Requisitos de versão do projeto:
1. Node.js LTS Hydrogen (18.14.2 ou mais atual dentro da linha 18)
2. Next.js 13.1.6
3. React 18.2.0
4. React DOM 18.2.0

## 1. Abrir o projeto no dia a dia

1. Abrir o Terminal
2. Ir para a pasta do projeto
   cd ~/Projects/clone-tabnews

3. Carregar a versão do Node definida no projeto
   nvm use

4. Instalar dependências (apenas quando necessário)
   npm install

5. Subir o projeto
   npm run dev

6. Abrir o VS Code na pasta do projeto (manual, recomendado)
   code .

7. Acessar no navegador
   http://localhost:3000

### Como parar o localhost
No Terminal onde o servidor está rodando, pressione:
Ctrl + C

Se o terminal travar, pare o processo e volte ao prompt com:
Ctrl + C

## 2. Como configurar o ambiente no macOS

### 2.1 Criar pasta padrão de projetos
1. Abra o Terminal e rode:
   mkdir -p ~/Projects

### 2.2 Instalar Xcode Command Line Tools
No Terminal:
xcode-select --install

Se aparecer uma janela, confirme a instalação.

### 2.3 Instalar Homebrew (Apple Silicon)
No Terminal:
 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Depois, habilite o brew no shell (Apple Silicon normalmente usa /opt/homebrew):
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

Validar:
brew --version

### 2.4 Instalar Git
No Terminal:
brew install git

Validar:
git --version

### 2.5 Instalar VS Code
Instale o VS Code normalmente.

Habilitar o comando `code` no Terminal:
1. Abra o VS Code
2. Command Palette: Cmd + Shift + P
3. Digite: Shell Command: Install 'code' command in PATH
4. Selecione e confirme

Feche e abra o Terminal novamente, e teste:
code --version

### 2.6 Instalar NVM
Recomendado via Homebrew:
brew install nvm

Criar pasta do nvm:
mkdir -p ~/.nvm

Adicionar ao ~/.zshrc:
nano ~/.zshrc

Cole no final do arquivo:
export NVM_DIR="$HOME/.nvm"
source "$(brew --prefix nvm)/nvm.sh"

Salvar e sair do nano:
Ctrl + O
Enter
Ctrl + X

Carregar as alterações:
source ~/.zshrc

Validar:
nvm --version

### 2.7 Clonar o projeto
Entre na pasta Projects:
cd ~/Projects

Clone o repositório:
git clone <URL_DO_REPOSITORIO>

Entre no projeto:
cd clone-tabnews

Abrir no VS Code:
code .

## 3. Setup de versões do projeto (Node, Next, React)

### 3.1 Node com .nvmrc (importante)
O arquivo `.nvmrc` deve conter apenas a versão do Node, em uma única linha.

Exemplo recomendado para este projeto:
18.14.2

Se o seu `.nvmrc` estiver com texto extra (Next, React etc), o `nvm use` vai falhar.
Versões de Next e React ficam no `package.json`, não no `.nvmrc`.

### 3.2 Instalar a versão do Node do projeto
Dentro da pasta do projeto:
cd ~/Projects/clone-tabnews

Instalar o Node correto:
nvm install 18.14.2

Usar a versão:
nvm use

Validar:
node -v
npm -v

### 3.3 Fixar Next e React nas versões exigidas
Ainda dentro do projeto, rode:
npm install --save-exact next@13.1.6 react@18.2.0 react-dom@18.2.0

Isso atualiza:
1. package.json
2. package-lock.json

Depois valide:
npx next --version

Opcional para confirmar React:
node -e "console.log(require('react').version)"

### 3.4 Instalar dependências e rodar o projeto
npm install
npm run dev

Acesse:
http://localhost:3000

## 4. Extensões recomendadas do VS Code

Instale estas extensões:
1. ESLint
2. Prettier
3. EditorConfig for VS Code
4. GitLens (opcional)

## 5. Atalhos no Terminal (aliases)
Você pode manter apenas estes aliases no ~/.zshrc:

# Atalhos de projetos
alias projects="cd ~/Projects"
alias tabnews="cd ~/Projects/clone-tabnews"

# Atalho para subir o projeto
alias tabnews-dev="cd ~/Projects/clone-tabnews && nvm use && npm run dev"

Após editar o ~/.zshrc, rode:
source ~/.zshrc

## 6. Checklist rápido de verificação
1. brew --version
2. git --version
3. code --version
4. nvm --version
5. cd ~/Projects/clone-tabnews
6. nvm use
7. node -v
8. npm install
9. npm run dev
10. abrir http://localhost:3000
