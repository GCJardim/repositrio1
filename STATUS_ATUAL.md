# ADESAI2.0 — Estado atual

**Atualizado em:** 18/11/2026
**URL principal:** https://adesai2-0.vercel.app/
**Vercel:** projeto `adesai2-0`, ID `prj_kNnDldgjmDxXe22te7I3ecQjWfsN`.
**Publicação verificada:** `dpl_4iJNc3XEsFH1HYquqtZqWVXJfbt1` — estado READY.

## O que foi confirmado
- Na impressão da ficha o botão móvel “☰ Menu” e a sobreposição do menu estão ocultos por `@media print` no CSS `adesai-print-hide-navigation`. A publicação foi confirmada; a prévia visual de impressão ainda não foi reavaliada no navegador.
- Página estática principal em HTML foi recuperada do ambiente publicado.
- Nova barra lateral agrupada e responsiva publicada em produção em 18/11/2026.
- Arquivo HTML respondeu HTTP 200 nos dois domínios e manteve conteúdo esperado e hash de integridade.
- Código JavaScript validado sintaticamente.
- Editor da nova ficha cadastral: recuo da sidebar recolhida/expandida corrigido; ações integradas no final do formulário; abas e grid responsivos. Publicado e verificado por HTTP e hash, teste visual interativo pendente.
- Ficha impressa: foto colocada em coluna independente de seus campos, sem linhas compartilhadas. Preview e produção com integridade de HTML confirmada. Impressão física ainda não reavaliada após alteração.

## Estrutura identificada
- Na versão inspecionada o aplicativo usa um único arquivo HTML grande, com CSS, scripts e imagens incorporadas.
- Sidebar `<aside id="sidebar">`, navegação `<nav id="navigation">`.
- Renderização dinâmica da navegação usa `MENU`, `MENU_ICON`, `ui.page`, `render()`.
- Rotas identificadas: `dashboard`, `participants`, `fichas`, `turmas`, `chamada`, `empresas`, `faltas`, `justificativas`, `relatorios`, `autorizacoes`, `admin`.
- Na interface recuperada havia aviso de demonstração e dados fictícios. A existência de aba do Supabase no navegador não comprova conexão da versão online a um banco; conferir antes de considerar persistência real.

## Requisitos aprovados ou pedidos anteriormente (não revalidados nesta entrega)
- Ficha: preservar layout, enquadramento da foto, campo cútis e outros campos da ficha impressa, Enter não deve salvar, salvar pelo botão.
- Relatórios: cabeçalho institucional, logo, impressão A4 vertical, mantendo layout.
- Relações: cabeçalho institucional ao imprimir.
- Reembolsos: aba para lançamentos mensais, campos e cálculos a confirmar.

## Observações de continuidade
- O GitHub `GCJardim/repositrio1` foi usado inicialmente para **documentação**, não foi confirmado como fonte de código da Vercel.
- A Vercel está com deploy baseado em `build.js` e `package.json` para reconstruir a página a partir de um deploy base imutável com patch. **Não substituir a aplicação pelo HTML incompleto nem presumir que este repositório já contém o código integral**.
- Ao modificar o produto, leia `CONTINUIDADE.md` e o histórico antes de alterar.
- Não publicar dados pessoais ou segredos em arquivos públicos.

## Prioridade
1. Confirmar a navegação visual em computador e celular e qualquer feedback da usuária.
2. Retomar melhorias dos relatórios e da relação apenas mediante nova solicitação.
3. Implementar/ajustar reembolsos conforme escopo solicitado.
4. Registrar cada mudança testada no HISTORICO.md.

**Contador:** 4 / 5 entregas verificadas.
