---
name: usar-o-vendai
description: Guia geral da loja Vend.AI: o que a IA consegue fazer, por onde começar e como as ações críticas funcionam. Use quando o lojista perguntar o que dá para fazer ou não souber por onde começar.
---

Você está conectado à loja do lojista pelo servidor MCP `vendai`, com as permissões do usuário dele.

## O que dá para fazer

| Área | Skill |
|---|---|
| Resumo e números do negócio | `relatorios`, `fechamento-do-dia` |
| Estoque e reposição | `consultar-estoque`, `repor-estoque` |
| Cadastro de produtos e preços | `gerenciar-produtos` |
| Pedidos | `pedidos` |
| Clientes e fidelidade | `clientes-e-fidelidade` |
| Fornecedores e pedidos de compra | `compras-e-fornecedores` |
| Contas a pagar e a receber | `financeiro`, `contas-vencidas` |
| Entregas e entregadores | `entregas` |
| Caixa e notas fiscais (consulta) | `caixa-e-fiscal` |
| Campanhas e cupons | `campanhas-e-cupons` |
| Atendimento no WhatsApp | `atendimento-whatsapp` |
| Rotinas agendadas | `automacoes` |
| Horário, entrega, pagamentos e política | `informacoes-da-loja` |

## O que a IA NÃO faz por aqui

Disparar campanha, emitir ou cancelar nota fiscal, vender no caixa (PDV) e administrar usuários,
papéis, chaves ou assinatura. Isso continua só no painel.

## Acesso da conexão

O lojista escolhe ao conectar: **somente consulta** (padrão), **consulta e cadastros** ou **operação
completa**. A IA nunca pode mais do que o próprio usuário pode.

Atalhos do servidor (prompts): `fechamento_do_dia`, `repor_estoque`, `contas_vencidas`,
`resumo_da_semana`, `conferir_entregas`. Recursos: `vendai://dashboard`, `vendai://catalogo`,
`vendai://estoque-baixo`, `vendai://contas-vencidas`.
