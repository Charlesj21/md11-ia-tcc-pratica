# Evidências de Uso da IA (Questão 11)

## 1. Ferramenta de IA Utilizada
- **Ferramenta:** Assistente de IA integrado (Claude / VS Code / Claude Code) em conjunto com as diretrizes locais.

## 2. Contexto da Tarefa Realizada
Utilizámos o projeto base `GerenciadorDeTarefas` (aplicação de console em C#) para aplicar o fluxo automatizado de revisão de código com base na skill personalizada criada (`revisar-codigo`) e nas regras definidas no `CLAUDE.md`.

## 3. Prompt Exato Utilizado
```text
@revisar-codigo Analise o código atual do ficheiro Program.cs do projeto GerenciadorDeTarefas, verifique se as convenções de nomenclatura da Microsoft (PascalCase e camelCase) estão a ser rigorosamente cumpridas e sugira melhorias na organização da lógica.