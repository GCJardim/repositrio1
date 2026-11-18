# ADESAI2.0 — GUIA DE CONTINUIDADE

**Última consolidação:** 18/11/2026 após **5 entregas documentadas**.

## COMO RECOMEÇAR EM OUTRO CHAT
1. Ler `README.md`, `HISTORICO.md` e `STATUS_ATUAL.md` neste repositório.
2. Consultar o deployment atual da Vercel antes de qualquer edição: **não usar uma versão desatualizada**.
3. Escutar a nova solicitação e modificar somente a área pedida.
4. Testar o build e publicar em preview; após verificar, publicar produção e checar os domínios ativos.
5. Atualizar `HISTORICO.md` com escopo, testes, implantação e limitações.
6. A cada cinco novas entregas, consolidar novamente STATUS_ATUAL.md e CONTINUIDADE.md.

## IDENTIFICADORES
- Vercel projeto: `adesai2-0`, ID `prj_kNnDldgjmDxXe22te7I3ecQjWfsN`, URL https://adesai2-0.vercel.app/
- Último deploy 18/11/2026: `dpl_5cwuJwBuA9taSuKXSbCw9RxpNjeA`.
- Deploy anterior: `dpl_2QRiA4xPEgM8LizbeCS3BVLkAcyZ`.
- Banco Supabase identificado: projeto `ADESAI2.0`, mas conexão com a aplicação online não foi validada.
- GitHub da documentação: `GCJardim/repositrio1` (repositório público, não assumir que contém o código completo).

## ARQUITETURA OBSERVADA
- HTML estático monolítico com estilos, scripts e imagens incorporadas; navegação dinâmica baseada em `MENU`, `MENU_ICON`, `ui.page`, `render()`.
- A implantação atual usa `build.js` e `package.json` que reconstroem HTML a partir de deploy anterior imutável mais patch verificado por hash. **Nunca substituir diretamente por arquivos parciais.**
- Ações de sidebar usam estilos `sidebar-adesai-modern` e script `sidebar-adesai-behavior`.
- Foto impressa separada de campos por `pf-first-fields`, com estilos `adesai-print-photo-fix`.
- Editor Nova ficha corrigido pelo estilo `adesai-ficha-layout-fix`.
- Botão móvel oculto na impressão por `adesai-print-hide-navigation`.
- Paginação mais compacta por `adesai-print-compact-pages` (permite quebrar blocos longos, mas mantém campos inteiros).
- Impressão de seções condicionais: `group(title,cells)` agora devolve vazio se nenhum campo possui informação, mas mantém Dados do Aluno; respostas Não/0 contam como informação.
- Aba `Cursos` adicionada à ficha digital (após Projeto e turma), com campos `d_curso` e `d_observacoesCurso`; a rotina de salvamento genérica de `d_*` registra os valores em `details`, usados na impressão. Estilos `adesai-course-tab-styles`.

## DECISÕES QUE DEVEM SER PRESERVADAS
- Layout institucional ADESAI (logo azul/amarelo).
- Ficha aprovada provisoriamente; alterações pontuais, sem refazer telas.
- Enter NÃO salva ficha; apenas avança entre campos. Botão Salvar realiza o salvamento.
- Formulário deve conter campos da ficha impressa, incluindo cútis.
- Impressão da ficha: foto alinhada, linhas sem sobreposição, sem botão flutuante, cabeçalhos e compactação.
- Relatório e relação: cabeçalho institucional e impressão vertical conforme requisitos.
- Solicitação de controle de reembolsos mensais (verificar implementação).

## CUIDADOS
- Não publicar dados pessoais nem chaves de acesso em GitHub público.
- Não presumir persistência em Supabase sem testar.
- Distinguir "solicitado", "editado", "publicado" e "testado". Atualmente há validação técnica da publicação, mas teste visual de impressão ainda pendente.
- Os CSS de impressão devem ser restritos à ficha, para não modificar termos, relatórios e reembolsos.
- Evitar informar economia exata de folhas sem verificar paginação real.

## CONTAGEM
- Primeiro ciclo concluído: **5 de 5** atualizações documentadas.
- Novo ciclo em andamento: **2 de 5**.
