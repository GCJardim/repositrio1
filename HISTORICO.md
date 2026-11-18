# Histórico de entregas — ADESAI2.0

## 18/11/2026 — Entrega 1: barra lateral modernizada (confirmada)

**Solicitação:** melhorar a usabilidade, aparência, organização e acessibilidade da barra lateral sem modificar as demais telas.

**Mudanças feitas:**
- Navegação agrupada em Principal, Cadastros, Gestão e Frequência, Administrativo.
- Grupos expansíveis/recolhíveis, preservando as rotas existentes.
- Botão para recolher e expandir a sidebar no desktop.
- Layout responsivo com botão de abertura, sobreposição e fechamento no celular.
- Estado ativo destacado em amarelo institucional.
- Maior largura, legibilidade e espaçamento, mantendo identidade ADESAI.

**Testes realizados:**
- JavaScript validado com `node --check`.
- Geração do HTML completo conferida por hash SHA-256.
- Prévia Vercel retornou HTTP 200 com HTML atualizado.
- Os dois domínios públicos de produção retornaram HTTP 200 com mesmo hash.

**Não verificado:** testes de clique com navegador automatizado e uso de todas as funcionalidades internas. Nenhuma regra de dados, fichas, relatórios ou Supabase foi intencionalmente alterada.

**Vercel:** projeto `adesai2-0`, ID `prj_kNnDldgjmDxXe22te7I3ecQjWfsN`; deploy de produção `dpl_27auN7ZW8si9GDVtaFRraHCAfFkL`; deploy de prévia `dpl_82XB7QiMvymPySC1ktYwDEdybzF3`; URL https://adesai2-0.vercel.app/

**Integridade da página publicada:** SHA-256 `ee4b57e20001c841a153dadaaa5db41b436559f300072f43ae3a3cbeac3e1fa7`.

## 18/11/2026 — Entrega 2: foto sem linhas sobrepostas na impressão da ficha (publicada)

**Problema observado:** na folha impressa, a fotografia ficava atravessada por linhas de campos e desalinhada dentro de "Dados do Aluno".

**Causa técnica:** a foto era inserida antes da grade de campos e posicionada com `position:absolute`, enquanto a grade usava apenas `padding-right` para reservar espaço, permitindo interferência visual das linhas.

**Correção pontual:** apenas na ficha impressa, os campos de "Dados do Aluno" passaram a ficar dentro de `pf-first-fields`, e a fotografia foi colocada como segunda coluna própria da grade. O CSS `adesai-print-photo-fix` posiciona e enquadra a foto com fundo branco, `overflow:hidden` e `object-fit:cover`. Demais seções, fichas digitais, cadastro, relatórios e Supabase não tiveram regras alteradas.

**Validação:** `node --check` passou nos scripts; comparação binária confirmou o HTML esperado; preview e os dois domínios de produção retornaram HTTP 200 com SHA-256 `fc061edf0782dcf1f7af1d78aa5024ead0c33d5b64f86c67614dc21c48a27117`. **Pendente:** teste visual do papel após impressão real pela instituição (não foi possível imprimir fisicamente).

**Deploy preview:** `dpl_9JsEccFm8fZKETuNQPck44TbWuKg`.
**Deploy produção:** `dpl_6VJ2yx9udfWMJ2j9oV59ZLEPeics`.
**URL:** https://adesai2-0.vercel.app/

## 18/11/2026 — Entrega 3: alinhamento da tela Nova ficha cadastral (publicada)

**Problema identificado na imagem enviada:** a nova ficha aparecia deslocada à direita quando a barra lateral era recolhida, e a barra de ações (Salvar ficha, Limpar empresa, Mover para Preparatório, Cancelar) flutuava sobre o conteúdo. As sete abas ocupavam linhas desiguais.

**Causa:** o editor continuava com recuo lateral fixo independente do estado da sidebar; a barra `ficha-footer` tinha `position:sticky`; as abas eram limitadas a seis colunas mesmo havendo sete seções.

**Alteração:** adicionado o CSS isolado `adesai-ficha-layout-fix` no HTML. Recuo do editor ajustado para sidebar expandida (282px), recolhida (78px) e celular (0). Barra de ações transformada em rodapé normal do formulário, sem sobreposição; abas reorganizadas em grade responsiva com 7/4/3/2 colunas conforme largura; grid de conteúdo e histórico adaptados a telas menores. Os controles e a lógica de salvamento não foram modificados.

