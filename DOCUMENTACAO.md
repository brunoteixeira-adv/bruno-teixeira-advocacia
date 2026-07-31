# Site Bruno Teixeira Advocacia — Manual Completo

**Endereço do site:** https://bteixeirasadv.com.br
**Painel de administração:** https://bteixeirasadv.com.br/admin
**Última atualização deste documento:** 30 de julho de 2026

Este manual tem duas partes. A **Parte 1** é para o Dr. Bruno: o que dá para mudar sozinho e como fazer. A **Parte 2** é técnica, para quem for dar manutenção no site.

---

# PARTE 1 — Para o proprietário do site

## 1. O que é este site

É um **site institucional de página única** (o que o mercado chama de *landing page*) com duas áreas extras acopladas:

| Parte | Endereço | O que é |
|---|---|---|
| Página principal | `/` | Rola de cima a baixo em seções: início, sobre, áreas de atuação, contato. Todos os botões levam ao formulário ou ao WhatsApp. |
| Blog | `/artigos.html` | Lista os artigos publicados, com filtro por área do Direito. |
| Artigo | `/artigo.html?slug=...` | A página de leitura de cada artigo. |
| Páginas legais | `/privacidade.html`, `/termos.html`, `/aviso-legal.html` | Exigências de LGPD e das normas de publicidade da OAB. |

**Por que isso importa:** uma landing page é feita para *converter* — o visitante chega, entende o serviço e entra em contato. Ela não foi feita para ter dezenas de páginas. O caminho para crescer sem descaracterizar o site é **publicar artigos**, que é justamente a parte que o senhor controla sozinho.

## 2. Como o site fica no ar (em uma frase)

O conteúdo fica guardado no GitHub; a Netlify observa esse repositório e, **a cada alteração, republica o site sozinho em 1 a 2 minutos**. Não existe botão de "publicar site" — publicar um artigo no painel já dispara tudo.

```
Painel /admin  →  grava no GitHub  →  Netlify reconstrói  →  site no ar
     (você)                                (automático, ~1 a 2 min)
```

## 3. Entrando no painel

1. Acesse **https://bteixeirasadv.com.br/admin**
2. Clique em **Login with Netlify Identity** e informe e-mail e senha.
3. Esqueceu a senha? Use "Forgot password" na mesma tela.

> O convite de acesso é enviado por e-mail pela Netlify. Se ninguém mais precisa entrar, não convide — cada pessoa com acesso pode alterar o site inteiro.

## 4. O que o senhor pode alterar sozinho

### 4.1 Configurações do Site → "Foto, Logo e Dados"

| Campo | Onde aparece no site |
|---|---|
| Logomarca (navbar) | O brasão no topo de todas as páginas |
| Favicon | O ícone da aba do navegador e o ícone quando alguém salva o site na tela inicial do celular |
| Foto Principal | A foto grande da seção "Sobre o Advogado" |
| Nome completo | Identificação interna |
| OAB | O número que aparece no rodapé |
| Telefone / WhatsApp | O telefone do bloco de contato **e** todos os botões de WhatsApp do site |
| Endereço | Registro interno do endereço |
| E-mail | O e-mail do bloco de contato |
| Instagram principal | Registro do perfil |

Depois de alterar, clique em **Publish** (canto superior). Aguarde 1 ou 2 minutos e atualize o site.

> **Atenção com o telefone:** escreva no formato `5574988561132` — código do país (55), DDD (74) e o número, tudo junto, sem espaços, traços ou parênteses. O site formata sozinho na tela. Se escrever errado, os botões de WhatsApp param de funcionar.

### 4.2 Regras para as imagens

Estas regras existem porque o site tem tamanhos fixos. Enviar a imagem errada não quebra nada, mas fica feio.

