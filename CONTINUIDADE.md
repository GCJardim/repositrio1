# Guia de continuidade — próximo chat do ADESAI2.0

## Objetivo
Dar continuidade ao ADESAI2.0 sem perder funcionalidades e decisões já aprovadas.

## Leia primeiro
- `README.md`: visão geral.
- `STATUS_ATUAL.md`: fatos verificados e pontos ainda não confirmados.
- `HISTORICO.md`: entregas, validações e identificadores de deploys.

## Método de trabalho
1. Confirmar o ambiente, código existente e o último deployment Vercel antes de qualquer edição.
2. Preservar o layout das fichas e demais áreas não solicitadas.
3. Modificar somente o módulo pedido e realizar testes.
4. Diferenciar **solicitado**, **implementado**, **publicado** e **testado**.
5. Não dizer que foi concluído antes de verificar.
6. Depois de cada entrega efetivamente concluída, adicionar uma entrada ao HISTORICO.md, com data, escopo, arquivos, testes, resultado, eventual rollback e URL.
7. A cada 5 entregas documentadas, atualizar o resumo de STATUS_ATUAL.md e as orientações deste arquivo. Manter histórico cumulativo.

## Ambiente conhecido em 18/11/2026
- Endereço público: https://adesai2-0.vercel.app/
- Vercel project ID: `prj_kNnDldgjmDxXe22te7I3ecQjWfsN` (nome `adesai2-0`).
- Deploy de produção da sidebar atualizada: `dpl_27auN7ZW8si9GDVtaFRraHCAfFkL`.
- Deploy anterior de produção: `dpl_6VJ2yx9udfWMJ2j9oV59ZLEPeics` (correção da foto na impressão da ficha).
- Deploy anterior de produção: `dpl_jcMuX1jHh4oaPJjjSxL6SMDhRXSi` (reorganização do editor Nova ficha cadastral).
- **Último deploy de produção:** `dpl_4iJNc3XEsFH1HYquqtZqWVXJfbt1` (ocultação do botão móvel de menu na impressão).
- CSS isolado do editor `adesai-ficha-layout-fix`: corrige recuo com menu recolhido ou expandido, rodapé de botões não flutuante, distribuição responsiva das abas e painéis. Verificar visualmente a tela ao abrir o formulário.
- Base anterior: `dpl_D7A8fbCfyeMsfQoScen1zwXSzAw9`.
- Na última atualização, app mantinha HTML monolítico com CSS e JS embutidos; os módulos eram renderizados via `render()`.
- Impressão da ficha: foto posicionada em coluna própria e campos em `pf-first-fields`, regras específicas em `adesai-print-photo-fix`; verificar visualmente uma nova impressão física antes de considerar o resultado visual totalmente confirmado.
- Atualização da sidebar incorporada ao HTML, com grupos `SIDEBAR_GROUPS` e `sidebarClosedGroups`; estilos no bloco `sidebar-adesai-modern` e comportamentos no bloco `sidebar-adesai-behavior`.
- Deploy atual foi reconstruído via build que obtém uma versão anterior da Vercel e aplica patch controlado; para novas mudanças, inspecionar os arquivos do deploy atual, não presumir que a página será editável diretamente no GitHub.
- Este repositório foi identificado como `GCJardim/repositrio1` e estava vazio antes da documentação; **não assumir** que Vercel está conectado a ele.

## Decisões de produto
- Design institucional azul e amarelo, logo oficial.
- Ficha aprovada provisoriamente: preservar, salvo pedido explícito.
- Enter navega entre campos da ficha, não salva; salvar apenas via botão.
- Campos da ficha digital devem corresponder à impressa, incluindo cútis.
- Relatórios e relação devem ter cabeçalho institucional e impressão adequada.
- Controle mensal de reembolsos foi solicitado.
- Priorizar alteração pontual, sem refazer telas inteiras.

## Limites e segurança
- Não copiar dados reais de participantes, documentos, logins, senhas ou tokens para este GitHub público.
- Não assumir que a persistência via Supabase está ativa sem verificação.
- Preferir preview + testes antes de publicar produção.
- Se não houver acesso ao código-fonte real, buscar na Vercel antes de qualquer alteração.

## Próxima ação
Leia a solicitação atual da usuária e confirme o estado mais recente antes de mexer. Se ela pedir ajuste na sidebar, começar verificando se a versão de 18/11/2026 está no ar. Contador de entregas: **4/5**.
