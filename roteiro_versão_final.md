# Capacitação — Git, GitLab e IA aplicada à Engenharia de Software

## 1. Objetivo da capacitação

Esta capacitação tem como objetivo apresentar os conceitos fundamentais de **Git**, **GitLab**, **branches**, **Merge Requests** e **GitLab CLI**, utilizando problemas reais encontrados no ambiente de trabalho como exemplos práticos.

Além da parte de versionamento, será apresentada uma abordagem para utilização de **agentes de IA**, especialmente o Claude Code, como ferramenta auxiliar na compreensão, análise, refatoração e documentação de sistemas existentes.

### Objetivos específicos

Ao final da capacitação, espera-se que os participantes sejam capazes de:

- compreender o que é Git e para que ele serve;
- compreender o que é GitLab e como ele se relaciona com o Git;
- diferenciar Git, GitLab, GitHub e GitLab CLI;
- compreender branches e seu propósito;
- compreender o conceito de Merge Request;
- executar o fluxo básico de trabalho colaborativo com Git;
- compreender e resolver conflitos básicos de merge;
- compreender o problema de integração de históricos Git independentes;
- integrar um sistema local previamente versionado a um repositório GitLab institucional;
- compreender como utilizar um agente de IA como ferramenta auxiliar de engenharia de software;
- estruturar um processo de documentação profunda de sistemas legados.

---

# 2. O que é o GitLab e para que serve?

O **GitLab** é uma plataforma de desenvolvimento e gerenciamento de software baseada no Git.

Ele oferece, em uma mesma plataforma, recursos para:

- hospedagem de repositórios Git;
- controle de versões;
- gerenciamento de branches;
- Merge Requests;
- revisão de código;
- controle de permissões;
- Issues;
- CI/CD;
- pipelines;
- releases;
- segurança;
- auditoria;
- colaboração entre equipes.

É importante entender que **Git e GitLab não são a mesma coisa**.

O Git é o sistema de controle de versão.

O GitLab é uma plataforma que utiliza Git e acrescenta recursos para colaboração, gerenciamento e automação do desenvolvimento.

## 2.1. Git × GitLab × GitHub

| Tecnologia | O que é? | Principal finalidade |
|---|---|---|
| Git | Sistema distribuído de controle de versão | Controlar o histórico do código |
| GitLab | Plataforma baseada em Git | Hospedar, gerenciar e colaborar sobre projetos |
| GitHub | Plataforma baseada em Git | Hospedar, gerenciar e colaborar sobre projetos |
| GitLab CLI (`glab`) | Ferramenta de linha de comando | Interagir com o GitLab pelo terminal |

### Git

Pode funcionar completamente localmente.

Por exemplo:

```bash
git init
git add .
git commit -m "Primeiro commit"
```

Nenhum servidor GitLab ou GitHub é necessário para esses comandos.

### GitLab e GitHub

São plataformas que acrescentam uma camada de colaboração ao Git.

Elas permitem, por exemplo:

- hospedar o repositório;
- controlar usuários;
- revisar código;
- criar Merge Requests ou Pull Requests;
- executar pipelines;
- gerenciar Issues;
- controlar permissões.

---

# 3. GitLab Self-Managed

Um ponto especialmente importante para organizações é que o GitLab possui uma modalidade que pode ser instalada e administrada na própria infraestrutura da organização.

Isso é conhecido como **GitLab Self-Managed**.

Em um ambiente desse tipo, a instituição pode manter sua própria instância do GitLab em seus servidores ou infraestrutura autorizada.

Isso pode permitir maior controle sobre:

- armazenamento dos dados;
- código-fonte;
- histórico dos projetos;
- usuários;
- permissões;
- autenticação;
- auditoria;
- políticas de segurança;
- integração com outros sistemas.

### Atenção

Não devemos interpretar isso como:

> "Se está dentro da empresa, então está automaticamente seguro."

