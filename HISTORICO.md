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

## Controle do ciclo de cinco entregas

**3 / 5** entregas documentadas neste ciclo. As duas próximas devem ser registradas somente após conclusão e verificação. Ao atingir 5, consolidar STATUS_ATUAL.md e CONTINUIDADE.md.

### Não confundir com entregas confirmadas
Os requisitos de cabeçalho de relatórios, impressão vertical, relação e reembolsos foram solicitados anteriormente, mas os respectivos detalhes de implementação não foram testados nesta entrega.
