# Assistente-Pessoal-Jarvis
# JAS — Assistente Pessoal

> Um assistente pessoal local para Windows, com interface web própria, conversa por texto e voz, memória de longo prazo e integração opcional com modelos de IA.

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-orange)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Platform](https://img.shields.io/badge/platform-Windows-lightgrey)
![License](https://img.shields.io/badge/license-a%20definir-lightgrey)

## 📌 Sobre o projeto

A **JAS** é um projeto pessoal de assistente virtual desenvolvido para funcionar localmente no Windows.

O projeto começou com a ideia de criar um assistente inspirado em interfaces futuristas de ficção científica, mas a implementação é própria e independente.

A aplicação combina um servidor local em Python com uma interface web executada no navegador.

### Principais recursos

- 💬 Conversa por texto
- 🎤 Entrada por microfone
- 🔊 Respostas por voz
- 🧠 Memória de longo prazo
- 📷 Análise de imagens com IA
- 🧮 Calculadora local
- 📝 Elaboração de textos
- 💡 Quadro de ideias
- 📱 Preparação de mensagens para WhatsApp
- 🤖 Integração opcional com Google Gemini
- 🤖 Provedor alternativo NVIDIA NIM para conversa/texto
- 🔐 Proteção dos endpoints locais por token de sessão
- ⚙️ Configurações persistentes
- 🧪 Testes automatizados

---

## 🖥️ Interface

A interface possui um painel central de comando, área de conversa, visão por câmera, ações rápidas e quadro de ideias.

A prévia da câmera permanece no computador até que o usuário escolha enviar uma imagem para a IA.

---

## 🏗️ Arquitetura

A estrutura atual do projeto é simples e foi pensada para facilitar futuras evoluções:

```text
Jarvis_Pessoal/
│
├── app.py
├── core.py
├── Iniciar.bat
│
├── web/
│   ├── index.html
│   ├── app.js
│   └── style.css
│
├── test_core.py
├── test_server.py
├── test_frontend.cjs
│
├── LEIA_PRIMEIRO.md
├── PASSO_A_PASSO_GEMINI.md
└── O_QUE_MUDOU.md
```

### Responsabilidade dos principais arquivos

| Arquivo | Função |
|---|---|
| `app.py` | Servidor local, API e gerenciamento do estado da aplicação |
| `core.py` | Funções de IA, voz, transcrição, cálculos e validações |
| `web/index.html` | Estrutura da interface |
| `web/app.js` | Comportamento da interface e comunicação com a API |
| `web/style.css` | Estilo visual da interface |
| `Iniciar.bat` | Inicialização simplificada no Windows |
| `test_core.py` | Testes das funções principais |
| `test_server.py` | Testes de integração do servidor |
| `test_frontend.cjs` | Testes dos fluxos do frontend |

---

# 🚀 Instalação

## Requisitos

- Windows
- Python 3
- Navegador baseado em Chromium, como Microsoft Edge ou Google Chrome
- Internet somente para os recursos que utilizam serviços online

O projeto foi desenvolvido para funcionar usando a biblioteca padrão do Python, sem exigir uma instalação de pacotes via `pip` para a execução básica.

## 1. Baixe o projeto

Clone o repositório:

```bash
git clone SEU_REPOSITORIO_AQUI
cd Jarvis_Pessoal
```

Ou baixe o projeto como ZIP pelo GitHub e extraia todos os arquivos.

## 2. Verifique o Python

No Prompt de Comando:

```bash
python --version
```

ou:

```bash
py --version
```

O projeto precisa de Python 3.

## 3. Inicie a JAS

No Windows, execute:

```text
Iniciar.bat
```

O script tenta utilizar `py -3` e, caso não esteja disponível, tenta `python`.

Mantenha o terminal aberto enquanto estiver usando a aplicação.

A JAS abrirá uma interface local no navegador. Caso ela não seja aberta automaticamente, use o endereço exibido no terminal.

> **Importante:** o endereço local pode conter um token de sessão. Não publique esse endereço completo em prints, vídeos ou mensagens.

---

# 🤖 Integração com IA

A JAS possui um modo local e integrações online opcionais.

## Modo local

Algumas funções não precisam de internet, como:

- cálculos;
- comandos internos;
- gerenciamento da memória local;
- quadro de ideias;
- preparação de links para WhatsApp.

Por exemplo:

```text
quanto é 25 vezes 4
```

A aplicação pode responder localmente:

```text
Resultado: 100
```

## Google Gemini

A aplicação possui integração com a API do Google Gemini para recursos online, incluindo conversa, transcrição, geração de voz e análise de imagens, conforme a configuração do projeto e os recursos disponíveis para a chave utilizada.

A chave deve ser configurada pela interface da aplicação ou por variável de ambiente.

### Variável de ambiente

No Windows, é possível configurar:

```text
GEMINI_API_KEY
```

> Nunca coloque uma chave de API diretamente no código-fonte.

---

# 🔊 Voz

A JAS possui suporte para síntese de voz.

As vozes disponíveis dependem do mecanismo configurado. No modo Gemini, o projeto possui vozes configuradas no código, incluindo:

```text
Charon
Orus
Algenib
Algieba
```

A voz do projeto é sintética e não tem como objetivo reproduzir a voz de um ator, dublador ou personagem específico.

---

# 🧠 Memória

A memória de longo prazo é armazenada localmente.

Comandos disponíveis:

```text
/lembrar <informação>
```

Exemplo:

```text
/lembrar curso de Engenharia de Software
```

Listar memória:

```text
/memoria
```

Remover um item:

```text
/esquecer 1
```

Apagar toda a memória:

```text
/esquecer tudo
```

Os dados são armazenados em:

```text
dados/memoria.json
```

A aplicação limita a memória a **200 itens**, com até **400 caracteres por fato**.

---

# 📱 WhatsApp

A JAS pode preparar uma mensagem e gerar um link para abertura no WhatsApp.

O envio não é feito automaticamente pelo projeto: o usuário revisa o destinatário e a mensagem antes de enviar.

---

# 🔐 Segurança

Alguns cuidados são importantes antes de publicar o projeto no GitHub.

## Nunca publique

- chaves de API;
- senhas;
- tokens de sessão;
- arquivos pessoais;
- documentos privados;
- dados pessoais sensíveis.

O arquivo:

```text
dados/config.json
```

pode conter configurações e, dependendo da opção escolhida pelo usuário, uma chave de API.

**Não faça commit desse arquivo.**

Adicione `dados/` ao `.gitignore`.

---

# 🧪 Testes

O projeto possui testes automatizados para funções principais, API e frontend.

### Testes Python

```bash
py -3 -m unittest
```

ou:

```bash
python -m unittest
```

### Testes do frontend

O projeto também possui:

```text
test_frontend.cjs
```

que pode ser executado com Node.js:

```bash
node test_frontend.cjs
```

---

# 🛠️ Tecnologias

- **Python 3**
- **HTML5**
- **CSS3**
- **JavaScript**
- **HTTP Server local**
- **Google Gemini API**
- **NVIDIA NIM API** (opcional)
- **Web APIs do navegador**
- **JSON para armazenamento local**

---

# 🗺️ Roadmap

A ideia é evoluir a JAS gradualmente.

### Concluído / em desenvolvimento

- [x] Interface própria
- [x] Chat local
- [x] Integração com IA
- [x] Voz
- [x] Microfone
- [x] Memória local
- [x] Quadro de ideias
- [x] Calculadora
- [x] Análise de imagem
- [x] Preparação de mensagens
- [x] Testes automatizados
- [x] Provedor alternativo para conversa

### Próximos passos

- [ ] Wake word — dizer "JAS" para ativá-la
- [ ] Aplicativo desktop nativo
- [ ] Inicialização opcional com o Windows
- [ ] Mais comandos do sistema operacional
- [ ] Sistema de plugins/ferramentas
- [ ] Melhor gerenciamento de contexto
- [ ] Personalização avançada da personalidade
- [ ] Interface mais responsiva e animada
- [ ] Empacotamento em executável

---

# 📂 Documentação adicional

O projeto possui alguns documentos auxiliares:

- `LEIA_PRIMEIRO.md` — instalação e primeiros passos
- `PASSO_A_PASSO_GEMINI.md` — configuração da integração Gemini
- `O_QUE_MUDOU.md` — histórico das principais alterações recentes

---

# ⚠️ Estado do projeto

Este projeto está em **desenvolvimento ativo**.

Alguns recursos dependem de APIs externas e podem mudar conforme os serviços utilizados alterem modelos, limites ou endpoints.

Antes de usar uma integração online, consulte a documentação oficial do respectivo provedor.

---

# 👨‍💻 Autor

Projeto pessoal desenvolvido por **Jhon** como estudo e desenvolvimento de um assistente virtual.

O objetivo é aprender, na prática, conceitos de:

- desenvolvimento de software;
- Python;
- JavaScript;
- APIs;
- integração com IA;
- desenvolvimento web;
- automação;
- arquitetura de aplicações;
- testes;
- segurança.

---

# 📄 Licença

A licença deste projeto ainda não foi definida.

Se o projeto for publicado publicamente, recomenda-se escolher uma licença apropriada antes de permitir reutilização, modificação ou distribuição do código.