A segurança depende também de:

- configuração;
- controle de acesso;
- atualização do software;
- autenticação;
- políticas de senha;
- backups;
- firewall;
- segmentação de rede;
- monitoramento;
- auditoria;
- gestão de vulnerabilidades.

O ponto principal é:

> **A organização pode manter o ambiente GitLab sob sua própria administração e dentro de sua infraestrutura ou ambiente controlado.**

---

# 4. O que é uma Branch?

Uma **branch** é uma linha de desenvolvimento dentro do histórico do Git.

Ela permite que alterações sejam desenvolvidas de maneira isolada, sem modificar diretamente outra linha do projeto.

Exemplo:

```text
main
 |
 +--- desenvolvimento
 |        |
 |        +--- nova-funcionalidade
 |        |
 |        +--- correcao-bug
 |
 +--- outra-funcionalidade
```

Uma equipe pode utilizar branches para separar diferentes tipos de trabalho.

Exemplo:

```text
main
 |
 +--- feature/login
 |
 +--- feature/relatorio
 |
 +--- bugfix/autenticacao
 |
 +--- hotfix/erro-producao
```

## 4.1. Por que utilizar branches?

Branches ajudam a:

- desenvolver funcionalidades isoladamente;
- corrigir bugs;
- experimentar alterações;
- trabalhar em paralelo;
- evitar alterações diretas na `main`;
- organizar o trabalho da equipe;
- permitir revisão antes da integração.

Uma ideia importante:

> **Branch é uma linha de desenvolvimento dentro do histórico do Git.**

Ela não deve ser entendida simplesmente como uma "cópia permanente" do projeto.

---

# 5. O que é um Merge Request?

Um **Merge Request (MR)** é uma solicitação para incorporar as alterações de uma branch em outra.

Exemplo:

```text
feature/login
      |
      | Merge Request
      v
     main
```

O desenvolvedor trabalha na branch:

```text
feature/login
```

Depois envia essa branch para o GitLab e abre um Merge Request.

A equipe pode então:

1. visualizar as alterações;
2. revisar o código;
3. comentar;
4. solicitar alterações;
5. executar testes;
6. aprovar;
7. realizar o merge.

## 5.1. Analogia simples

Podemos pensar assim:

```text
Commit
   ↓
Registrar uma alteração

Branch
   ↓
Criar uma linha de desenvolvimento

Merge Request
   ↓
Solicitar a integração dessa linha de desenvolvimento
```

---

# 6. O que é o Git e para que serve?

O **Git é um sistema distribuído de controle de versão**.

Ele permite registrar a evolução de um projeto ao longo do tempo.

Um histórico Git pode ser representado simplificadamente assim:

```text
Commit A
   |
   v
Commit B
   |
   v
Commit C
   |
   v
Commit D
```

Cada commit representa um estado registrado do projeto.

O Git permite:

- saber quais alterações foram realizadas;
- identificar quando alterações foram realizadas;
- identificar quem realizou alterações;
- consultar o histórico;
- criar branches;
- combinar alterações;
- recuperar estados anteriores;
- trabalhar em equipe.

---

# 7. Comandos básicos do Git

| Comando | Função |
|---|---|
| `git clone` | Clonar um repositório |
| `git init` | Inicializar um repositório Git |
| `git status` | Verificar o estado atual |
| `git add` | Preparar alterações para commit |
| `git commit` | Registrar alterações |
| `git log` | Consultar histórico |
| `git branch` | Listar ou criar branches |
| `git switch` | Trocar de branch |
| `git merge` | Unir históricos |
| `git fetch` | Buscar informações do remoto |
| `git pull` | Buscar e integrar alterações |
| `git push` | Enviar alterações para o remoto |
| `git diff` | Comparar alterações |
| `git restore` | Restaurar arquivos |
| `git remote` | Gerenciar repositórios remotos |

---

# 8. Fluxo básico de trabalho em equipe

