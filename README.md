# Vend.AI para IAs (MCP)

Use a sua loja [Vend.AI](https://github.com/Aura-Build-Ltda) dentro do Claude, Claude Code, Codex,
ChatGPT, Cursor e outras IAs: consulte vendas, estoque e finanças, monte pedidos de compra, receba
mercadoria e confira entregas conversando. É o mesmo conjunto de capacidades do assistente do painel,
sob as **permissões do seu próprio usuário**.

Este repositório traz o plugin (Claude Code e Codex) e o passo a passo dos demais aplicativos. O
servidor é o MCP remoto da Vend.AI: você precisa de uma conta com o plano que inclui conexão de IA.

## Instalar

### Claude Code

```bash
claude plugin marketplace add Aura-Build-Ltda/vendai-mcp
claude plugin install vendai@vendai
```

O Claude Code pergunta o **endereço do servidor** (copie em *Configurações → Conectar sua IA* no
painel). Depois, dentro do Claude Code, rode `/mcp`, escolha `vendai` e entre com o seu login.

### Codex

```bash
codex plugin marketplace add Aura-Build-Ltda/vendai-mcp
```

Reinicie o aplicativo, abra o diretório de plugins, instale **Vend.AI** e entre com o seu login.

### ChatGPT e Claude.ai (versão web)

Ainda não estão no diretório oficial: adicione como conector personalizado.

- **Claude.ai:** Configurações → Conectores → Adicionar conector personalizado → cole o endereço do servidor.
- **ChatGPT:** Configurações → Conectores (modo desenvolvedor) → Criar → cole o endereço do servidor.

Uma janela do Vend.AI abre: entre, escolha o que a IA pode fazer e clique em **Autorizar**.

### Cursor, VS Code, Windsurf, Gemini CLI e outros

Em *Configurações → Conectar sua IA* no painel, cada aplicativo tem o trecho pronto (ou o botão de
1 clique). Qualquer cliente MCP que fale HTTP com OAuth 2.1 também serve.

## Segurança

O servidor trata a IA conectada como **não confiável** (ela lê textos que a loja não controla, como
nome de cliente e observação de pedido):

- **Acesso por perfil**, escolhido por você ao autorizar: somente consulta (padrão), consulta e
  cadastros, ou operação completa. A IA nunca pode mais do que você pode.
- **Ações críticas em 2 etapas**: baixar conta, receber compra, ajustar estoque, mudar preço ou
  cancelar só executam depois de uma prévia e de um `confirm_token` de uso único.
- **OAuth 2.1 com PKCE**, token de acesso de 1 hora e renovação com rotação.
- **Trilha de tudo o que a IA fez**, visível no painel, e revogação da conexão num clique.
- A IA conectada **não** dispara campanhas, não emite nota fiscal, não vende no caixa e não
  administra usuários, papéis ou assinatura.

Encontrou uma falha de segurança? Veja [SECURITY.md](SECURITY.md).

## O que o plugin traz

Além da conexão com o servidor MCP (que entrega as 88 ferramentas conforme o acesso da sua conexão),
o plugin traz **17 skills** em português, uma por área, que ensinam a IA a usar as ferramentas
certas, na ordem certa e com as regras de segurança:

| Skill | Cobre |
|---|---|
| `usar-o-vendai` | Mapa geral, o que a IA não faz e como funciona o acesso |
| `relatorios`, `fechamento-do-dia` | KPIs, vendas, mais vendidos, horários de pico, fluxo de caixa, resumo do dia |
| `consultar-estoque`, `repor-estoque` | Estoque, variações, produtos parados, reposição com o melhor fornecedor |
| `gerenciar-produtos` | Produtos, categorias, variações, preço e ajuste de estoque |
| `pedidos` | Fila, detalhe, criar, alterar, mudar status e cancelar |
| `clientes-e-fidelidade` | Clientes, endereços, segmentos, pontos, ranking e recompensas |
| `compras-e-fornecedores` | Fornecedores, custo por fornecedor, pedidos de compra e recebimento |
| `financeiro`, `contas-vencidas` | Contas a pagar e a receber, fluxo de caixa, aging, baixa e cancelamento |
| `entregas` | Entregas, entregadores, zonas e taxas |
| `caixa-e-fiscal` | Sessões de caixa e notas fiscais (só consulta) |
| `campanhas-e-cupons` | Cupons, rascunho e custo de campanhas (o disparo é no painel) |
| `atendimento-whatsapp` | Fila de conversas, resumo e transferência para humano |
| `automacoes` | Rotinas agendadas |
| `informacoes-da-loja` | Horário, taxa de entrega, pagamentos, adicionais e política de troca |

No Claude Code elas aparecem como `/vendai:<skill>`. Três ferramentas do servidor
(`build_order`, `request_info` e `guardrail_stats`) servem ao bot de WhatsApp da própria loja e não
têm skill aqui.

O servidor também oferece os atalhos (prompts) `fechamento_do_dia`, `repor_estoque`,
`contas_vencidas`, `resumo_da_semana` e `conferir_entregas`, e os recursos `vendai://dashboard`,
`vendai://catalogo`, `vendai://estoque-baixo` e `vendai://contas-vencidas`.

## Licença

[MIT](LICENSE) © Aura Build Ltda. O serviço Vend.AI em si é um produto à parte, com termos próprios.