**Verificação:** integridade do HTML validada na geração, scripts passaram em `node --check`, preview e dois endereços de produção responderam HTTP 200 com SHA-256 `cc4ced9946438801ac9d605e8c1f8df831e090b3d95c4139bb59a9bc45f4c86a`. **Pendente:** confirmação visual por uso do navegador na tela real.

**Deploy de prévia:** `dpl_Eunw2mf4sj4P1R44o8YCwFBKMeYf`.
**Deploy de produção:** `dpl_jcMuX1jHh4oaPJjjSxL6SMDhRXSi`.
**URL:** https://adesai2-0.vercel.app/

## 18/11/2026 — Entrega 4: ocultação do botão Menu na impressão (publicada)

**Relato:** o botão flutuante "☰ Menu" aparecia no canto inferior esquerdo da visualização de impressão da ficha de aluno.

**Correção pontual:** inclusão do bloco CSS `adesai-print-hide-navigation` com `@media print`, ocultando `.mobile-menu-button`, `#mobileMenuButton`, `.sidebar-overlay` e `#sidebarOverlay`. O menu continua disponível na navegação normal. Nenhum campo da ficha, cabeçalho, foto, lógica de cadastro ou banco de dados foi alterado.

**Testes efetuados:** scripts passaram em `node --check`; versão gerada comparada com o resultado esperado; prévia e os dois endereços de produção responderam HTTP 200 com o HTML atualizado e SHA-256 `53ca1b1e862034a7f46a0a6a800cb61f4159eaef71ebaf2c5ed79fbc7bd2c44f`. A visualização de impressão no navegador ainda não foi testada interativamente.

**Prévia:** `dpl_F1fz8icmxRbmZMDmNSNhTRJSDADn` — **Produção:** `dpl_4iJNc3XEsFH1HYquqtZqWVXJfbt1`.
**URL:** https://adesai2-0.vercel.app/

## 18/11/2026 — Entrega 5: impressão mais compacta, com menos espaços em branco (publicada)

**Problema:** uma seção grande da ficha era empurrada para a folha seguinte, deixando grande área vazia na página anterior.

**Causa identificada:** o CSS de impressão marcava todos os blocos `.pf-group` com `break-inside:avoid` e `page-break-inside:avoid`, além de `overflow:hidden`, impedindo que seções extensas fossem divididas.

**Alteração pontual:** criado o estilo `adesai-print-compact-pages`, que autoriza a divisão de seções longas entre páginas, mantém cabeçalhos junto ao conteúdo quando possível, evita divisão de campos individuais e reduz discretamente margens, lacunas e alturas de campos. Mantém `pf-first` intacta para preservar a fotografia, mantém layout da tela e termos de assinatura com regras próprias.

**Testes:** HTML completo gerado e comparado; scripts verificados com `node --check`; ambiente preview e os dois domínios de produção retornaram HTTP 200 com SHA-256 `8f71a4a227d66549acea509f1fabb7d3bc9e01661e7e1f41a5b84812f80dba6e`. **Pendente:** conferir no navegador a paginação visual e o número exato de folhas (dependem dos dados preenchidos e das configurações de impressão).

**Preview:** `dpl_8Hggz8PUAGUwEhq7dRdnivApR5SE`.
**Produção:** `dpl_9nytGdvDGyCz5Qg4HaDuYrZibhqR`.
**URL:** https://adesai2-0.vercel.app/

## 18/11/2026 — Entrega 6: aba Cursos na ficha cadastral (publicada)

**Problema:** seção "Cursos" aparecia no documento impresso, mas os campos `d.curso` e `d.observacoesCurso` não tinham controles correspondentes na ficha digital; o usuário não conseguia preenchê-los.

**Correção:** aba claramente identificada como **Cursos**, após "Projeto e turma", com campo multilinha "Cursos realizados ou em andamento" (um por linha) e "Observações sobre os cursos". Os campos têm nomes `d_curso` e `d_observacoesCurso`, capturados pelo salvamento genérico de `[name^=d_]` já existente; os valores alimentam a seção Cursos da ficha impressa. Estilo responsivo `adesai-course-tab-styles` organiza 8 abas em quatro colunas (duas no celular).

**Teste:** `node --check` de scripts, verificações de presença do formulário, capturador de salvamento e seção de impressão, reconstrução fiel de HTML, preview e dois domínios de produção respondendo HTTP 200 com SHA-256 `1dd1383a15776a8ed1b0b34b24b0663a27807260f5f5136b0c532c93b3bccae3`.