Um fluxo comum é:

```text
git pull
    |
    v
Alterar código
    |
    v
git status
    |
    v
git add
    |
    v
git commit
    |
    v
git push
    |
    v
Merge Request
    |
    v
Revisão
    |
    v
Merge
```

Exemplo:

```bash
git pull

# realizar alterações

git status

git add .

git commit -m "Adiciona nova funcionalidade"

git push origin minha-branch
```

Depois disso, normalmente será criado um Merge Request.

---

# 9. Conflitos no Git

Um conflito ocorre quando o Git encontra alterações incompatíveis e não consegue determinar automaticamente qual versão deve ser utilizada.

Por exemplo:

Branch A:

```text
nome = "João"
```

Branch B:

```text
nome = "Maria"
```

Se as duas alterações forem realizadas na mesma região de um arquivo, o Git poderá solicitar uma decisão humana.

O conflito não significa necessariamente que o Git "deu erro".

Significa:

> **O Git precisa que alguém determine como as alterações devem ser combinadas.**

---

# 10. O que é o GitLab CLI?

O **GitLab CLI**, normalmente utilizado por meio do comando `glab`, permite interagir com o GitLab diretamente pelo terminal.

Exemplo:

```bash
glab auth login
```

Depois da autenticação, é possível executar diversas operações relacionadas ao GitLab.

Por exemplo:

```bash
glab mr create
```

para criar um Merge Request pelo terminal.

O `glab` pode ser utilizado para trabalhar com:

- Merge Requests;
- Issues;
- projetos;
- pipelines;
- branches;
- releases;
- autenticação;
- informações do GitLab.

## 10.1. Git × GitLab × glab

```text
Git
 |
 +-- Controle de versão

GitLab
 |
 +-- Plataforma de colaboração

glab
 |
 +-- Interface de linha de comando para o GitLab
```

---

# 11. Problema 1 — Integração de sistemas já existentes ao GitLab institucional

Agora vamos sair da teoria e analisar um problema real.

A instituição possuía um GitLab empresarial restrito.

Ao criar um novo repositório, o GitLab institucional já disponibilizava:

- uma branch `main`;
- um `README` padrão;
- regras institucionais;
- proteção da `main`.

A `main` não permitia alterações diretas.

Alterações deveriam ser realizadas por meio de Merge Requests.

## 11.1. O problema

Alguns sistemas já existiam localmente e já possuíam histórico Git.

Por exemplo:

```text
REPOSITÓRIO LOCAL

A --- B --- C --- D
```

Ao mesmo tempo, o GitLab havia criado:

```text
REPOSITÓRIO GITLAB

X --- Y
```

São dois históricos independentes.

O Git não possui uma ancestralidade comum entre:

```text
A --- B --- C --- D
```

e:

```text
X --- Y
```

Portanto, não é possível simplesmente tratar os dois como se fossem uma única linha histórica.

---

# 12. Solução — Integração dos dois históricos

O objetivo é transformar:

```text
LOCAL

A --- B --- C --- D


REMOTO

X --- Y
```

em um histórico integrado:

```text
          A --- B --- C --- D
         /                   \
        /                     M
       /                     /
      X -------- Y --------
```

O commit `M` representa o merge dos históricos.

---

# 13. Etapa 1 — Adicionar o repositório remoto

Primeiro, adicionamos o repositório GitLab ao projeto local:

```bash
git remote add origin <URL_DO_REPOSITORIO>
```

Isso cria uma referência chamada:

```text
origin
```

Podemos verificar:

```bash
git remote -v
```

---

# 14. Etapa 2 — Buscar as informações do remoto

Executamos:

```bash
git fetch origin
```

O `fetch` busca informações do repositório remoto sem realizar automaticamente um merge na branch atual.

Depois disso, podemos ter referências como:

```text
branch local
    |
    +--- histórico local


origin/main
    |
    +--- histórico institucional
```