| Imagem | Formato | Como deve ser |
|---|---|---|
| **Logomarca** | PNG com fundo transparente | **Só o brasão**, sem o texto "Bruno Teixeira" embaixo e sem sobra de espaço em volta. O site exibe com 64 pixels de altura: se a imagem vier com o texto dentro, o brasão fica minúsculo e ilegível. |
| **Favicon** | PNG quadrado, 128×128 ou maior | Só o brasão. Como fica muito pequeno, prefira sobre fundo escuro. |
| **Foto Sobre** | JPG | Retrato na vertical, rosto na parte de cima. |
| **Capa de artigo** | JPG | Horizontal (paisagem). Aparece com 420 pixels de altura, cortada no centro. |

> **Peso do arquivo:** foto tirada do celular costuma ter 4 ou 5 MB e deixa o site lento no 4G. Antes de enviar, reduza para no máximo **300 KB**. Qualquer site de compressão gratuito resolve.

### 4.3 Publicando um artigo

1. No painel, vá em **Artigos** → **New Artigo**.
2. Preencha:
   - **Título** — é o que aparece no Google. Escreva como o cliente pesquisaria: *"Fui demitido sem justa causa, o que fazer?"* funciona melhor que *"Considerações sobre a rescisão contratual"*.
   - **Data de Publicação**
   - **Resumo** — 2 ou 3 linhas. É o textinho que aparece embaixo do título no Google e no card da lista.
   - **Categoria** — Trabalhista, Cível, Previdenciário, Criminal ou Dicas Jurídicas. É o que alimenta os filtros da página de artigos.
   - **Imagem de Capa** — opcional.
   - **Conteúdo** — o texto do artigo.
3. Clique em **Publish**.

**Formatação do conteúdo:** o editor aceita negrito, itálico, listas, links e subtítulos pela barra de ferramentas. Use subtítulos a cada 3 ou 4 parágrafos — ajuda o leitor e ajuda o Google.

**Editar ou excluir:** entre em **Artigos**, clique no artigo, altere e publique de novo. Para excluir, use o menu de três pontos.

### 4.4 O que **não** dá para mudar pelo painel

Estas partes estão escritas dentro do código e precisam de um desenvolvedor:

- Textos da página principal (título de destaque, texto "Sobre o Advogado", frase do banner)
- Os seis cards de "Áreas de Atuação" e as listas dentro deles
- As opções do formulário de contato
- Cores, fontes e todo o layout
- Textos das páginas legais
- Título e descrição que aparecem no Google
- Endereço mostrado no bloco de contato (o campo do painel é apenas um registro)

## 5. O formulário de contato

Quando alguém envia o formulário, os dados vão para um **Google Apps Script** (uma automação do Google, ligada à conta Google do escritório) que registra e/ou encaminha a mensagem.

> **Teste a cada 2 ou 3 meses:** preencha o formulário com seus próprios dados e confirme que a mensagem chegou. Automações do Google podem parar de funcionar sem aviso, e uma mensagem perdida é um cliente perdido. Enquanto isso, o botão flutuante de WhatsApp é o canal mais confiável.

## 6. As ferramentas do Google

### 6.1 Google Analytics — quem visita o site

**Endereço:** https://analytics.google.com · **Código da propriedade:** `G-F5HKN2YQ7W`

Entre com a conta Google do escritório. O que vale olhar, uma vez por mês:

| Onde | O que responde |
|---|---|
| Relatórios → Aquisição de tráfego | De onde vêm as visitas: Google, Instagram, WhatsApp, digitação direta |
| Relatórios → Páginas e telas | Quais artigos são realmente lidos |
| Relatórios → Dados demográficos → Cidade | **De quais cidades chegam as visitas** — é a métrica que mostra se o alcance está passando de Petrolina |

### 6.2 Google Search Console — como o Google enxerga o site

**Endereço:** https://search.google.com/search-console

