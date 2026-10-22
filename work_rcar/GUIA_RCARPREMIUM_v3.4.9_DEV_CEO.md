# RCarPremium v3.4.9 — Analista de TI (DEV) e autorização exclusiva de CEOs

## O que mudou

- A conta **rafaellimeiracarlos@gmail.com** passa de `CEO` para **`DEV` (Analista de TI)** na inicialização do aplicativo, preservando sua senha anterior e seu histórico local.
- A conta DEV tem acesso às telas administrativas, inclusive relatórios, estoque, notas, pedidos, configurações, permissões e funções anteriormente restritas ao CEO.
- O DEV não pode ser excluído, bloqueado ou rebaixado nas telas de gestão de contas.
- Os CEOs atuais permanecem com seus acessos operacionais. Somente Rafael DEV pode **criar novos CEOs** ou **atribuir/remover o cargo CEO de outra conta**.
- A Central de Gestão de Acessos apresenta a área **Gestão de cargos • exclusivo DEV**, com ações **Adicionar novo CEO**, **Alterar cargo** e **Histórico de autorizações**.
- Cada ação de criação ou alteração de cargo CEO pede novamente a senha atual do Rafael. A confirmação é válida para uma ação e expira em 60 segundos.
- CEOs novos recebem senha provisória forte e são obrigados a alterá-la no primeiro login. Ao promover uma conta já existente para CEO, ela também fica obrigada a trocar a senha.
- Todas as promoções, rebaixamentos e criações de CEO ficam registradas com responsável, usuário-alvo, cargo anterior/novo, ação e data/hora **no histórico local**.
- CEO comum continua podendo cadastrar e gerenciar contas da equipe, mas **não pode alterar qualquer cargo**, nem autorizar CEO.
- A recuperação por token de um CEO somente pode ser iniciada pelo DEV; a recuperação da conta DEV não é liberada por tokens gerados por CEOs comuns.

## Como usar

1. Abra a pasta `work_rcar` no Android Studio e sincronize o Gradle.
2. Entre pelo **Login do CEO** com a conta que já pertence a Rafael. Não é necessário cadastrar uma nova conta.
3. Confira o título **Painel do Analista TI (DEV)** e entre em **Gestão de acessos**.
4. Na seção exclusiva DEV, toque em **Adicionar novo CEO**. Preencha nome, e-mail único e uma senha temporária forte (pelo menos 10 caracteres, maiúscula, minúscula, número e símbolo). Depois informe **a senha atual do Rafael** para autorizar.
5. O novo CEO deverá entrar e substituir a senha inicial.
6. Em qualquer outra conta, use **Alterar cargo • DEV** para promover, rebaixar ou transferir uma função. A alteração é registrada no histórico.
7. Entre como outro CEO: as opções DEV não devem aparecer nem funcionar.

## Testes recomendados

- Rafael mantém acesso ao painel e todas as telas administrativas existentes.
- Renan permanece CEO e não pode promover alguém a CEO, nem remover o DEV.
- Um usuário comum ou gerente não consegue executar ações DEV.
- A criação de CEO falha sem a senha correta do Rafael.
- Uma confirmação de senha só pode autorizar uma ação.
- O novo CEO deve trocar sua senha antes de acessar o painel.
- Ao promover um usuário para CEO, o acesso anterior fica encerrado e a senha deverá ser alterada no próximo login.
- Ao rebaixar CEO, o acesso administrativo deve deixar de funcionar.
- A conta de Rafael não deve apresentar botões de bloquear, excluir nem alterar cargo.
- Uma conta CEO só pode receber token de recuperação quando Rafael DEV está autenticado.

## Segurança e limitações importantes

Esta versão ainda usa **contas, sessão, cargos e histórico em armazenamento local do aplicativo**, como protótipo offline. A verificação do e-mail de Rafael identifica a conta local, **mas não comprova a identidade civil do titular**. O app contém credenciais de demonstração herdadas do projeto anterior. Não é adequado considerar a autorização exclusiva segura contra adulteração do aplicativo, acesso ao armazenamento local ou uso em vários dispositivos.

**Antes do uso comercial**, migre autenticação e permissões para o backend: identidade verificada, senhas e tokens administrados no servidor, MFA para DEV, aprovação online de nomeação/remoção de CEO, auditoria imutável e invalidação de sessões entre dispositivos. Retire credenciais de demonstração do aplicativo e distribua novas senhas por canal seguro. Não use essas contas e senhas predefinidas em produção.

## Compilação

Os arquivos fonte foram revisados, mas o APK não foi compilado neste ambiente: a distribuição Gradle 9.4.1 não está instalada e seu download depende de acesso a `services.gradle.org`.
