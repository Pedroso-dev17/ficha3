# RISICCO V6 — STREET LUXURY / CINEMATIC EDITION (06-11-2026)

## Identidade da V6

A V6 mantém **toda a estrutura e o conteúdo da V5.1**, incluindo as 18 tabelas, autenticação, área privada, projetos, orçamentos, equipa, portefólio de demonstração, serviços e personalização mesmo sem login. A direção artística foi desenvolvida com base na imagem do cartaz RISICCO entregue pelo autor: **preto profundo, ouro/amarelo, grafite à mão, halftone e molduras luminosas**. Não se usam imagens fictícias como capturas do website.

**Abertura obrigatória intacta:** bobina + auscultadores a rodar da direita para a esquerda, letras RISICCO reveladas uma a uma, portal de passagem, opção saltar, replay e respeito por `prefers-reduced-motion`. O comportamento predefinido é voltar a mostrar a introdução ao abrir a homepage. Isto não pode ser retirado em futuras revisões.

### Alterações visuais

- `public/assets/css/street-luxury-v6.css` é a nova camada visual, colocada **depois** de todas as CSS anteriores.
- `public/assets/svg/urban-marks-v6.svg` reúne rabiscos originais: coroas, setas, estrelas e marcas urbanas discretas.
- O menu desktop e o menu mobile de ecrã inteiro ganharam linguagem de **painel de cinema urbano** com letras editoriais, bordas ouro, numeração e foco acessível.
- A homepage mantém a colagem original; moldura, halo e sombras foram redesenhados para corresponder ao cartaz, sem usar um print falso no lugar do site.
- Serviços, trabalhos, equipa, login, laboratório de personalização, dashboard e gestão ganham o mesmo design system.
- A navegação fora da abertura está no modo **Equilíbrio** por predefinição, com hover e revelações suaves. `CINEMA` e `OFF` continuam opções reais no laboratório.
- As preferências de **Minimalismo** e **Graffiti** seguem independentes, persistindo localmente com ou sem conta.

### Executar

Servidor PHP (rotas autênticas):

```bash
cd RISICCO_SITE_V6
php -S localhost:8000 -t public public/router.php
```

Pré-visualização (site público apenas): extrai **o ZIP inteiro** e abre `RISICCO_V6_PREVIEW/index.html`. Os estilos, scripts, SVG e imagens usam caminhos relativos.

**Nota:** autenticação e dados de projetos precisam de MySQL e validação no ambiente de instalação. A pré-visualização offline não apresenta dashboards falsamente autenticados. Ver a documentação legada abaixo e os resultados de verificação em `docs/QA_V6.md`.

---

# RISICCO V5.1 — PREMIUM EDITORIAL / CINEMATIC INTRO

## Atualização V5.1 — Introdução cinematográfica preservada

A animação de abertura é uma assinatura obrigatória da RISICCO e **não pode ser removida em versões futuras**: bobina com auscultadores a rodar da direita para a esquerda, revelação sequencial de **R I S I C C O.**, portal expansivo e transição visual para o hero. Por predefinição, **reproduz sempre ao entrar na homepage**, mesmo depois de uma visita anterior. A migração da preferência antiga `first` para `always` acontece uma vez em navegadores que guardavam o comportamento legado. Uma escolha explícita de desligar a introdução continua disponível para conforto/acessibilidade; `prefers-reduced-motion` é sempre respeitado. Botões **SALTAR INTRODUÇÃO** e **REVER ABERTURA / REVER INTRO** continuam presentes. A demo offline usa exatamente o mesmo JavaScript e CSS da versão PHP.

**Verificação para a apresentação da PAP:** extrai todo o ficheiro ZIP; abre `RISICCO_V5_1_PREVIEW/index.html` e recarrega a homepage. A entrada deve aparecer em ambas as visitas, salvo movimento reduzido ou desativação explícita. Clica em `REVER ABERTURA` na homepage para a repetir manualmente. Para testar o CSS, confirma que o símbolo e a imagem central carregam, e que os títulos usam o estilo editorial.


**Versão 5.0, PAP 2026–2027.** Esta atualização resolve o problema da V4, em que a pré-visualização HTML utilizava caminhos absolutos (`/assets/...`) e abria sem CSS ao fazer duplo clique. Na V5, os recursos da pré-visualização são referidos por caminhos relativos e foram verificados em 23 páginas. O projeto PHP mantém caminhos absolutos próprios para o servidor, como é correto.

