# 🚀 Git para Desenvolvedores: Guia Completo do Zero

## Por que aprender Git?

Imagine que você está trabalhando em um projeto. Você faz mudanças, mais mudanças, e de repente quebrou tudo. Com Git, você volta atrás facilmente. É como um **"ctrl+z" em esteroides"** para seu código.

Além disso, em uma empresa com 5, 10 ou 100 desenvolvedores, Git permite que todos trabalhem **no mesmo projeto sem se pisar nos pés**.

---

## 📋 Conceitos Essenciais (Leia Primeiro!)

### 1. O que é um Repositório?
Um repositório é uma **pasta especial** que Git monitora. Dentro dela:
- Estão todos os seus arquivos do projeto
- Git guarda o histórico de TODAS as mudanças
- Você pode voltar a qualquer versão anterior

### 2. Local vs Remoto

**Local = Seu computador**
```
Seu PC
  └─ Pasta do projeto (Git monitora aqui)
     └─ Todos seus arquivos
```

**Remoto = GitHub, GitLab, Bitbucket (na nuvem)**
```
GitHub (servidor na internet)
  └─ Cópia do seu projeto
     └─ Compartilhada com seu time
```

### 3. O Fluxo Principal

```
Você edita arquivos (Local)
        ↓
git status (Ver o que mudou)
        ↓
git add . (Preparar mudanças)
        ↓
git commit -m "mensagem" (Salvar localmente com descrição)
        ↓
git push (Enviar pro GitHub)
        ↓
GitHub (Backup seguro na nuvem)
```

---

## 🔧 Instalação e Configuração Inicial