---

# 15. Etapa 3 — Renomear a branch local

Como a `main` local não deve conflitar conceitualmente com a `main` institucional, podemos renomeá-la.

Exemplo:

```bash
git branch -m desenvolvimento
```

Ou, se a branch atual for `main`:

```bash
git branch -m main desenvolvimento
```

Passamos a ter:

```text
desenvolvimento
    |
    +--- histórico original do sistema
```

Enquanto o remoto possui:

```text
origin/main
    |
    +--- histórico institucional
```

---

# 16. Etapa 4 — Unir os históricos

Executamos:

```bash
git merge --allow-unrelated-histories origin/main
```

O parâmetro:

```text
--allow-unrelated-histories
```

permite que o Git realize um merge entre históricos que não possuem ancestral comum.

Esse parâmetro deve ser utilizado de maneira consciente.

Ele não significa:

> "Ignore todos os conflitos."

Ele significa:

> "Eu sei que esses históricos não possuem uma ancestralidade comum e autorizo o Git a tentar integrá-los."

---

# 17. Etapa 5 — Resolver conflitos

Um conflito pode surgir, por exemplo, no:

```text
README.md
```

porque o arquivo existe tanto no projeto local quanto no repositório GitLab.

Podemos verificar:

```bash
git status
```

O Git indicará os arquivos que precisam ser resolvidos.

---

# 18. `ours` e `theirs`

Esta é uma das partes mais importantes para evitar erros.

Durante um merge, existem dois lados:

```text
                 MERGE
                   |
          +--------+--------+
          |                 |
        OURS              THEIRS
          |                 |
    branch atual       branch que está
                       sendo incorporada
```

Se quisermos manter a versão do arquivo correspondente ao lado atual:

```bash
git restore --ours README.md
```

Também pode ser encontrada a forma tradicional:

```bash
git checkout --ours README.md
```

Se quisermos manter a versão correspondente ao outro lado:

```bash
git restore --theirs README.md
```

Ou:

```bash
git checkout --theirs README.md
```

## 18.1. Atenção

`ours` não significa necessariamente:

> "arquivo que está no meu computador".

`ours` significa:

> **o lado correspondente à branch atual durante aquele merge.**

Da mesma forma:

> `theirs` corresponde ao outro lado do merge.

Essa interpretação é fundamental para evitar a preservação acidental da versão errada.

---

# 19. Registrar a resolução do conflito

Depois de decidir qual versão deve permanecer:

```bash
git add README.md
```

Se houver outros arquivos:

```bash
git add .
```

Depois:

```bash
git commit
```

O commit registra a resolução e a integração dos históricos.

---

# 20. Publicar a nova branch

Agora podemos enviar a branch para o GitLab:

```bash
git push origin desenvolvimento
```

No GitLab teremos algo semelhante a:

```text
main
 |
 +--- histórico institucional


desenvolvimento
 |
 +--- histórico do sistema integrado
```

A `main` continua protegida.

---

# 21. Criar o Merge Request

Agora criamos:

```text
desenvolvimento
       |
       | Merge Request
       v
      main
```

O Merge Request é a etapa formal de integração com a branch principal.

A equipe pode:

- revisar as alterações;
- verificar o histórico;
- executar testes;
- discutir alterações;
- aprovar;
- realizar o merge.

Dependendo das regras do projeto, o merge poderá exigir aprovação de usuários com permissões específicas.

---

# 22. Pode ser feito tudo pelo terminal?

Sim.

O Git permite realizar a parte relacionada ao versionamento e aos merges localmente.

O GitLab CLI (`glab`) também permite interagir com recursos do GitLab pelo terminal.

Por exemplo:

```bash
glab mr create
```

Entretanto, em ambientes institucionais, a utilização da interface web pode continuar sendo importante para:

- revisão visual;
- aprovação;
- auditoria;
- acompanhamento;
- visualização de pipelines;
- colaboração da equipe.