**Novidades:** nova camada visual `public/assets/css/premium-v5.css`, tipografia fluida para evitar sobreposições, layout editorial responsivo, animações e transições elegantes, linhas e setas estilo grafite original em SVG (`public/assets/svg/street-ink.svg`), dashboard e administração com acabamento mais cuidado. As opções **Modo Minimalista** e **Traços Urbanos / Graffiti** permanecem funcionais e aplicam-se com ou sem login. O armazenamento local é feito no navegador; contas autenticadas podem sincronizar as preferências com MySQL.

**Comandos úteis:** `php -S localhost:8000 -t public public/router.php` para iniciar o servidor na pasta do projeto. `php scripts/export_preview.php preview` seguido de `python scripts/build_static_v5.py preview` gera uma nova exportação offline das páginas públicas.

**Qualidade / limitações:** foram validados automaticamente 23 documentos HTML, 857 referências de ficheiros, sintaxe dos scripts PHP e JS, quatro folhas de estilos, e resposta HTTP com CSS real. `/conta` e `/admin` sem sessão redirecionam para `/login`. O navegador Chromium disponível neste ambiente tem a navegação local bloqueada por política; por isso **não afirmamos que houve inspeção visual completa da V5** nem testes end-to-end de registo e MySQL. Realiza essa revisão localmente antes da avaliação. Consultar `docs/QA_V5.md`.

---

# RISICCO. — Estúdio criativo / PAP 2026–2027

Um website multipágina com identidade visual derivada diretamente da arte original fornecida: colagem **preto/branco/amarelo**, bobina de cinema e auscultadores. Inclui uma introdução cinematográfica coreografada, navegação editorial, transições, portefólio demonstrativo, perfis da equipa, login/registo, área de cliente, contacto e um laboratório de personalização.

## Pré-visualização sem instalações

O pacote separado **`RISICCO_V5_PREVIEW_OFFLINE.zip`** contém **23 páginas públicas**. Extrai o ZIP inteiro e faz duplo clique em `RISICCO_V5_PREVIEW/index.html`: o CSS, JavaScript, imagens e desenhos de grafite usam caminhos locais relativos. Ao contrário da V4, não dependem de um servidor para carregar. As páginas privadas não são exportadas. Na pré-visualização não existe autenticação real: os formulários de envio não guardam dados.

## 1. Ver o site em 30 segundos

Requisitos: **PHP 8.1+** (recomendado PHP 8.2–8.4).

```bash
cd RISICCO_SITE_V5
php -S localhost:8000 -t public public/router.php
```

Abre **http://localhost:8000**. A parte pública funciona **sem MySQL**. Testa as rotas no menu ou visita diretamente `/equipa`, `/equipa/membro-01`, `/portfolio`, `/portfolio/frequencia-zero`, `/login` e `/personalizar`.

> **Importante:** Não abras `index.php` por duplo clique (`file://`). Usa um servidor local para obteres as rotas reais.

## 2. Ativar MySQL e contas

1. Instala **MySQL 8+** e ativa a extensão PHP `pdo_mysql` (no XAMPP é geralmente incluída).
2. Importa o ficheiro `sql/schema.mysql.sql` no MySQL (contém **18 tabelas**, incluindo tokens de recuperação).
3. Copia `.env.example` para `.env` e define `DB_DSN`, `DB_USER` e `DB_PASSWORD`.
4. Reinicia o servidor e utiliza `/registo` para criar um cliente.
5. Para promover **um utilizador concreto e autorizado** a administrador, efetua essa ação manualmente na base de dados, num ambiente de desenvolvimento: `UPDATE users SET role='admin' WHERE email='ENDERECO_AUTORIZADO';`. Não há registo público de administradores.

### Estado real das funcionalidades