| Onde | O que responde |
|---|---|
| Desempenho | **Que palavras as pessoas digitaram** antes de chegar ao site. É o melhor guia para escolher o tema do próximo artigo: se aparece "adicional de insalubridade" com muitas exibições e poucos cliques, esse é o artigo a escrever. |
| Páginas | Quais páginas o Google indexou e quais recusou |
| Inspeção de URL | Cola o endereço de um artigo novo e clica em "Solicitar indexação" para apressar a entrada dele no Google |

> Ao publicar um artigo importante, use a **Inspeção de URL** e peça a indexação. Sem isso o Google pode levar dias ou semanas para achar sozinho.

### 6.3 Perfil da Empresa no Google — Maps e busca local

**Endereço:** https://business.google.com

É o que faz o escritório aparecer no Maps e no quadro lateral quando alguém busca "advogado trabalhista Petrolina". O que mantém esse perfil forte:

- **Avaliações de clientes.** É o fator com mais peso na busca local. Pedir a avaliação ao cliente satisfeito, com o link direto, é a ação de maior retorno em todo este manual.
- **Postagens** — o mesmo artigo publicado no site pode virar uma postagem curta no perfil.
- **Dados sempre iguais aos do site**: nome, endereço (com o "Terceiro Andar") e telefone (74) 98856-1132. O Google cruza essas informações; divergência derruba a posição.

## 7. Rotina sugerida

| Frequência | O que fazer |
|---|---|
| Toda semana | Publicar ou revisar um artigo |
| Todo mês | Olhar Analytics (cidades) e Search Console (palavras buscadas) |
| A cada 2 ou 3 meses | Testar o formulário de contato |
| Sempre | Pedir avaliação no Google aos clientes atendidos |

---

# PARTE 2 — Documentação técnica

## 8. Ficha técnica

| Item | Valor |
|---|---|
| Tipo | Site estático — HTML, CSS e JavaScript puros, sem framework e **sem etapa de build** |
| Repositório | `github.com/brunoteixeira-adv/bruno-teixeira-advocacia` (branch `main`) |
| Hospedagem | Netlify — `bruno-teixeira-adv-site.netlify.app`, domínio `bteixeirasadv.com.br` |
| Deploy | Automático a cada commit na `main` |
| CMS | Decap CMS 3 em `/admin`, autenticação Netlify Identity, gravação via Git Gateway direto na `main` |
| Analytics | GA4 `G-F5HKN2YQ7W`, presente nas 6 páginas HTML |
| Formulário | POST para um Google Apps Script (`script.google.com/macros/s/AKfycbw…/exec`) |

## 9. Estrutura de arquivos

```
index.html          Landing page (todas as seções)
artigos.html        Lista de artigos
artigo.html         Leitor de artigo individual (?slug=)
privacidade.html    ┐
termos.html         ├ Páginas legais
aviso-legal.html    ┘
style.css           Folha de estilo única de todo o site
script.js           Menu, scroll, animações, formulário e carga do perfil.json
artigos.js          Lista e filtra os artigos
artigo.js           Renderiza um artigo e monta o SEO dele
_config/perfil.json Dados editáveis pelo CMS
artigos/*.md        Um arquivo por artigo (frontmatter + markdown)
imagens/            Mídia enviada pelo CMS (media_folder)
admin/              Decap CMS (index.html + config.yml)
sitemap.xml         Mapa do site, estático
robots.txt          Libera indexação e aponta o sitemap
```

## 10. Como o `perfil.json` chega na tela

O `_config/perfil.json` não é lido em tempo de build — é buscado pelo navegador e aplicado por JavaScript:

- **`script.js`** (todas as páginas): aplica `logo` em `#logo-img`/`.logo-mark` e `favicon` em todos os `<link rel="icon">` e `apple-touch-icon`.
- **`index.html`** (bloco inline): aplica `foto_sobre`, `oab`, `telefone` (formata e reescreve todos os links `wa.me`) e `email`.