O processo pode ser realizado pelo terminal, mas as regras de permissão do GitLab continuam valendo.

---

# 23. Problema 2 — Sistemas existentes sem documentação

Depois de resolver o problema de versionamento, surge outro problema:

> **Um sistema estar versionado não significa que ele esteja documentado ou compreendido.**

Muitos sistemas existentes possuem:

- documentação incompleta;
- documentação desatualizada;
- conhecimento concentrado em poucas pessoas;
- código legado;
- regras de negócio não documentadas;
- dependências desconhecidas;
- configurações pouco claras;
- dificuldade de manutenção.

Podemos representar o problema assim:

```text
Código existente
      |
      v
Pouca documentação
      |
      v
Conhecimento concentrado
      |
      v
Dificuldade de manutenção
      |
      v
Dificuldade de expansão
      |
      v
Risco operacional
```

---

# 24. Como resolver?

Uma das ferramentas utilizadas para acelerar esse processo foi um **agente de IA para desenvolvimento**, como o Claude Code.

A ideia não é simplesmente:

> "Mandar a IA escrever uma documentação."

A proposta é utilizar a IA como uma ferramenta auxiliar de engenharia de software.

Ela pode auxiliar na:

- descoberta da arquitetura;
- análise do código;
- identificação de dependências;
- compreensão dos fluxos;
- identificação de regras de negócio;
- identificação de duplicações;
- identificação de problemas;
- análise de segurança;
- refatoração;
- produção de documentação.

---

# 25. IA não substitui a validação humana

Um ponto fundamental da metodologia é que o agente de IA não deve ser tratado como autoridade absoluta sobre o sistema.

O fluxo deve ser:

```text
Sistema
   |
   v
IA analisa
   |
   v
IA produz hipóteses e documentação
   |
   v
Humano valida
   |
   v
Documentação consolidada
```

A IA pode interpretar incorretamente:

- regras de negócio;
- intenção do desenvolvedor;
- comportamentos implícitos;
- configurações;
- dependências;
- funcionalidades.

Portanto:

> **A documentação gerada por IA deve ser validada contra o sistema real.**

---

# 26. Evolução dos prompts

A qualidade do resultado depende também da qualidade das instruções fornecidas ao agente.

Um prompt inicial poderia ser:

```text
Analise este projeto e crie uma documentação.
```

Esse prompt é muito aberto.

O agente pode produzir algo superficial.

---

# 27. Evolução — Prompt estruturado

Podemos começar a exigir informações específicas:

- arquitetura;
- tecnologias;
- banco de dados;
- funcionalidades;
- dependências;
- configuração;
- instalação;
- problemas conhecidos.

Exemplo:

```text
Analise o projeto e documente:

1. Arquitetura
2. Tecnologias
3. Banco de dados
4. Funcionalidades
5. Dependências
6. Configuração
7. Instalação
8. Problemas conhecidos
```

Já temos maior controle.

---

# 28. Evolução — Análise profunda

Depois podemos exigir:

- análise arquivo por arquivo;
- análise detalhada do código;
- arquitetura;
- segurança;
- pontos fracos;
- falhas;
- dívida técnica;
- dependências;
- regras de negócio;
- integrações.

A ideia passa a ser:

> **Não apenas documentar aquilo que parece existir, mas investigar o sistema para descobrir como ele realmente funciona.**

---

# 29. Framework de documentação em múltiplas fases

A abordagem pode ser organizada em fases.

```text
FASE 0
READ-ONLY DISCOVERY
        |
        v
FASE 1
INVENTÁRIO
        |
        v
FASE 2
ARQUITETURA
        |
        v
FASE 3
ANÁLISE DETALHADA
        |
        v
FASE 4
SEGURANÇA E PROBLEMAS
        |
        v
FASE 5
DOCUMENTAÇÃO
        |
        v
FASE 6
VALIDAÇÃO
```

