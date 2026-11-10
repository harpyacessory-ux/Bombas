# LP Bombas Industriais — Vazão Engenharia

Landing page da campanha **Bombas Industriais** (Google Ads) da **Vazão Engenharia e Montagem**. Reúne os 4 grupos da campanha numa página só: **Kronox**, **ARO**, **Higra** e **Locação de Bombas**.
Palavra-chave principal: **bombas industriais** (no H1 e no título da aba). Cada prateleira repete o termo do seu grupo no título.

## Estrutura

- `index.html`: página única e autocontida (HTML, CSS e JS inline). Fonte: Plus Jakarta Sans. Identidade visual igual à da LP NR13 e do site da Vazão (marinho `#0b3f8a`, azul `#2468cc`, vermelho `#e1062f`).
- `assets/`: imagens. As fotos e logos abaixo entram **sozinhas** na página quando o arquivo é salvo com o nome exato (vale `.webp`, `.jpg` ou `.png`). Até lá, aparece um ícone no lugar.

### Blocos

1. Topo com menu e botão "Solicitar orçamento"
2. Hero: H1 "Bombas industriais Kronox, ARO e Higra", chat de atendimento, pontos Engenharia · PE e CE · Desde 1991
3. Marcas (Kronox, ARO, Higra, Locação) + selos: Atendimento PE e CE · Engenharia especializada · Equipe técnica
4. Vitrine com 4 prateleiras e 15 itens: Kronox (6), ARO (2 + comparativo pneumática × elétrica), Higra (3), Locação (4)
5. Como funciona a locação (6 etapas, sem prazos) + quando optar pela locação
6. Aplicações: captação, elevatória de esgoto, drenagem (compra **e** locação), ETE + mineração (locação)
7. Diferenciais (5)
8. Perguntas frequentes (8, separadas em Locação e Produtos)
9. Frase de autoridade "Não escolha a bomba pelo tamanho." + formulário de orçamento com os 6 dados que o cliente pode enviar
10. Rodapé

### Imagens pendentes

**Logos das marcas** (400×160, fundo transparente) em `assets/marcas/`:

| Arquivo | Observação |
|---|---|
| `kronox.png` | enviada pelo usuário; recortar sem o fundo branco |
| `aro.png` | enviada; baixa resolução |
| `higra.png` | enviada como JPG quadrado; exportar horizontal |

**Fotos de produto** (800×600, de preferência fundo transparente) em `assets/produtos/`. As 9 primeiras existem no site da Vazão. O site bloqueia download automático (Cloudflare), então precisam ser salvas pelo navegador:

| Arquivo | Origem em vazao.com.br/wp-content/uploads/ |
|---|---|
| `kronox-baby-booster.jpg` | `2025/03/BABY-BOOSTER.jpg` |
| `kronox-booster-w.jpg` | `2025/03/BOOSTER-W.jpg` |
| `kronox-booster-z.png` | `2025/03/Design-sem-nome-93.png` |
| `kronox-booster-x.png` | `2025/03/Design-sem-nome-96.png` |
| `kronox-elevatoria-plug-e-play.png` | `2023/07/toraqua.png` |
| `aro-diafragma-pneumatica.jpg` | `2023/07/bomba-aro.jpg` |
| `aro-serie-evo.jpg` | `2023/07/bomba-serie-evo.jpg` |
| `higra-bombas-anfibias.jpg` | `2023/07/PHOTO-2022-11-25-14-56-544.jpg` (foto de galpão) |
| `higra-aeradores.jpg` | `2023/07/aeradores-higra.jpg` (foto de galpão) |
| `kronox-elevatoria-4-0` | **ausente** |
| `higra-bombas-submersas` | **ausente** |

**Locação** (1200×900, foto de campo **sem marca em destaque**) em `assets/locacao/`: `bombas-para-mineracao`, `bombas-de-drenagem`, `bombas-de-incendio`, `sistemas-de-bombeamento`.

**Aplicações** (1200×900, equipamento operando) em `assets/aplicacoes/`: `captacao-de-agua-bruta`, `estacao-elevatoria-de-esgoto`, `drenagem-industrial`, `tratamento-de-efluentes-ete`, `mineracao`.

**Banner do hero**: `assets/banner-topo.jpg` (incluído). É a arte enviada pelo usuário com as bombas reduzidas e o fundo estendido para cima e para a direita, para o chat ficar sobre a parte escura sem cobrir as bombas. No celular, a arte aparece como um recorte das bombas entre o texto e o chat.

## Configuração (bloco `CONFIG` no fim do `index.html`)

- `gtmId`: ID do Google Tag Manager. Vazio = não carrega.
- `leadEndpoint`: URL que recebe o lead (POST JSON). **Enquanto estiver vazio, o lead segue pelo WhatsApp da campanha (81) 99203-9379**, já com os dados preenchidos.
- `privacyUrl`: link da política de privacidade.

O lead leva campanha, grupo (do parâmetro `adgroup` da URL; se não houver, deduzido do produto escolhido), palavra-chave (`keyword`/`utm_term`), anúncio (`creative`/`utm_content`), UTMs e `gclid`, guardados por 90 dias.
Eventos no `dataLayer`: `cta_click` (com o produto clicado), `chat_start`, `generate_lead`.
Os botões "Solicitar orçamento" da vitrine já preenchem o produto e marcam Compra ou Locação no formulário.

## Regras de conteúdo aplicadas

- Locação **sem marca e sem modelo**, e **sem prazo mínimo** de locação
- "Representante" só aparece na prateleira Higra ("Representante Higra no Nordeste"). "Distribuidor" e "revenda" não aparecem
- Nenhum nome de concorrente, nenhum cliente citado
- "Peças nacionais" virou "Componentes nacionais" (Kronox)
- Drenagem separada entre comprar (Higra) e alugar (Locação)

## Pendências

- [ ] Imagens e logos listados acima
- [ ] URL final da LP (hoje `https://vazao.b2marketingindustrial.com.br/bombas-industriais/` no canonical, robots e sitemap)
- [ ] Link da política de privacidade e `leadEndpoint`/GTM
- [ ] Endereço: o briefing traz "Brasilit"; a LP NR13 usa "Várzea" para o mesmo CEP. Confirmar com o cliente
- [ ] Perguntas frequentes: validar com o comercial
- [ ] Negativas do grupo Kronox: lista vazia no briefing (pendência da mídia)
- [ ] "bomba de incêndio" (genérica) atrai também quem quer **comprar**; a página só aluga
- [ ] O Grupo 3 (Higra) hoje aponta para `/product-category/aro/`

## Rodar localmente

```bash
python3 -m http.server 8000   # http://localhost:8000
```

## Deploy

Vercel, conectada a este repositório: todo push na `main` publica em produção.
