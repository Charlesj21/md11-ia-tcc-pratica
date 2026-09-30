# Avaliação Individual — Módulo 11 — Tecnologias Emergentes e IA

**Data de entrega:** 30/09/2026
**Formato:** individual, de consulta aberta — use slides, anotações e a própria IA à vontade para pesquisar e testar suas respostas.

## Como participar

1. Faça um **fork** deste repositório.
2. Clone o seu fork localmente.
3. Responda as questões teóricas **direto neste README**, abaixo de cada uma.
4. Complete a parte prática (veja abaixo) editando `CLAUDE.md`, `.claude/skills/minha-skill/SKILL.md` e `EVIDENCIAS.md`.
5. Abra um **Pull Request** do seu fork de volta para este repositório.

> O PR não será mergeado — ele existe só para eu avaliar o seu diff. Pode deixar aberto depois de enviar.

O objetivo não é decorar definições, e sim demonstrar que você entende os conceitos e sabe aplicá-los para ganhar eficiência ao usar IA no seu projeto de TCC. Responda com suas próprias palavras — copiar e colar resposta pronta de IA sem entender não demonstra o aprendizado esperado.

---

## Questões dissertativas

### Questão 1 — O que é um "agent"?
O que é um "agent" (agente de IA)? Explique com suas próprias palavras e dê um exemplo de situação em que faz mais sentido usar um agente do que um chat comum.


Um agente de IA (agent) é um sistema autônomo baseado em modelos de linguagem que vai além de responder a perguntas em um chat estático. Ele tem a capacidade de planejar, tomar decisões, utilizar ferramentas externas (como ler/escrever arquivos, executar comandos no terminal e navegar pela web) e executar fluxos de trabalho em loop de forma independente até alcançar um objetivo final.
*Exemplo:* Em vez de usar um chat comum onde você copia um erro de compilação em C#, cola na IA, recebe a dica, copia o código e altera manualmente no Visual Studio, um agente de IA (como o Claude Code ou Cursor) pode ler os arquivos do projeto localmente, identificar o bug no código, aplicar a correção diretamente, compilar a solução para testar e validar o resultado de forma totalmente autônoma.


### Questão 2 — O que são guidelines?
O que são "guidelines" (diretrizes) ao usar uma IA generativa? Qual é o papel delas na qualidade das respostas geradas pelo modelo?


Guidelines (diretrizes) são conjuntos de regras, padrões, convenções de código e restrições predefinidas fornecidas à IA (geralmente através de um arquivo de configuração como o `CLAUDE.md`). O papel delas é guiar o comportamento do modelo para garantir que as respostas e códigos gerados sigam exatamente o padrão técnico desejado pelo desenvolvedor ou pela equipe, evitando que a IA utilize bibliotecas obsoletas, crie estruturas fora do padrão do projeto ou viole regras arquiteturais.


### Questão 4 — Escolha de modelo e nível de esforço
Qual modelo de IA utilizar para cada tipo de tarefa? Dê um exemplo de tarefa simples e outra mais complexa, explicando como você escolheria o modelo em cada caso. O que é o "nível de esforço" (effort level) e quando faz sentido aumentá-lo ou diminuí-lo?


A escolha do modelo depende da complexidade da tarefa:
- **Tarefas simples** (ex: formatar um JSON, renomear variáveis ou criar um pequeno script utilitário): Utilizo modelos mais rápidos e leves (como o Claude 3.5 Haiku), pois oferecem respostas imediatas e gastam menos recursos.
- **Tarefas complexas** (ex: projetar a arquitetura de controllers ASP.NET Core, estruturar banco de dados relacional ou refatorar lógica de negócios crítica): Utilizo modelos avançados de raciocínio (como o Claude 3.5 Sonnet ou GPT-4o), capazes de lidar com lógica refinada e contexto profundo.
O **nível de esforço (effort level)** controla o tempo de computação e planejamento interno que o modelo gasta antes de responder. Faz sentido aumentá-lo em tarefas de depuração profunda ou algoritmos complexos onde o raciocínio passo a passo é crucial, e diminuí-lo para tarefas textuais rápidas e diretas.


### Questão 5 — Como estruturar um bom prompt
Descreva os elementos que tornam um prompt mais eficaz (ex.: contexto, objetivo, formato esperado, exemplos, restrições).

