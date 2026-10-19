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

- A conexão com o servidor MCP da Vend.AI.
- Atalhos (skills) em português: `fechamento-do-dia`, `repor-estoque` e `contas-vencidas`.

## Licença

[MIT](LICENSE) © Aura Build Ltda. O serviço Vend.AI em si é um produto à parte, com termos próprios.
