# ADESAI2.0 — STATUS ATUAL CONSOLIDADO

**Consolidação:** 18/11/2026 — primeiro ciclo de 5 entregas documentadas.
**Aplicativo:** https://adesai2-0.vercel.app/
**Vercel:** projeto `adesai2-0`, ID `prj_kNnDldgjmDxXe22te7I3ecQjWfsN`.
**Último deploy de produção verificado:** `dpl_9nytGdvDGyCz5Qg4HaDuYrZibhqR` (READY).
**SHA-256 do HTML:** `8f71a4a227d66549acea509f1fabb7d3bc9e01661e7e1f41a5b84812f80dba6e`.

## Entregas do primeiro ciclo
1. **Menu lateral modernizado:** grupos, modo recolhido, menu móvel e página ativa destacada.
2. **Foto da ficha na impressão:** área de foto em coluna independente, impedindo linhas de campos sobrepostas.
3. **Editor Nova ficha cadastral:** alinhamento conforme menu recolhido/aberto, abas responsivas, ações ao final do formulário sem flutuar sobre campos.
4. **Menu móvel oculto na impressão:** regra `adesai-print-hide-navigation` em `@media print`.
5. **Impressão compacta:** `adesai-print-compact-pages` permite separar seções longas entre páginas e compacta espaçamentos, reduzindo áreas vazias.

## Testes realizados e limites
- Validação sintática de scripts, reprodução integral do HTML, checagem por hashes e respostas HTTP 200 em preview/produção.
- As alterações foram publicadas e verificadas tecnicamente.
- **Ainda não foi executado teste visual automatizado em navegador da paginação ou confirmação de impressão física.** Não afirmar quantidade definitiva de páginas economizadas antes disso.
- O site apresentou indicador de ambiente demonstrativo com dados fictícios. **Não considerar persistência Supabase confirmada só por existir o projeto do banco.**
- O aplicativo é HTML monolítico com CSS, JS e imagens embutidas. O GitHub `GCJardim/repositrio1` contém inicialmente documentação e NÃO foi verificado como repositório de origem da Vercel.

## Cuidados e decisões que devem permanecer
- Preservar visual institucional azul/amarelo e a logo.
- Na ficha, Enter avança ao próximo campo sem salvar; salvar apenas no botão.
- Campo cútis e outros campos impressos devem existir também no formulário.
- Preservar campos e regras fora do escopo de cada alteração.
- Na impressão manter cabeçalho, foto sem sobreposição, não imprimir botões, evitar folhas com muito espaço vazio.
- Não publicar dados reais de jovens, documentos ou credenciais no GitHub público.

## Pendências anteriormente solicitadas (validar antes de assumir concluídas)
- Relatórios com cabeçalho ADESAI, impressão A4 retrato.
- Relação de participantes com cabeçalho institucional.
- Reembolsos mensais e seus detalhes.
- Integração real do Supabase e permissões.

## Próximos passos
1. Conferir visualmente impressão das fichas em diferentes tamanhos (incluindo seção longa e foto).
2. Continuar conforme próxima solicitação.
3. Ao concluir uma nova tarefa, atualizar HISTORICO.md e contar novo ciclo.

**Ciclo anterior: 5/5 documentadas. Próximo ciclo: 0/5.**