**Limitação:** salvamento em navegador e resultado de impressão não foram exercitados visualmente de ponta a ponta. Persistência real no Supabase continua não comprovada.

**Deploy preview:** `dpl_6JsUpeUBydwoCHYVc7GodtoJZT6B`.
**Deploy produção:** `dpl_2QRiA4xPEgM8LizbeCS3BVLkAcyZ`.
**URL:** https://adesai2-0.vercel.app/

**Novo ciclo de entregas:** 1/5.

## 18/11/2026 — Entrega 7: omitir seções vazias na impressão da ficha (publicada)

**Pedido:** quando uma área inteira da ficha estiver sem informações, não imprimir essa seção. Exemplo: participante sem curso não deve gerar o bloco "Cursos".

**Implementação:** a função `group(title,cells)` da impressão da ficha verifica se pelo menos um campo possui valor não vazio antes de renderizar a seção. Campos sem valor ou somente espaços/`&nbsp;` não mantêm um bloco vazio. Respostas explícitas "Não", "Sim" ou "0" contam como preenchidas. O cabeçalho e os Dados do Aluno permanecem preservados mesmo em fichas incompletas. Vale para seções como Cursos, Documentação, Contato, Benefícios e demais grupos criados por `group()`. O formulário digital e seus dados não foram alterados.

**Verificações:** execução de casos de teste (seção sem cursos omitida; com curso incluída; "Não" e "0" mantidos), `node --check` nos scripts, reconstrução integral por hash e publicação HTTP 200 nos dois domínios. A conferência visual no navegador com fichas reais continua pendente.

**Deploy de prévia:** `dpl_73bEBQkvV62ru54nCJs2B8epuZya`.
**Deploy de produção:** `dpl_5cwuJwBuA9taSuKXSbCw9RxpNjeA`.
**Hash HTML publicado:** `30a885d687b578434ea838637f6441df069263d36396a4939cde4f488f76d741`.
**URL:** https://adesai2-0.vercel.app/

**Segundo ciclo:** 2 de 5 entregas.

## 18/11/2026 — Entrega 8: imprimir somente o relatório analítico, usando largura útil do A4 (publicada)

**Pedido:** ao imprimir o Relatório Analítico de faltas, ocultar as abas superiores ("Relatórios e descontos" e "Reembolsos por mês") e ampliar o relatório para aproveitar a folha A4 vertical.

**Causa:** botão `#printReport` imprimia a página inteira (`window.print()`) e, por isso, elementos do módulo apareciam na visualização de impressão.

**Correção:** botão agora cria uma cópia temporária exclusivamente do conteúdo `#reportContent` em `#adesaiReportPrintSheet`, fora dos painéis e abas da interface, adiciona regra A4 retrato com margem de 10 mm e aciona a impressão. CSS isolado `adesai-report-print-only` oculta todo o restante da página enquanto a cópia é impressa e amplia relatório, tabela e cabeçalho para 100% da largura útil. O conteúdo temporário e a regra A4 são removidos após a impressão. O relatório exibido na tela e a lógica de dados permanecem inalterados.

**Verificações:** scripts passaram em `node --check`; patch reproduzido e comparado binariamente; preview e dois endereços de produção responderam HTTP 200 com SHA-256 `415c76197d1d63f6bfcc004c68d5aa096d0231b04892d0e3a323eaa8a1a64365`. **Limite:** prévia visual/ impressão em navegador não foi executada.

**Prévia:** `dpl_J6TyF62bEUAV3GC5Kg1V2sQPf473`.
**Produção:** `dpl_E4arP3wkNHdX1ksVXP4nYQTA2DPD`.
**URL:** https://adesai2-0.vercel.app/

**Segundo ciclo:** 3/5.

## Controle do ciclo de cinco entregas

**5 / 5 entregas documentadas no primeiro ciclo (18/11/2026).** Consolidação realizada em STATUS_ATUAL.md e CONTINUIDADE.md. Novo ciclo: **3/5**, incluindo a aba Cursos, a omissão das seções vazias e a impressão isolada do relatório. Preservar este histórico.

### Não confundir com entregas confirmadas
Os requisitos de cabeçalho de relatórios, impressão vertical, relação e reembolsos foram solicitados anteriormente, mas os respectivos detalhes de implementação não foram testados nesta entrega.