---

# 30. FASE 0 — Read-Only Discovery Mode

Antes de permitir modificações, o agente deve primeiro compreender o sistema.

Durante essa fase:

- não modificar código;
- não excluir arquivos;
- não executar refatorações destrutivas;
- não alterar configurações;
- não realizar commits;
- não alterar a estrutura do projeto.

O objetivo é:

> **Descobrir antes de modificar.**

Isso reduz o risco de uma IA realizar alterações prematuras baseadas em uma compreensão incompleta do sistema.

---

# 31. FASE 1 — Inventário

O agente deve identificar:

- estrutura de diretórios;
- arquivos;
- linguagens;
- frameworks;
- bibliotecas;
- dependências;
- banco de dados;
- APIs;
- serviços externos;
- scripts;
- configurações;
- arquivos de ambiente;
- mecanismos de autenticação;
- mecanismos de autorização.

O resultado é um mapa inicial do sistema.

---

# 32. FASE 2 — Arquitetura

O agente deve explicar:

- componentes;
- responsabilidades;
- comunicação entre componentes;
- fluxo de dados;
- banco de dados;
- APIs;
- frontend;
- backend;
- serviços externos;
- autenticação;
- autorização.

Exemplo:

```text
Frontend
   |
   v
API / Backend
   |
   +------> Banco de dados
   |
   +------> Serviço externo
```

---

# 33. FASE 3 — Análise detalhada

Nesta fase o agente investiga o código.

Pode analisar:

- arquivos;
- classes;
- funções;
- módulos;
- consultas;
- endpoints;
- componentes;
- regras de negócio;
- fluxos;
- dependências.

Quando necessário, pode ser realizada análise linha a linha de trechos críticos.

O objetivo não é necessariamente escrever uma explicação de cada linha, mas compreender suficientemente o código para documentar seu comportamento.

---

# 34. FASE 4 — Segurança e problemas

O agente deve procurar:

- credenciais expostas;
- configurações inseguras;
- problemas de autenticação;
- problemas de autorização;
- validação insuficiente;
- consultas inseguras;
- exposição de informações;
- dependências vulneráveis;
- código duplicado;
- código morto;
- pontos frágeis;
- problemas de manutenção;
- dívida técnica.

As conclusões devem ser tratadas como resultados de análise e devem ser validadas antes de serem consideradas definitivas.

---

# 35. FASE 5 — Documentação

A documentação pode ser organizada em:

```text
docs/
├── README.md
├── architecture.md
├── installation.md
├── configuration.md
├── database.md
├── api.md
├── security.md
├── business-rules.md
├── dependencies.md
├── known-issues.md
├── technical-debt.md
└── maintenance.md
```

A estrutura exata deve ser adaptada ao sistema.

O importante é que a documentação tenha utilidade prática.

---

# 36. FASE 6 — Validação

A documentação deve ser comparada com o sistema real.

Perguntas importantes:

- A arquitetura documentada corresponde ao código?
- Os endpoints realmente existem?
- O banco de dados corresponde à documentação?
- As regras de negócio estão corretas?
- As instruções de instalação funcionam?
- As configurações estão corretas?
- Os problemas identificados são reais?
- Existem informações que não foram documentadas?

A documentação deve ser considerada um artefato vivo.

Quando o sistema mudar, a documentação também deverá ser revisada.

---

# 37. O que o Prompt pede?

O prompt estruturado pode ser dividido em seis grandes perguntas.

## 37.1. Descoberta

> O que existe neste sistema?

## 37.2. Compreensão

> Como as partes do sistema se relacionam?

## 37.3. Funcionamento

> Como o sistema funciona?

## 37.4. Auditoria

> Quais são os problemas, riscos e pontos fracos?

## 37.5. Documentação

> Como transformar esse conhecimento em documentação útil?

## 37.6. Validação