| Área | Estado | Notas |
| --- | --- | --- |
| Intro cinematográfica com bobina em rotação direita → esquerda, letras sequenciais e portal | **IMPLEMENTADO** | Skip, primeira visita, repetição e movimento reduzido |
| Homepage editorial e microinterações | **IMPLEMENTADO** | Mobile e desktop |
| Rotas reais, URLs diretos, serviços e portefólio | **IMPLEMENTADO** | Renderização no servidor PHP |
| Equipa com três perfis individuais e transição contextual | **IMPLEMENTADO / PERFIS PROVISÓRIOS** | Sem identidades reais inventadas |
| Portefólio | **PROTÓTIPO VISUAL** | Todos os seis conceitos estão marcados como demonstrações, sem fingir clientes |
| Laboratório de personalização | **IMPLEMENTADO** | Temas, cores, movimento, intro, tipografia, contraste, parallax, cursor, layout e presets; `localStorage` para visitantes |
| Registo/login com passwords cifradas por hash, sessão segura e CSRF | **IMPLEMENTADO QUANDO LIGADO AO MYSQL** | Sem DB, mostra indisponibilidade em vez de fingir login |
| Pedidos, orçamentos e área privada | **IMPLEMENTADO QUANDO LIGADO AO MYSQL** | Pedido real, envio de orçamento pelo admin, aceite transacional pelo cliente e projeto criado automaticamente |
| Dashboard do cliente e projetos | **IMPLEMENTADO QUANDO LIGADO AO MYSQL** | Resumo, KPIs, filtros, pesquisa, estados, progresso por etapas e detalhe privado de cada projeto |
| Gestor de projetos da equipa | **IMPLEMENTADO QUANDO LIGADO AO MYSQL** | Administração altera estados, adiciona etapas e altera cada etapa |
| Ficheiros entregues | **DOWNLOAD PRIVADO IMPLEMENTADO** | Apenas ficheiros já registados e fisicamente presentes em `storage/private`; ainda não existe interface de upload |
| Avaliações verificadas | **IMPLEMENTADO PARCIALMENTE** | Só projetos concluídos e próprios; revisão pendente por publicar |
| Recuperação de password | **PARCIAL** | Token de utilização única expira em 30 min; URL local exibida só em desenvolvimento; email de produção ainda não integrado |
| Orçamentos versionados e etapas | **IMPLEMENTADO PARCIALMENTE** | Orçamento enviado em versões, aceitação atómica com bloqueio; gestão detalhada de linhas/impostos e atribuição da equipa ainda pendentes |
| Administração editorial completa | **PARCIAL** | Gestão funcional de pedidos, orçamentos, estados de projeto e etapas; edição do portefólio e uploads pendentes |
| Assistente FAQ | **IMPLEMENTADO COMO FAQ ESTÁTICA** | Não é IA; não guarda conversas |
| Testes automáticos, auditoria de segurança, emails em produção, Lighthouse | **PENDENTE** | Testes manuais de rotas e layout no protótipo; ver lista abaixo |

## 3. Arquitetura

```text
RISICCO_SITE/
  public/
    index.php                # Router HTTP / páginas dinâmicas
    router.php               # Servidor PHP embutido
    .htaccess                # Apache URL rewriting
    assets/
      css/site.css           # Sistema de design + motion + responsive
      css/dashboard.css      # Dashboard do cliente, detalhes e administração
      js/site.js             # Intro, navegação, filtros e preferências
      js/dashboard.js        # Filtros e pesquisa de projetos
      img/                   # Arte original autorizada + símbolo recortado
  app/
    bootstrap.php            # Sessão, CSRF, ligação PDO e conteúdo demo
    handlers.php             # Ações POST com validações e DB
    views.php                # Páginas SSR públicas
    client_dashboard.php     # Dashboard, projetos e downloads privados
    project_actions.php      # Orçamentos, aceitação e administração de projetos
  sql/schema.mysql.sql       # 18 tabelas MySQL 8
  storage/private/           # Entregas reais — fora da pasta pública
  scripts/export_preview.php # Exportação demonstrativa, sem MySQL
  .env.example
  docs/QA.md
```

**Páginas:** `/`, `/servicos`, `/servicos/fotografia`, `/servicos/video`, `/servicos/som`, `/portfolio`, `/portfolio/{slug}`, `/equipa`, `/equipa/{slug}`, `/contacto`, `/avaliacoes`, `/personalizar`, `/login`, `/registo`, `/recuperar-password`, `/redefinir-password`, `/conta`, `/conta/pedidos`, `/conta/orcamentos`, `/conta/projetos`, `/conta/projetos/{id}`, `/conta/entregas`, `/conta/historico`, `/conta/preferencias` e `/admin`, `/admin/orcamentos`, `/admin/projetos` (apenas administradores).

## 4. Próximos passos para uma PAP completa

