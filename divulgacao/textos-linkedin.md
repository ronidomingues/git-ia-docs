# Textos para o LinkedIn

## 1. Post no feed

Imagem: `linkedin.png` (1080×1080).

---

Um prompt de 231 caracteres virou um de 37.883. E cada linha nova tem uma falha por trás. 🧵

No meu estágio em Análise e Desenvolvimento de Sistemas na Marinha do Brasil, enfrentei dois problemas que viraram uma capacitação para a equipe e, agora, um material aberto no GitHub.

🔀 Problema 1: sistemas que já tinham anos de histórico Git precisavam entrar num GitLab Self-Managed em que a main já vem criada, com README padrão e protegida. São dois históricos sem nenhum ancestral comum, e o Git responde: "refusing to merge unrelated histories".
A solução coube em 8 passos, com --allow-unrelated-histories, a decisão consciente entre ours e theirs (a parte que mais gera erro) e um Merge Request no fim. Sem perder um commit.

🤖 Problema 2: versionado não é documentado. Usei o Claude Code para fazer engenharia reversa e documentar sistemas legados. Analisei os 717 prompts reais do meu histórico e encontrei 5 versões do prompt de documentação. Cada falha virou uma regra:
• a documentação saía superficial → análise em fases, com uma fase só para validar o entendimento;
• o agente preenchia lacunas por conta própria → "nunca invente", com rótulos como DESCONHECIDO e REQUER VALIDAÇÃO;
• havia risco de alterar código durante a análise → descoberta somente leitura;
• o prompt em inglês gerou respostas em inglês → saída obrigatória em PT-BR;
• o agente seguia em frente diante de risco → protocolo Safe Stop-and-Report: parar, reportar e esperar a decisão humana.

📉 O retrabalho estimado caiu de ~53% para ~25%. A amostra é pequena, e eu deixo isso claro no material.

A lição que fica: IA é ferramenta de engenharia, não autoridade. Quem define o objetivo, valida no sistema real e decide continua sendo gente.

📦 O repositório tem 122 páginas: slides, apostila para iniciantes (com padrões de commit e assinatura de commits com GPG e SSH), exercícios, roteiro de falas e o prompt final completo.
👉 github.com/ronidomingues/git-ia-docs

Se você também usa agentes de IA no dia a dia, qual regra já teve que acrescentar depois de uma falha?

#Git #GitLab #ClaudeCode #IA #EngenhariaDePrompt #EngenhariaDeSoftware #DevOps #Documentação #Estágio #AnáliseEDesenvolvimentoDeSistemas

---

## 2. Seção "Projetos" do perfil

**Nome do projeto:** git · ia · docs: Git, GitLab e IA aplicada à Engenharia de Software

**Associado a:** Estágio em Análise e Desenvolvimento de Sistemas, Marinha do Brasil

**URL:** https://github.com/ronidomingues/git-ia-docs

**Descrição:**

Capacitação completa (slides, apostila e roteiro de falas, 122 páginas em LaTeX) criada a partir de dois problemas reais do estágio.

• Git e GitLab: integração de sistemas já versionados a um GitLab Self-Managed com a main protegida, unindo históricos sem ancestral comum (--allow-unrelated-histories, ours × theirs e Merge Request, também pelo GitLab CLI). Inclui um exercício que reproduz o caso sem servidor.

• IA aplicada: engenharia reversa e documentação de sistemas legados com o Claude Code. Analisei 717 prompts reais e mapeei 5 versões do prompt de documentação. O prompt final tem descoberta somente leitura, a regra "nunca inventar" com rótulos de evidência, a separação AS-IS/TO-BE/GAP e um protocolo Safe Stop-and-Report. Retrabalho estimado de ~53% para ~25%.

• Material para iniciantes: exercícios com respostas, cola de comandos e glossário. Todos os comandos foram executados de verdade.

**Competências:** Git · GitLab · GitLab CLI · Claude Code · Engenharia de prompt · Documentação técnica · LaTeX · Didática