### Passo 1: Instalar Git
- **Windows**: Baixar em [git-scm.com](https://git-scm.com)
- **Mac**: `brew install git`
- **Linux**: `sudo apt-get install git` (ou equivalente)

### Passo 2: Configurar Identidade (Faça UMA VEZ)

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@email.com"
```

**Exemplo:**
```bash
git config --global user.name "Edigelson Nascimento"
git config --global user.email "ed@xrundev.com"
```

### Passo 3: Criar Repositório Local

**Opção A: Clonar um repositório existente (Primeira vez)**
```bash
git clone https://github.com/usuario/seu-projeto.git
cd seu-projeto
```

**Opção B: Iniciar um repositório novo**
```bash
mkdir meu-projeto
cd meu-projeto
git init
```

---

## 📚 Os 5 Comandos Principais

### 1️⃣ `git status` - Ver o que mudou

**O que faz:**
Mostra todos os arquivos que foram:
- Modificados (editados)
- Deletados
- Criados (novos)

**Comando:**
```bash
git status
```

**Resultado típico:**
```
On branch main

Changes not staged for commit:
  modified:   index.html
  modified:   style.css

Untracked files:
  new_file.js
```

**Tradução:**
- `modified` = Você editou esses arquivos
- `Untracked` = Git não tá rastreando esse arquivo novo ainda

---

### 2️⃣ `git add .` - Preparar mudanças

**O que faz:**
Prepara todos os arquivos modificados e novos para serem salvos.

É como você colocar uma caixa de mudança no chão antes de levar pro caminhão.

**Comando:**
```bash
git add .
```

**Variações:**
```bash
git add .                    # Adiciona TUDO
git add index.html           # Adiciona apenas um arquivo
git add *.js                 # Adiciona todos os .js
git add pasta/               # Adiciona uma pasta inteira
```

**Após `git add .`, nada visível muda.** É um comando "silencioso".

---

### 3️⃣ `git commit -m "mensagem"` - Salvar localmente

**O que faz:**
Salva uma "foto" do seu projeto com uma **mensagem descritiva**.

É como tirar um screenshot do seu código num momento específico.

**Comando:**
```bash
git commit -m "Adicionar função de login"
```

**Entendendo o `-m`:**
- `-m` = **message** (mensagem em inglês)
- `"Adicionar função de login"` = A mensagem que descreve oq você fez

**Exemplos de boas mensagens:**
```bash
git commit -m "Corrigir bug do formulário de cadastro"
git commit -m "Adicionar validação de email"
git commit -m "Remover código obsoleto"
git commit -m "Atualizar estilos do botão de login"
git commit -m "Implementar autenticação JWT"
```

**Exemplos de PÉSSIMAS mensagens:**
```bash
git commit -m "aaa"
git commit -m "mudança"
git commit -m "fix"
```

⚠️ **IMPORTANTE:** O commit salva **apenas no seu computador**. Ninguém vê isso ainda!

---

### 4️⃣ `git push` - Enviar pro GitHub

**O que faz:**
Envia seus commits para o GitHub (ou outro servidor remoto).

É como apertar "Enviar" depois de escrever um email.

**Comando:**
```bash
git push
```

**Ou especificando origem:**
```bash
git push origin main
```

**Tradução:**
- `origin` = Nome do servidor GitHub (padrão)
- `main` = Nome da branch principal (antigamente era `master`)

**Após `git push`:**
- Seu código está no GitHub
- Seu time consegue ver
- É um backup seguro na nuvem
- Seus colegas podem fazer `git pull` pra baixar suas mudanças

---

### 5️⃣ `git pull` - Baixar atualizações

**O que faz:**
Baixa mudanças que outras pessoas fizeram no GitHub.

É essencial em uma empresa onde várias pessoas trabalham no mesmo projeto.

**Comando:**
```bash
git pull
```

**Ou especificando:**
```bash
git pull origin main
```

**Quando usar:**
```
Segunda-feira, chegou no trabalho
            ↓
git pull  (Baixa o que o time fez na sexta)
            ↓
Agora seu código está atualizado com o do time
```

---

## 🔄 O Fluxo Diário Completo

### Cenário 1: Você está trabalhando sozinho

```bash
# 1. Ver o que mudou desde o último commit
git status

# 2. Preparar as mudanças
git add .

# 3. Salvar localmente com uma mensagem
git commit -m "Adicionar página de contato"

# 4. Enviar pro GitHub
git push

# 5. Verificar que funcionou
git status
# Resultado: "nothing to commit, working tree clean"
```

### Cenário 2: Você trabalha em uma empresa

**Chegando no trabalho (segunda-feira):**
```bash
# Baixar tudo que o time fez na semana passada
git pull
```

**Durante o dia:**
```bash
# Você faz mudanças no código...

# Ver o que mudou
git status

# Preparar mudanças
git add .

# Salvar localmente
git commit -m "Implementar validação de CPF"

# Enviar pro GitHub pro time ver
git push

# Colega faz git pull e recebe seu código
```

**Fim do dia:**
```bash
# Fazer commits das mudanças que fez
git add .
git commit -m "Corrigir bug da página de login"
git push

# Pronto! Código seguro no GitHub
# Quando desliga o PC, tudo tá sincronizado
```

---

## 🎯 Passo a Passo: Primeira Vez

### Objetivo: Clonar um repositório e começar a trabalhar

```bash
# 1. Abrir terminal/cmd

# 2. Ir pra uma pasta onde quer colocar o projeto
cd Documentos

# 3. Clonar o repositório do GitHub
git clone https://github.com/usuario/meu-projeto.git

# 4. Entrar na pasta
cd meu-projeto

# 5. Ver status
git status
# Resultado: "On branch main, nothing to commit"

# 6. Fazer uma mudança em um arquivo qualquer
# (Editar com seu editor de código)

# 7. Ver o que mudou
git status
# Resultado: "modified: arquivo.js"

# 8. Preparar mudanças
git add .

# 9. Salvar localmente
git commit -m "Meu primeiro commit!"

# 10. Enviar pro GitHub
git push

# 11. Verificar que funcionou
git status
# Resultado: "nothing to commit"
```

---

## 🚨 Situações Comuns e Como Resolver

### Situação 1: "Deslig meu PC, agora falta baixar?"

**Resposta: NÃO!**

Seus arquivos **não desaparecem**. Eles estão no seu HD/SSD.

```
Ontem:
  git add .
  git commit -m "mudança"
  git push
  DESLIGOU O PC

Hoje:
  git status
  # Resultado: "nothing to commit" (tudo normal)
  
  git pull
  # Baixa APENAS o que mudou desde ontem
  # Não baixa o projeto inteiro de novo
```

### Situação 2: "Esqueci de fazer git push, como recupero?"

Não se preocupe! Seus commits locais estão seguros.

```bash
git log
# Mostra todos seus commits (mesmo os que não fez push)

git push
# Envia tudo o que faltou
```

### Situação 3: "Colega fez mudanças, como pego?"

```bash
git pull
# Baixa e mescla automaticamente as mudanças do colega
```

### Situação 4: "Fiz commit mas a mensagem ficou errada"

```bash
git commit --amend -m "Mensagem correta"
# Corrige o último commit (se ainda não fez push)
```

---

## 📊 Diagrama Visual do Fluxo Completo

```
┌─────────────────────────────────────────────────────────────┐
│                    SEU COMPUTADOR (Local)                    │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  1. Edita arquivo.js (seu editor de código)                 │
│     ↓                                                         │
│  2. git status ← Vê que arquivo.js mudou                     │
│     ↓                                                         │
│  3. git add . ← Prepara arquivo.js                           │
│     ↓                                                         │
│  4. git commit -m "msg" ← Salva com mensagem                │
│     ↓                                                         │
│  5. git push ← ENVIA PRO SERVIDOR                            │
│     ↓                                                         │
└─────────────────────────────────────────────────────────────┘
                          ⬇️ INTERNET ⬇️
┌─────────────────────────────────────────────────────────────┐
│              GITHUB (Servidor na Nuvem - Remoto)             │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  • Cópia do seu projeto                                      │
│  • Histórico de todas mudanças                               │
│  • Visível pro seu time                                      │
│  • Backup seguro                                             │
│                                                               │
└─────────────────────────────────────────────────────────────┘
                          ⬇️ INTERNET ⬇️
┌─────────────────────────────────────────────────────────────┐
│              COMPUTADOR DO COLEGA (Local)                    │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  1. git pull ← Baixa suas mudanças                          │
│     ↓                                                         │
│  2. Agora tem seu arquivo.js atualizado                     │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎓 Tabela de Referência Rápida

| Comando | O que faz | Quando usar |
|---------|-----------|------------|
| `git status` | Vê mudanças | Sempre, no início |
| `git add .` | Prepara tudo | Antes de commit |
| `git commit -m "msg"` | Salva localmente | Depois de adicionar |
| `git push` | Envia pro GitHub | Após commit |
| `git pull` | Baixa atualizações | Chegando no trabalho |
| `git clone URL` | Copia repositório | Primeira vez |
| `git log` | Vê histórico | Quando quer ver commits |
| `git diff` | Vê exatamente o que mudou | Para revisar mudanças |

---

## 💡 Dicas Ouro

### ✅ Boas Práticas

1. **Commit frequente**
   ```bash
   # ✓ BOM: Vários commits pequenos
   git commit -m "Adicionar campo de email"
   git commit -m "Validar campo de email"
   git commit -m "Estilizar campo de email"
   
   # ✗ RUIM: Um commit gigante
   git commit -m "Trabalho de 8 horas"
   ```

2. **Mensagens claras**
   ```bash
   # ✓ BOM
   git commit -m "Corrigir bug do cálculo de frete"
   
   # ✗ RUIM
   git commit -m "arrumei"
   ```

3. **Pull antes de Push**
   ```bash
   # Ordem correta
   git pull        # Primeiro baixa o que tem de novo
   git add .       # Depois prepara seu trabalho
   git commit -m "msg"
   git push        # Por fim envia
   ```

4. **Não commitir lixo**
   ```bash
   # ✗ Não faça commit de:
   # - node_modules/
   # - .env (arquivos com senhas)
   # - arquivos temporários
   
   # Para isso, crie um arquivo .gitignore
   ```

---

## 🎬 Exemplo Prático Completo

### Você é contratado em uma empresa

**Dia 1: Tarde**
```bash
# Clonar o projeto da empresa
git clone https://github.com/empresa/sistema-vendas.git

# Entrar na pasta
cd sistema-vendas

# Ver histórico
git log

# Ler a documentação
cat README.md
```

**Dia 2: Manhã**
```bash
# Chegou, primeiro coisa: baixar atualizações
git pull
# Resultado: já recebe mudanças que fizeram ontem

# Abre editor de código e começa a trabalhar
# Tarefa: Adicionar validação de CPF no cadastro
```

**Dia 2: Meio da manhã**
```bash
# Terminou a validação, quer salvar
git status
# Mostra: arquivo.js modificado

git add .
# Preparou a mudança

git commit -m "Adicionar validação de CPF no cadastro"
# Salvou localmente

git push
# Enviou pro GitHub

# Agora o resto do time vê sua mudança!
```

**Dia 2: Fim do dia**
```bash
# Antes de sair
git status
# Tudo commitado e enviado? Responda: "nothing to commit"

# Pode desligar o PC tranquilo!
```

**Dia 3: Manhã**
```bash
# Liga o PC
git pull
# Baixa o que o time fez ontem

# Continua trabalhando...
```

---

## 🔐 Segurança Básica

### Nunca commitir senhas ou tokens

**✗ ERRADO:**
```bash
# arquivo .env
DB_PASSWORD=minha-senha-super-secreta
API_KEY=sk_live_abc123xyz
```

**✓ CERTO:**
Criar arquivo `.gitignore`:
```
# Criar arquivo chamado .gitignore
node_modules/
.env
.env.local
```

Depois:
```bash
git add .gitignore
git commit -m "Adicionar .gitignore"
```

---

## 📞 Troubleshooting Rápido

### Erro: "fatal: not a git repository"

**Solução:**
```bash
# Você tá na pasta errada
# Procure a pasta com arquivo .git

cd caminho/correto/do/projeto
git status
```

### Erro: "Please tell me who you are"

**Solução:**
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

### Erro: "Your branch is ahead of 'origin/main'"

**Solução:**
```bash
git push
# Envia seus commits que faltavam
```

---

## 🎯 Próximas Etapas

Depois de dominar esses 5 comandos, aprenda:
1. **Branches** (trabalhar em paralelo)
2. **Merge** (juntar trabalhos)
3. **Pull Requests** (sistema de revisão de código)
4. **Rebase** (organizar commits)
5. **Stash** (salvar trabalho temporariamente)

Mas por enquanto, domine:
- `git status`
- `git add .`
- `git commit -m "msg"`
- `git push`
- `git pull`

---

## 📝 Resumo Final

```
Git = Sistema que guarda histórico do seu código
Local = Seu PC
Remoto = GitHub (servidor na internet)

Fluxo diário:
1. Editar código
2. git status (ver mudanças)
3. git add . (preparar)
4. git commit -m "msg" (salvar localmente)
5. git push (enviar pro servidor)

Quando chega:
- git pull (baixar atualizações)

Repeat!
```

**Você consegue! 🚀**

---

**Dúvidas? Volte a este guia quando precisar. Está tudo aqui.**