1. Substituir os três perfis provisórios por fotografias e biografias autorizadas; associar os conteúdos à tabela `members`.
2. Substituir os seis conceitos por trabalhos reais e integrar editor de media e portefólio nas tabelas `portfolio_items` e `portfolio_media`.
3. Expandir a gestão de orçamentos já implementada: linhas do orçamento, impostos aplicáveis validados, revisões, atribuições da equipa e revisões pelo cliente.
4. Criar uma interface de carregamento de entregas para a equipa. A pasta privada e o download autenticado e autorizado por proprietário já estão implementados.
5. Integrar emails transacionais de recuperação, verificação de email, limitador de tentativas distribuído, confirmação de privacidade, políticas legais e registos de auditoria completos.
6. Testar com MySQL a sincronização de preferências e as novas operações de projetos/orçamentos e expandir a administração editorial.
7. Migrar para Laravel/Blade caso o professor autorize, contando migrations auxiliares no limite de 18 tabelas. O protótipo atual usa **PHP MVC simplificado** para manter o número de tabelas e ter uma entrada fácil.
8. Fazer testes de integração, performance, acessibilidade, segurança, backup e recuperação antes de colocar em produção.

## 5. Notas de segurança

- Nunca colocar ficheiros `.env`, media privados nem dumps da BD dentro de `public/`.
- Na implementação atual, formulários POST utilizam token CSRF; palavras-passe são guardadas com `password_hash`; sessões usam cookies HttpOnly/SameSite; consultas usam PDO preparado.
- `APP_ENV=local` apenas no desenvolvimento. **Não lançar em produção** sem transporte de email configurado, rate limiting mais robusto, HTTPS, verificação de email, revisões de segurança e processo de privacidade implementado.
- O design não importa fotografias externas ou conteúdo fictício apresentado como trabalho real. A imagem enviada é o principal elemento gráfico da marca.

## 6. Identidade

O ficheiro `risicco-art.webp` é uma conversão otimizada do material enviado pelo utilizador. `risicco-reel.png` é um recorte do símbolo central (bobina + auscultadores). Todos os outros visuais conceptuais são composições gráficas CSS, sem rostos inventados.

## Validação executada nesta entrega

- `php -l` sem erros em todos os ficheiros PHP; `node --check` sem erros no JavaScript.
- 35 páginas da pré-visualização V2 exportadas com dados inventados identificados; verificar em `RISICCO_PREVIEW_V2.zip`.
- Novas rotas protegidas adicionadas para cada projeto e cada download; acesso por sessão e titular do recurso.
- Rascunho do pedido preservado após redirecionamento para autenticação.
- Modelo SQL contado com 18 tabelas.
- Capturas verificadas para dashboard (desktop/mobile), lista de projetos e cronologia do projeto; JS de filtragem e pesquisa testado.
- **Não testado:** fluxo de conta e operações MySQL, por indisponibilidade do driver `pdo_mysql` neste ambiente; a aplicação não deve ser considerada validada para produção.

## 7. NOVO / Dashboard do cliente e operação real (V2)

**Páginas do cliente, após autenticação**

- `/conta`: dashboard, KPIs reais, projetos ativos e ligações rápidas.
- `/conta/projetos`: todos os projetos do próprio cliente, com pesquisa e filtros pelos estados `planning`, `in_progress`, `review`, `completed`, `cancelled`.
- `/conta/projetos/{id}`: página individual protegida — descrição, datas, equipa atribuída, etapas reais, percentagem `etapas concluídas ÷ etapas totais`, entregas.
- `/conta/pedidos`, `/conta/orcamentos`, `/conta/entregas`, `/conta/historico`, `/conta/preferencias`.
- `/conta/entregas/{id}/download`: descarregamento protegido, apenas para o proprietário; caminho físico seguro sob `storage/private`.

**Fluxo de ponta a ponta com MySQL (dados reais):**

1. O cliente cria uma conta em `/registo` e envia um pedido no formulário `/contacto`.
2. O administrador autorizado entra em `/admin/orcamentos`, define âmbito, valor, validade e envia um orçamento ao cliente (a proposta aparece na conta; email ainda não integrado).
3. Em `/conta/orcamentos`, o cliente aceita a versão enviada e válida. A operação é transacional, impede dois projetos para o mesmo pedido e cria um projeto em **Planeamento**.
4. O administrador abre `/admin/projetos`, seleciona o novo projeto, altera o estado e cria etapas reais (por exemplo, captação, edição e revisão). O cliente passa a ver essas etapas, respetivos estados e progresso calculado.
5. Ao marcar o projeto como **Concluído**, o cliente encontra-o entre os projetos finalizados e pode avaliar se o desejar.
6. Os downloads só surgem quando os respetivos metadados forem criados e os ficheiros colocados em `storage/private`; **a interface de upload é trabalho futuro**.

**Importante:** a pré-visualização estática foi gerada com **dados 100% fictícios explicitamente marcados**, não com projetos guardados na base de dados. A aplicação PHP nunca injeta estes dados artificiais na área de um cliente; a primeira conta real começa vazia. A plataforma necessita de configuração e ensaios com MySQL antes de receber dados de clientes reais.

