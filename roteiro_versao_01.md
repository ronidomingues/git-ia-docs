# Capacitação GitLab, Git, GitLab CLI e Resolução de Problemas na Marinha

1. O que é o GitLab e para que serve?

- Explicar as diferenças principais entre o GitLab e o GitHub

- Explicar que o GitLab possui uma versão instalável em sua infraestrutura própria, o que permite as emporesas a utuilizá-lo para evitar de enviar seus dados pra fora, mantendo-os bem versionados e localmente em seus servidores.

1.a O que é uma branch e para que serve?

1.b O que é um merge request e para que serve?

2. O que é o Git e para que serve?

2.a Comandos básicos, para trabalho em equipe e conflitos ocasionais.

3. O que é o gitlab-cli e para que serve?

4. O problema 1 que tive que resolver na Marinha:
A Marinha possui um Gitlab Empresarial restrito com a Branch main já criada e bloqueada para alterações, ou seja, a instituição cria novos repositórios diretamente comela criada, um README padrão e bloqueada para alterações diretas, alyteraçõs nela somente via merge requeste, com isso, essa bramnch não possui ligação de histórico com os projetos que já se encontravam localmente versionados.

5. a. Como resolver?

Git add remote: para dar ao git local um repo remoto, ou seja adicionando uma origin;

Git fetch origin: para baixar as atualizações do remoto lado lado das atualizações locais;

Git branch -m <novo nome>: renomeando a branch main local para que não conflite com a main do remoto que está bloqueada;

git merge --allow-unrelated-histories origin/main: fazendo o merge da branch remota na branch local permitindo/forçando merge sem histórico relacionado, isso gera o conflito do README, entre o local e o remoto;

**Git checkout --ours README.md: isso garante que o nosso (ours) README seja preservado e o da remota seja finalizado na linha do histórico;

** Aqui entra uma questão importante de interpretação para não cometer erros, nesse ponto partimos de pontos de vista, no nosso caso estamos branch local que mudamos de nome, e queremos manter o README que esta nela, ou seja, o README da branch em que estamos, ou seja, o que entendemos como o nosso(ours), caso quiséssemos manter o deles, no caso o da branch em que não estamos, o comando seria (theirs, que siguinifica Deles).

git commit: Para gravar as mudanças no histórico;

git push origin <novo nome> para subir(Aqui ele sobe e cria a nova branch no gitlab ao lado da main original);
Merge Request: Esse é o ponto final e fundamental de todo o processo de união que fizemos, foi a união feita que permite agora a relação de histórico e essa relação permite a fusão da main original com a local e com todoa os erros tratados, agora não mais há conflitos e o mkerge flui sem recusar, esse merge é feito oinline e com aprovação de alguém que tenha acesso adm no repositório. Esse processo é feito online na plataforma do GitLab, pode ser feito localmente? Sim, mas vc precisa ter instalado o gitlab-cli e fazer o processo via terminal;

6. O Problema 2:

Os Sistemas já existentes e pré versionados, alguns legados, não possuiam, em sua maioria, nenhuma documentação.

6.a. Como resolvi?

Uso de Agente de IA da Claude Code para acelerar o processo de entendimento do sistema, refatoração e documentação profunda.

6. b. Prompts para documentação: Evolução dos prompts e adaptações necessárias, por fim chegando a versão final traduzida para o inglês para economizar Tokens da IA.

6. b. a. O que o Prompt pede e qual seu retorno?