Um prompt eficaz é estruturado combinando elementos claros:
1. **Contexto:** Explicação do cenário atual (ex: tecnologias usadas, versão do .NET, estado atual do código).
2. **Objetivo:** O que exatamente a IA deve fazer ou resolver.
3. **Formato esperado:** Como a resposta deve ser entregue (ex: trecho de código C# puro, tabela Markdown, JSON).
4. **Exemplos (opcional):** Demonstrações de entradas e saídas esperadas (few-shot).
5. **Restrições:** O que NÃO deve ser feito (ex: "não utilize bibliotecas externas", "mantenha a compatibilidade com C# 10").


### Questão 6 — Iteração de prompt
O que significa "iterar" um prompt? Por que a primeira resposta de uma IA geralmente não é a versão final, e como você usaria a resposta recebida para melhorar o próximo prompt?

Iterar um prompt significa refiná-lo sucessivamente em ciclos de conversa com base nos resultados obtidos. A primeira resposta muitas vezes não é a definitiva porque a IA pode generalizar demais, esquecer algum detalhe específico ou interpretar mal o contexto inicial. Usamos a resposta parcial recebida (ou um erro gerado ao testá-la) para alimentar o próximo prompt com correções direcionadas (ex: "A lógica funcionou bem, mas adapte para tratar exceções nulas e utilize LINQ").


### Questão 7 — Zero-shot vs. few-shot
Qual é a diferença entre um prompt "zero-shot" e um prompt "few-shot"? Dê um exemplo de situação em que vale a pena incluir exemplos dentro do próprio prompt.


- **Zero-shot:** É quando você dá a instrução à IA sem fornecer nenhum exemplo prévio, confiando apenas no conhecimento geral pré-treinado do modelo.
- **Few-shot:** É quando você inclui um ou mais exemplos de entrada e saída esperada diretamente no prompt antes de fazer a solicitação real.
*Exemplo prático:* Vale a pena usar few-shot ao mapear dados de um DTO para uma entidade de banco de dados em um formato proprietário ou específico do projeto, garantindo que a IA replique exatamente a estrutura de código exigida pela equipe.


### Questão 8 — Memória e contexto entre sessões
O que significa uma IA "ter memória" entre sessões diferentes de conversa? Por que, em um projeto longo como o TCC, é importante decidir o que precisa ser "lembrado" e como fornecer esse contexto para a IA a cada nova conversa?

Significa a capacidade do sistema de reter o histórico, decisões arquiteturais e preferências de conversas passadas. Em projetos longos como o TCC, isso é fundamental porque o escopo é grande e a IA não conhece naturalmente as regras de negócio ou as escolhas tecnológicas já feitas. Definir o que deve ser lembrado (através de documentações persistentes como o `CLAUDE.md`) garante consistência no desenvolvimento, evitando que você precise reescrever o contexto completo do sistema a cada nova sessão.


### Questão 9 — Avaliar a resposta da IA
Antes de aplicar a sugestão de uma IA no seu projeto, como você verifica se ela está correta? Descreva pelo menos 2 formas práticas de checar a confiabilidade de uma resposta gerada por IA.

1. **Compilação e Execução de Testes locais:** Inserir o código no ambiente de desenvolvimento (ex: rodar `dotnet build` ou depurar no Visual Studio) para verificar se há erros de sintaxe, tipos incompatíveis ou falhas de compilação.
2. **Revisão Estática e Análise de Lógica:** Ler criticamente o código linha por linha para garantir que ele atende aos requisitos de segurança, boas práticas de programação e regras de negócio específicas da aplicação.


### Questão 10 — Dividir tarefas complexas em etapas
Por que, em tarefas mais complexas, pode ser melhor dividir o trabalho em um fluxo de etapas (ex.: primeiro classificar/organizar, depois processar, depois revisar) em vez de pedir tudo em um único prompt? Dê um exemplo aplicado a uma tarefa do seu TCC.


Dividir tarefas complexas reduz a carga cognitiva da IA, minimiza alucinações e aumenta drasticamente a precisão dos resultados, pois foca o modelo em uma sub-tarefa por vez.
*Exemplo aplicado ao TCC:* Em vez de pedir para a IA criar todo um módulo de gerenciamento de dados de ponta a ponta em um único prompt, dividimos em etapas:
- **Etapa 1:** Modelar as classes de domínio e entidades do banco de dados (relação SQL e chaves estrangeiras).
- **Etapa 2:** Implementar os repositórios e a camada de serviços de negócio em C#.
- **Etapa 3:** Criar os Controllers da API e configurar o Swagger.
- **Etapa 4:** Revisar o código gerado aplicando validações e tratamento de erros.

---

> **Questão 3** (como escrever um bom CLAUDE.md) e a **Questão 11** (prática, evidência de uso real da IA) são respondidas nos próprios arquivos `CLAUDE.md` e `EVIDENCIAS.md` — veja a parte prática no repositório.