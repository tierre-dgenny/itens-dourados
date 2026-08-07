# Itens para venda — Dourados/MS

Catálogo simples (uma página HTML) com fotos e preços dos itens à venda.
Publicado via **GitHub Pages** para funcionar como um link único, atualizável, que pode ser enviado para compradores interessados.

## Como atualizar

1. Abra o arquivo `index.html`.
2. Procure o bloco `const items = [ ... ]` perto do fim do arquivo.
3. Cada item é um objeto assim:

```js
{
  name: "Nome do item",
  note: "Descrição / estado de conservação",
  photo: "images/arquivo.jpg",   // ou null se não tiver foto ainda
  min: 250, max: 450,            // faixa de preço em reais
  status: "disponivel"           // "disponivel" | "reservado" | "vendido"
}
```

- Para marcar um item como vendido, troque `status: "disponivel"` para `status: "vendido"`.
- Para adicionar uma foto nova, coloque o arquivo `.jpg` dentro da pasta `images/` e referencie o caminho em `photo`.
- Para adicionar um item novo, copie um bloco `{ ... }` e cole antes do `];`, com uma vírgula separando do anterior.

Depois de editar, salve, faça commit e envie (`git add .`, `git commit -m "atualiza catálogo"`, `git push`) — a página publicada atualiza sozinha em 1–2 minutos.

## Como publicar pela primeira vez (GitHub Pages)

1. Crie um repositório novo no GitHub (pode ser privado ou público).
2. Suba os arquivos desta pasta (`index.html`, `README.md`, pasta `images/`) para o repositório.
3. No repositório, vá em **Settings → Pages**.
4. Em "Source", selecione a branch `main` e a pasta `/ (root)`, depois clique em **Save**.
5. Em alguns minutos o GitHub mostra o link público, algo como:
   `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`
6. Esse é o link que você envia para os compradores — ele sempre mostra a versão mais recente.

## Editar direto pelo navegador (sem instalar nada)

Dá pra editar o `index.html` direto na página do GitHub: abra o arquivo no repositório, clique no ícone de lápis (Edit), altere o texto dentro de `items`, e clique em **Commit changes**. A página publicada atualiza sozinha.