Consequência: o HTML entregue tem valores padrão que são substituídos após o carregamento. Ao alterar qualquer um desses dados no código, altere **também** o `perfil.json`, senão o CMS sobrescreve.

## 11. Dimensionamento da logo

A classe `.logo-mark` no `style.css` controla a altura: 64px normal, 52px com a navbar reduzida, 52/46px no mobile. A largura é automática. Qualquer imagem enviada pelo CMS será exibida nessa altura — daí a instrução de enviar apenas o brasão.

## 12. Pendências e melhorias sugeridas

Em ordem de retorno sobre esforço.

### Alta prioridade

1. **Sitemap não inclui artigos.** É um arquivo fixo com as 5 páginas principais. Artigo novo só é descoberto pelo link da página de artigos. Solução: script de build que varre `artigos/*.md` e regenera o `sitemap.xml` (≈1 hora de trabalho).
2. **A lista de artigos depende da API pública do GitHub.** O `artigos.js` consulta `api.github.com` a cada visita — limite de 60 requisições por hora por IP, e o endereço configurado (`ailtonupe/…`) é o nome **antigo** do repositório, funcionando apenas pelo redirecionamento que o GitHub mantém. Se alguém criar um repositório com o nome antigo, a lista quebra. Solução: gerar um `artigos/index.json` no build (mesmo script do item 1) e ler dele.
3. **Formulário sem proteção anti-spam.** Não há honeypot nem reCAPTCHA. Robôs acham formulários públicos rapidamente.

### Média prioridade

4. **Páginas por área de atuação.** Hoje as seis áreas são cards em uma seção. Uma página própria por área ("Advogado Previdenciário", "Direito Bancário") é a forma clássica de disputar busca fora da cidade — é o item de maior impacto em SEO neste momento.
5. **Imagens sem `loading="lazy"`** em nenhuma página, e o `imagens/logo.png` (802 KB) ficou órfão após a troca da logo — pode ser removido.
6. **Sem página 404 personalizada.** Endereço errado devolve a página padrão da Netlify.
7. **`vercel.json` e `.vercel/`** são resquícios de uma hospedagem anterior. Removê-los evita confusão futura.
8. **Fontes do Google carregadas de servidor externo**, bloqueando a renderização. Servir localmente melhora o tempo de carregamento.

### Baixa prioridade

9. **Editorial workflow do Decap** — hoje o CMS publica direto na `main`, sem revisão. Ativar o modo de rascunho permite escrever sem publicar.
10. **Acessibilidade** — auditar contraste, textos alternativos e navegação por teclado.
11. **Backup do Apps Script do formulário** — não está versionado neste repositório.

## 13. Trabalho já realizado (julho/2026)

- Endereço com "Terceiro Andar" em todas as páginas e nos dados estruturados
- Horário de atendimento: online 24 horas
- Cabeçalho e rodapé com as seis áreas de atuação
- Logo do cabeçalho trocada pelo brasão recortado (sem o texto), de 48px para 64px
- Favicons substituídos (eram uma balança genérica)
- Logo e ícones do CMS passando a valer em **todas** as páginas
- Telefone corrigido para (74) 98856-1132 em todo o site
- Alinhamento do parágrafo das seções corrigido
- SEO: título, descrição, canonical, Open Graph, Twitter Card, `Attorney` nos dados estruturados e `Article` por artigo
- Correção do bug que exibia uma imagem quebrada em artigos sem capa
- Número da OAB uniformizado em **71.102** (o Aviso Legal e a Política de Privacidade traziam 71.020)

---

## 14. Suporte e evolução

Alterações que exigem desenvolvedor — textos fixos, novas seções, páginas por área de atuação, integrações, automações — devem ser solicitadas ao responsável técnico do site.

**Antes de qualquer alteração no código, é obrigatório `git pull`:** o CMS grava direto na `main` e o repositório local fica desatualizado a cada publicação feita pelo Dr. Bruno.
