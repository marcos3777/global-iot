# Global Solution - IoT

## 📹 Vídeos do Projeto

**Vídeo da Solução:** [Assista ao vídeo da apresentação](https://www.youtube.com/watch?v=gfY162zVXz8)

**Pitch do Projeto:** *ADIICONAR DPS DE GRAVADO*

## 👥 Integrantes

| Nome | RM | GitHub |
|------|-----|--------|
| Marcos Vinicius Pereira de Oliveira | 557252 | [@marcos3777](https://github.com/marcos3777) |
| Ruan Lima Silva | 558775 | [@ruaanls](https://github.com/ruaanls) |
| Richardy Borges Santana | 557883 | [@RichardyBS](https://github.com/RichardyBS) |

## 📄 Sobre o Projeto

Este projeto utiliza **N8n** como backend, integrando com a **IA da OpenAI** para leitura e interpretação de currículos. O sistema realiza match de perfil e vaga, sugerindo as melhores oportunidades para os candidatos.

## 🏗️ Arquitetura do Workflow

O workflow implementado no N8n (arquivo `GlobalSolution.json`) possui os seguintes componentes principais:

### 1. 📥 Recepção de Dados
- **Webhook**: Endpoint POST `/leituracv` que recebe currículos enviados via upload de arquivos PDF
- **On Form Submission**: Captura dados de formulários web para complementar informações do candidato

### 2. 🤖 Processamento com IA

- **Extract from File**: Extrai texto de arquivos PDF enviados
- **AI Agent**: Processador inteligente que analisa o conteúdo do currículo
- **OpenAI Chat Model**: Utiliza o modelo GPT-4.1-mini para interpretação avançada
- **Structured Output Parser**: Valida e estrutura a saída em formato JSON padronizado

### 3. 📊 Campos Extraídos do Currículo

A IA extrai e estrutura mais de 40 campos do currículo, incluindo:

**Dados Pessoais:**
- Nome, email, estado, cidade, idade
- Posição atual, empresa atual

**Experiência Profissional:**
- Histórico de empregos anteriores (empresa, cargo, período)
- Nível de senioridade
- Experiência em gestão

**Formação e Competências:**
- Nível de educação
- Cursos e certificações
- Habilidades técnicas com nível de proficiência
- Idiomas com nível de fluência
- Ferramentas e tecnologias

**Perfil Comportamental:**
- Personalidade e estilo de trabalho
- Estilo de liderança e comunicação
- Abordagem para resolução de problemas
- Motivações e objetivos de carreira

**Preferências de Trabalho:**
- Cargos desejados
- Tipo de emprego preferido (CLT, PJ, etc.)
- Salário desejado
- Preferência de ambiente (remoto/presencial/híbrido)
- Disponibilidade para viagem e realocação

**Dados Complementares:**
- LinkedIn, GitHub, portfólio
- Tags e palavras-chave
- Fuso horário

### 4. 🔐 Autenticação e Segurança

- **Check Token Firebase**: Valida tokens de autenticação Firebase
- **Error Handlers**: Tratamento de erros para autenticação, arquivo e IA

### 5. 💾 Armazenamento de Dados

- **PostgreSQL**: Banco de dados relacional para armazenar perfis de candidatos
- **Insert/Update Operations**: Insere novos perfis ou atualiza existentes
- **Select Operations**: Recupera informações de candidatos pelo ID

### 6. ✅ Resposta ao Usuário

- **Success Nodes**: Retorna confirmação de sucesso após processamento
- Resposta estruturada com dados processados

## 🛠️ Tecnologias Utilizadas

- **N8n** - Plataforma de automação de workflows
- **OpenAI API** - GPT-4.1-mini para análise de currículos
- **PostgreSQL** - Banco de dados relacional
- **Firebase Authentication** - Sistema de autenticação
- **Webhooks** - APIs RESTful para integração

## 📋 Fluxo de Funcionamento

1. **Upload**: Candidato envia currículo (PDF ou texto) através do webhook ou formulário
2. **Extração**: Sistema extrai texto do arquivo PDF
3. **Autenticação**: Token Firebase é validado
4. **Análise IA**: OpenAI processa o currículo e extrai informações estruturadas
5. **Validação**: Output Parser garante que o JSON está no formato correto
6. **Armazenamento**: Dados são salvos ou atualizados no PostgreSQL
7. **Resposta**: Sistema retorna confirmação de sucesso

## 📦 Arquivos do Projeto

- **GlobalSolution.json**: Workflow completo do N8n com todos os nós configurados

## 🚀 Como Utilizar

1. Importe o arquivo `GlobalSolution.json` no N8n
2. Configure as credenciais:
   - OpenAI API Key
   - PostgreSQL connection
   - Firebase credentials
3. Ative o workflow
4. Envie requisições POST para o endpoint `/leituracv` com o currículo em PDF

---

**Desenvolvido para Global Solution - FIAP 2025**
