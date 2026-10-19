---
name: repor-estoque
description: Sugere e monta a reposição de estoque na Vend.AI (produtos em falta, fornecedores e pedido de compra em rascunho). Use quando o lojista quiser repor mercadoria.
---

Use as ferramentas do servidor MCP `vendai`:

1. Liste os produtos com estoque baixo ou zerado. Quando o produto tiver variações (cor, tamanho),
   trate cada variação separadamente.
2. Para cada um, descubra o fornecedor e o último custo.
3. Proponha as quantidades e o valor total e **peça a confirmação do lojista** antes de criar
   qualquer coisa.
4. Depois do "sim", crie o pedido de compra como **rascunho**.

Ações que movimentam dinheiro ou estoque (receber compra, ajustar estoque, pagar conta) são críticas:
a primeira chamada só devolve uma prévia e um `confirm_token`. Mostre a prévia ao lojista e só
repita a chamada com o token depois da confirmação dele.