**Nota de compatibilidade:** o `mb_substr` de fallback foi corrigido para funcionar quando `mbstring` está ausente. Mantém a extensão `mbstring` instalada em produção para melhor suporte a Unicode.

## 8. Versão 3.0 — RISICCO Living Cinema (06/11/2026)

### Animações depois da introdução

- Nova sequência de entrada nas páginas internas (cortinas cinematográficas) que **não bloqueia cliques** e é desligada em movimento reduzido.
- Atmosfera de luz em movimento, película lateral com perfurações, anéis orbitais e feixes discretos no hero.
- Revelações de conteúdo em cascata por secção, títulos revelados palavra a palavra, indicador de cena e progresso ao scroll.
- Efeito 3D responsivo ao cursor em projetos, serviços e cartões da equipa; reflexão luminosa, fluidez e microinterações.
- Novas animações de progresso de projetos, etapas e atividades do dashboard, sem alterar os dados reais do servidor.
- Três novos controlos na página `/personalizar`: **atmosfera animada**, **cartões 3D** e **títulos cinéticos**. As preferências são aplicadas diretamente e aceites no servidor para contas iniciadas.
- O modo **Desligado** e `prefers-reduced-motion` desativam os efeitos não essenciais. As páginas e links continuam acessíveis sem JS.

### Dashboard APENAS com conta de cliente e login válido

A área `/conta` e todas as subrotas exigem `require_client()` no servidor. Esta função exige **sessão ativa**, valida os dados com a tabela `users` e `is_active=1` e confirma `role=client`. Os detalhes são filtrados por `projects.user_id` e os ficheiros também verificam o titular na consulta. Visitantes e contas não autenticadas são redirecionados para `/login`; administradores não acedem à área exclusiva de cliente.

**Mudança importante na pré-visualização:** a partir de V3, o pacote HTML offline exporta **apenas 23 páginas públicas**. Não inclui o dashboard demonstrativo nem páginas de projetos privados. O link de área do cliente aponta para `/login`. Em HTML estático não existe autenticação verdadeira; o acesso privado só funciona na aplicação PHP ligada ao MySQL. Os 18 nomes de tabelas permanecem inalterados.

**Como iniciar:**

1. Extrair `RISICCO_SITE_COMPLETO_V3.zip`.
2. Criar base de dados MySQL 8 e importar `sql/schema.mysql.sql` (18 tabelas).
3. Copiar `.env.example` para `.env` e definir `DB_DSN`, `DB_USER`, `DB_PASSWORD` e o ambiente local.
4. Na pasta `RISICCO_SITE`, executar `php -S localhost:8000 -t public public/router.php`.
5. Aceder a `/registo` e criar uma **conta de cliente válida**; após o registo é criada a sessão de cliente. Também se pode aceder por `/login` com a mesma conta.
6. Entrar em `/conta` para ver projetos reais, inicialmente vazio até serem submetidos pedidos, criados orçamentos e aceites.

**Estado de testes V3:** sintaxe PHP e JavaScript verificada; a renderização e os novos controlos foram verificados no navegador em páginas públicas desktop/mobile; pedidos não autenticados a `/conta`, `/conta/projetos`, detalhes, entregas e `/admin` devolvem `303 /login`. **Fluxos de registo/login reais e isolamento entre dois clientes ainda dependem de testes com PDO MySQL ativo**, não disponível neste ambiente de desenvolvimento. Não declarar a aplicação pronta para produção sem os testes do `docs/QA.md`.


## V5.1 — Intro cinematográfica obrigatória
- **Mantida**: bobina/audiovisual roda da direita para a esquerda, nome RISICCO aparece letra a letra e portal atravessa a homepage.
- **Padrão corrigido**: a introdução é mostrada em cada visita à página inicial; a versão antiga usava \`first\` e deixava de mostrar em visitas seguintes. Preferências legadas com esse padrão são migradas uma vez para \`always\`.
- **Replay manual**: ligação «REVER INTRO ↻» no rodapé de todas as páginas, em /?replay=intro. Também é possível pelo laboratório de personalização.
- O visitante continua a poder saltar ou desativar a introdução deliberadamente; \`prefers-reduced-motion\` evita a sequência por acessibilidade.
- **Regressão**: em futuras versões, não eliminar os elementos \`.intro\`, \`.intro-reel\`, \`.intro-word\`, \`.intro-portal\` e o respetivo timeline de CSS/JS.
