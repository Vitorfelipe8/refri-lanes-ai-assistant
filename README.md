# Refri-Lanes AI Assistant

Modelo público de workflow de atendimento automatizado no **n8n Cloud**, com **Claude**, consulta e atualização de cadastro na **Data Table** do n8n.

## O que está incluído
- Gatilho de chat do n8n e agente de IA.
- Modelo de bate-papo Anthropic (configuração sem credencial).
- Memória simples durante a sessão.
- Ferramenta de consulta de clientes por telefone.
- Ferramenta de criação/atualização (Upsert) de clientes pelo telefone.

## Como importar
1. No n8n, abra um workflow novo e importe `refri-lanes-ai-assistant-public.json`.
2. Vincule **sua própria** credencial Anthropic (ela não está incluída).
3. Crie/selecione uma Data Table chamada `clientes_refrilanes` com as colunas: `telefone` (texto), `nome` (texto), `cidade` (texto), `bairro` (texto), `equipamento` (texto), `local_instalacao` (texto), `observarcoes` (texto) e `capacidade_btu` (número).
4. Nos dois nós de Data Table, selecione a tabela criada. Revise os campos de mapeamento.
5. Teste consulta, inserção e atualização com dados fictícios antes de ativar o workflow.

> Observação: a coluna `observarcoes` mantém o nome exatamente como constava no esquema exportado do projeto. Se a sua tabela usar `observacoes`, ajuste o esquema e o mapeamento no n8n.

## Segurança e limites
- O JSON público **não contém credenciais de API, IDs de credencial, IDs internos da instância, webhook IDs nem IDs reais da tabela**.
- A versão pública contém uma **mensagem de sistema resumida**, não a configuração integral original da empresa.
- A tabela e a credencial precisam ser escolhidas após importar.
- Antes de uso real, revisar como o Upsert trata campos ausentes para não apagar informações existentes; padronizar telefones (DDD/código do país), testar duplicidades e obter as bases de consentimento/transparência adequadas à LGPD.
- Este repositório documenta um workflow n8n. **Publicar no GitHub não ativa o assistente no site**; integração com o site e ativação do n8n são etapas independentes.
- A memória simples mantém somente contexto de conversa; a Data Table não é uma transcrição integral do atendimento.

## Projeto
Refri-Lanes — automação de atendimento e pré-qualificação para orçamentos de serviços residenciais e comerciais.