> Como verificar se a documentação corresponde ao sistema real?

---

# 38. Qual é o retorno esperado?

O objetivo não é simplesmente gerar vários arquivos Markdown.

O objetivo é transformar:

```text
"Código que poucas pessoas conhecem"
```

em:

```text
"Sistema cujo funcionamento pode ser
compreendido e mantido por outras pessoas."
```

Uma documentação adequada deve permitir que uma nova pessoa consiga, progressivamente:

1. entender o propósito do sistema;
2. instalar o ambiente;
3. compreender a arquitetura;
4. compreender o banco;
5. entender os principais fluxos;
6. localizar funcionalidades;
7. identificar dependências;
8. diagnosticar problemas;
9. realizar manutenção;
10. continuar a evolução do sistema.

---

# 39. Evolução dos prompts e economia de tokens

Durante o desenvolvimento dos prompts, é possível perceber que um prompt muito grande pode consumir uma quantidade significativa de tokens.

Uma estratégia utilizada foi estruturar e consolidar o prompt e posteriormente mantê-lo em inglês quando isso oferecia melhor eficiência no contexto do agente utilizado.

Entretanto, a documentação produzida pelo agente pode continuar seguindo uma exigência explícita:

> **Toda a documentação deve ser produzida em português brasileiro.**

Assim temos:

```text
Prompt de instrução
        |
        v
Pode ser escrito em inglês
        |
        v
Agente executa a análise
        |
        v
Documentação final
        |
        v
Português brasileiro
```

O idioma do prompt e o idioma desejado para o artefato produzido são coisas diferentes.

---

# 40. Safe Stop-and-Report Protocol

Um agente que trabalha sobre um sistema real precisa saber quando parar.

O prompt pode estabelecer um protocolo de parada segura.

O agente deve interromper a execução e reportar o problema quando:

- encontrar informações insuficientes;
- identificar uma operação potencialmente destrutiva;
- encontrar uma inconsistência importante;
- não conseguir determinar a intenção do sistema;
- precisar de uma decisão humana;
- identificar risco significativo;
- encontrar conflito entre documentação e código;
- não possuir autorização para determinada alteração.

A ideia é:

```text
Problema crítico
      |
      v
PARAR
      |
      v
REPORTAR
      |
      v
AGUARDAR DECISÃO HUMANA
```

Em vez de:

```text
Problema crítico
      |
      v
IA decide sozinha
      |
      v
Altera o sistema
```

---

# 41. IA como ferramenta de engenharia

A utilização de IA deve ser entendida como parte de um processo de engenharia, e não como substituição do conhecimento técnico.

Um bom processo é:

```text
Engenheiro
    |
    +----> Define objetivo
    |
    +----> Define restrições
    |
    +----> Orienta o agente
    |
    v
Agente de IA
    |
    +----> Analisa
    |
    +----> Sugere
    |
    +----> Documenta
    |
    +----> Executa tarefas autorizadas
    |
    v
Engenheiro
    |
    +----> Revisa
    |
    +----> Valida
    |
    +----> Decide
```

A responsabilidade final sobre as decisões técnicas continua sendo humana.

---

# 42. Integração das duas experiências

Os dois problemas apresentados parecem diferentes, mas possuem uma relação.

## Problema 1

### Versionamento

Sistemas existentes precisavam ser incorporados ao ambiente institucional.

```text
Sistema
   ↓
Git
   ↓
GitLab
   ↓
Controle de versão
```

## Problema 2

### Conhecimento

Sistemas existentes precisavam ser compreendidos e documentados.

```text
Sistema
   ↓
Análise
   ↓
IA
   ↓
Documentação
   ↓
Conhecimento compartilhado
```

---

# 43. A visão geral

Podemos resumir a capacitação assim:

```text
                    SISTEMA
                       |
            +----------+----------+
            |                     |
            v                     v
       VERSIONAMENTO          CONHECIMENTO
            |                     |
            v                     v
           Git                  IA
            |                     |
            v                     v
         GitLab             Documentação
            |                     |
            +----------+----------+
                       |
                       v
              Manutenção e evolução
```

---

# 44. Conceitos fundamentais para memorizar

## Git

> Sistema de controle de versão.

## GitLab

> Plataforma de colaboração e gerenciamento baseada em Git.

## Branch

> Linha de desenvolvimento.

## Commit

> Registro de uma alteração no histórico.

## Merge

> Integração de históricos ou alterações.

## Merge Request

> Solicitação para integrar uma branch em outra, normalmente com revisão.

## GitLab CLI

> Ferramenta para interagir com o GitLab pelo terminal.

## Conflito

> Situação em que o Git não consegue determinar automaticamente como combinar alterações.

## IA

> Ferramenta auxiliar para análise, desenvolvimento, documentação e outras tarefas, sob orientação e validação humana.

---

# 45. Fluxo recomendado de trabalho

Para um novo desenvolvimento:

```text
1. Atualizar projeto
       ↓
2. Criar branch
       ↓
3. Desenvolver
       ↓
4. Testar
       ↓
5. Commit
       ↓
6. Push
       ↓
7. Merge Request
       ↓
8. Revisão
       ↓
9. Aprovação
       ↓
10. Merge
```

Para um sistema legado:

```text
1. Descobrir
       ↓
2. Versionar
       ↓
3. Analisar
       ↓
4. Documentar
       ↓
5. Validar
       ↓
6. Corrigir/refatorar
       ↓
7. Testar
       ↓
8. Manter
```

---

# 46. Conclusão

O objetivo de utilizar Git, GitLab, documentação e IA não é simplesmente adotar ferramentas novas.

O objetivo é melhorar a capacidade da equipe de:

- compreender sistemas;
- controlar alterações;
- trabalhar em conjunto;
- revisar código;
- preservar conhecimento;
- identificar problemas;
- realizar manutenção;
- reduzir dependência de conhecimento individual;
- evoluir sistemas existentes com maior segurança.

A ideia central pode ser resumida em:

> **"Tornar os sistemas mais fáceis de compreender, manter, compartilhar e evoluir."**

---

# 47. Exercício prático sugerido

Ao final da capacitação, cada participante pode realizar um pequeno exercício.

## Parte 1 — Git

1. Criar um repositório local.
2. Criar um arquivo.
3. Executar `git add`.
4. Executar `git commit`.
5. Criar uma branch.
6. Alterar o arquivo.
7. Criar outro commit.
8. Fazer o merge.
9. Simular um conflito.
10. Resolver o conflito.

## Parte 2 — GitLab

1. Criar ou utilizar um projeto.
2. Criar uma branch.
3. Realizar uma alteração.
4. Fazer `push`.
5. Criar um Merge Request.
6. Revisar a alteração.
7. Realizar o merge.

## Parte 3 — IA

Escolher um pequeno projeto existente e solicitar ao agente:

1. realizar descoberta somente leitura;
2. identificar tecnologias;
3. identificar arquitetura;
4. identificar dependências;
5. identificar funcionalidades;
6. identificar problemas;
7. gerar documentação;
8. apresentar dúvidas e pontos que exigem validação humana.

---

# 48. Mensagem final

O conhecimento técnico de uma equipe não deve permanecer apenas na cabeça de quem originalmente desenvolveu o sistema.

O código deve possuir histórico.

O sistema deve possuir documentação.

As alterações devem possuir revisão.

As decisões importantes devem possuir contexto.

E as ferramentas de IA podem ser utilizadas para acelerar esse trabalho, desde que sejam utilizadas dentro de um processo controlado, com objetivos claros, restrições bem definidas e validação humana.

```text
Código
  +
Histórico
  +
Documentação
  +
Processo
  +
Conhecimento compartilhado
  =
Sistema mais sustentável
```