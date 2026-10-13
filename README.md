# Itens para venda — Dourados/MS (mudança da Tierre)

Tudo deste projeto fica **neste repositório do GitHub** (`tierre-dgenny/itens-dourados`).
Não depende de nenhuma conta do Claude: qualquer pessoa (ou qualquer Claude) com acesso a este repositório consegue continuar.

## Links públicos

| O quê | Link |
|---|---|
| Catálogo (enviar aos compradores) | https://tierre-dgenny.github.io/itens-dourados/ |
| Gerador do termo de compra, venda e entrega | https://tierre-dgenny.github.io/itens-dourados/contrato.html |

O link do catálogo nunca muda. Cada alteração aparece nele em ~1 minuto.

## Arquivos

| Arquivo / pasta | Para que serve |
|---|---|
| `items.json` | **Lista de itens** (nome, descrição, preço, fotos, status). É o único arquivo que precisa mudar no dia a dia. |
| `index.html` | Página do catálogo (visual, cabeçalho, avisos, pagamento, WhatsApp). Lê o `items.json`. |
| `contrato.html` | Gerador do termo. Também lê o `items.json` (foto + descrição entram sozinhas). Botão "Baixar PDF". |
| `images/` | Fotos dos itens (`.jpg`, até ~1000 px). |
| `videos/` | Vídeos dos itens (`.mp4`). |
| `vendor/` | Biblioteca que gera o PDF do termo (html2pdf.js). Não mexer. |

## Formato de um item (`items.json`)

```json
{
  "name": "Cama box casal com baú",
  "note": "Descrição e estado de conservação",
  "photo": "images/cama-casal-1.jpg",
  "photos": ["images/cama-casal-1.jpg", "images/cama-casal-2.jpg"],
  "video": "videos/mesa-jantar.mp4",
  "videoPoster": "images/mesa-jantar-video.jpg",
  "min": 2200,
  "max": 3200,
  "status": "disponivel",
  "reservedFor": "Fernando",
  "queue": ["Fernando", "Thalita e Letícia"]
}
```

- `photo`: foto principal (ou `null`). `photos`: várias fotos (o card vira galeria "deslize"). `video` / `videoPoster`: opcionais.
- `min` e `max`: iguais = **preço fixo**; diferentes = faixa ("R$ min até R$ max").
- `status`: `"disponivel"` | `"reservado"` | `"vendido"`.
  - **reservado** → faixa vermelha "RESERVADO" sobre a foto, sem botão de WhatsApp.
    - `reservedFor`: nome que aparece ("Reservado para …").
    - `queue`: fila de reserva (mostra "Fila de reserva: 1º …, 2º …"; a faixa mostra só "RESERVADO").
  - **vendido** → faixa vermelha "VENDIDO", sem nome, sem botão de WhatsApp.
- A ordem dos itens no arquivo é a ordem no site.

## Regras e textos atuais do site (no cabeçalho do `index.html`)

- Local: Dourados/MS
- Retirada: de 31 de outubro a 20 de novembro de 2026
- Pagamento: Pix ou cartão de crédito (taxas por conta do comprador); aceita 2 cartões ou 2 formas de pagamento
- Frete, retirada e montagem: por conta do comprador
- Aviso azul: reservas valem por até 24h sem sinal/termo assinado
- WhatsApp: (67) 99219-0016 — botões abrem conversa com mensagem pronta com o nome do item

## Como pedir alterações para outro Claude (ou qualquer assistente)

Cole algo assim numa conversa nova:

> Tenho um catálogo de itens à venda no GitHub, repositório `tierre-dgenny/itens-dourados`, publicado em https://tierre-dgenny.github.io/itens-dourados/. Leia o README.md do repositório para entender a estrutura. Os itens ficam em `items.json`. Quero: [sua alteração]. Faça a alteração, faça commit e push na branch `main`.

O assistente precisa ter acesso ao seu GitHub (conectar o GitHub na conta do Claude, ou usar o Claude Code com o repositório).

## Editar sozinha pelo navegador (sem Claude)

1. Entre em https://github.com/tierre-dgenny/itens-dourados e abra `items.json`.
2. Clique no lápis (**Edit**), altere o texto (ex.: troque `"disponivel"` por `"vendido"`), e clique em **Commit changes**.
3. Para foto nova: na pasta `images/`, clique em **Add file → Upload files**, envie o `.jpg`, e depois coloque o caminho (`images/nome.jpg`) no item.
4. Em ~1 minuto o site atualiza.

Cuidado com vírgulas e aspas no `items.json`: se o arquivo ficar inválido, o catálogo mostra "Não foi possível carregar os itens". Basta desfazer a última alteração (aba **History** do arquivo).
