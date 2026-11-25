# BRIEFING DO PROJETO — COMITÊ INDEPENDENTE DE MORADORES DO RESIDENCIAL CLUBE BRASIL

## 1. Identidade, Posicionamento e Regras de Negócio
- **Nome da iniciativa:** Comitê Independente de Moradores do Residencial Clube Brasil
- **Slogan:** Regras iguais para todos. Fiscalização, transparência e respeito.
- **E-mail oficial para dúvidas e LGPD:** `comiteindependente.cb@gmail.com`
- **Condomínio de referência:** Condomínio Residencial Clube Brasil — Novo Hamburgo/RS (120 unidades totais: Bloco 1 ao Bloco 12, cada um com apartamentos 11, 12, 21, 22, 31, 32, 41, 42, 51, 52).
- **Subtítulo principal (Hero):** "O Regulamento Interno existe para ser cumprido — não ignorado. Moradores organizados pelo fim da seletividade nas regras, pela apuração real das reclamações e pelo direito básico ao sossego."
- **Princípio estrutural:** Se uma regra precisa mudar, que seja discutida e alterada pelo rito formal em assembleia. Enquanto estiver vigente, deve ser cumprida e aplicada de forma igualitária a todas as unidades, sem privilégios ou seletividade.
- **Restrições obrigatórias (não violar):**
  1. Deixar explícito no topo, antes do formulário e no rodapé que esta é uma **iniciativa independente e voluntária de moradores**, sem vínculo institucional, autorização ou representação oficial do Condomínio Residencial Clube Brasil, do síndico ou da administradora (ADCON).
  2. NÃO usar logotipo oficial do condomínio ou da administradora.
  3. NÃO mencionar nomes de moradores, síndico, números de apartamentos específicos ou tom ameaçador.
  4. NÃO divulgar metas numéricas de adesão na página pública. Informar apenas que o grupo privado de WhatsApp será criado mediante adesão suficiente de unidades distintas.
  5. Os dados do formulário alimentarão uma planilha privada no Google Sheets (via Google Apps Script) e o site terá botão para download direto do arquivo `./public/regulamento-interno.pdf`.

## 2. Identidade Visual e Arquitetura (Mobile-First)
- **Stack tecnológica:** Projeto ágil e leve em HTML5, Tailwind CSS e JavaScript puro (garantindo carregamento ultrarrápido em 4G mobile).
- **Direção estética:** Visual institucional cívico/editorial — sério, firme e organizado, sem cara de escritório de advocacia tradicional.
  - **Paleta:** Azul-ardósia profundo (`#0F172A` / `#1E293B`) como base de contraste, fundo claro off-white (`#F8FAFC`) nas seções de leitura, texto em grafite escuro (`#0F172A`), e acentos em âmbar/mostarda sóbrio (`#B45309` / `#D97706`) ou verde-esmeralda institucional (`#065F46`) para destaques e botões.
  - **Tipografia:** Sans-serif geométrica limpa e moderna (`Plus Jakarta Sans` para títulos e `Inter` para leitura e formulários).
- **Hero Section (Mobile-First):**
  - Selo superior discreto: `INICIATIVA INDEPENDENTE DE MORADORES • NOVO HAMBURGO/RS`
  - Identificação da iniciativa: **Comitê Independente de Moradores do Residencial Clube Brasil**
  - Headline (H1): **Regras iguais para todos. Fiscalização, transparência e respeito.**
  - Subheadline: *"O Regulamento Interno existe para ser cumprido — não ignorado. Moradores organizados pelo fim da seletividade nas regras, pela apuração real das reclamações e pelo direito básico ao sossego."*
  - Botão primário: **Participar da pesquisa de interesse** (scroll suave até `#pesquisa`).
  - Imagem `./public/portaria-clube-brasil.webp` apresentada logo abaixo no mobile (e ao lado no desktop) em um card com bordas arredondadas, proporção integral preservada (`aspect-[4/3]`) para não cortar a guarita nem os portões laterais.

## 3. Seções de Conteúdo da Página

### Seção A — O que o nosso Regulamento Interno já determina
Apresentar 3 cards objetivos citando literalmente as normas vigentes do documento oficial do condomínio, seguidos de um botão destacado para baixar o PDF completo (`./public/regulamento-interno.pdf`):
1. **Horários de Silêncio Absoluto (Regra 1ª):**
   *"De acordo com a lei municipal em vigor, deve ser observado o horário de silêncio absoluto em todo o prédio, das 22h às 7h... Nos finais de semana, além desse horário, deverá ser mantido o silêncio no horário compreendido entre 12h e 15h, bem como nos feriados."*
2. **Limite de Ruído Fora do Horário (Regra 1ª):**
   *"Fora desse horário, deve-se ter o cuidado e evitar que o barulho (música, conversas, etc.) ultrapasse as dependências do apartamento."*
3. **Advertência e Multas Progressivas (Regra 31ª):**
   *"A desobediência a qualquer dos itens deste regulamento ou da convenção do condomínio sujeitará o infrator e ou seu responsável legal, a uma advertência verbal ou por escrito, segundo a gravidade da mesma, e após a cobrança de multa de uma taxa condominial e o dobro por reincidência."*
- **CTA da Seção:** Botão secundário com ícone de documento: **Baixar Regulamento Interno completo (PDF)** (`download="Regulamento-Interno-Clube-Brasil.pdf"`).

### Seção B — O que buscamos construir juntos
4 pilares claros de atuação institucional:
1. **Protocolo e resposta formal:** Que toda reclamação individual formalizada receba protocolo, registro e retorno claro da administração dentro de prazo razoável.
2. **Apuração individual de provas:** Separar o recebimento e apuração de ocorrências documentadas (áudio, vídeo, registros com data e hora) da aplicação de sanções, garantindo direito de defesa e critérios objetivos.
3. **Isonomia sem seletividade:** Aplicação uniforme das regras em todas as unidades e áreas comuns — fim do tratamento desigual entre moradores.
4. **Revisão democrática em assembleia:** Se alguma regra atual não reflete mais a realidade do condomínio, que seja debatida e alterada pelo quórum formal em assembleia, e nunca ignorada no dia a dia.

### Seção C — Formulário de Pesquisa de Interesse (`#pesquisa`)
Incluir antes do formulário um aviso curto de que dúvidas antes do preenchimento podem ser enviadas anonimamente ou sem identificar unidade para `comiteindependente.cb@gmail.com`.

Formulário completo, acessível, com validação cruzada de unidade e envio via `fetch` POST para endpoint configurável do Google Apps Script (`GOOGLE_SCRIPT_URL`):

1. **Nome completo** (`input text`, obrigatório).
2. **Bloco** (`select`, obrigatório): opções exatas de `Bloco 1` até `Bloco 12`.
3. **Apartamento** (`select`, obrigatório, habilitado após escolher o bloco): opções exatas `11`, `12`, `21`, `22`, `31`, `32`, `41`, `42`, `51`, `52` (impede unidades inexistentes).
4. **Vínculo com a unidade** (`select`, obrigatório):
   - `Proprietário(a)`
   - `Inquilino(a)`
   - `Outro vínculo (familiar/morador autorizado)`
5. **WhatsApp para contato** (`input tel` com máscara `(51) 99999-9999`, obrigatório).
6. **E-mail** (`input email`, opcional).
7. **Quais situações você enfrenta ou observa no condomínio?** (`checkbox` múltipla seleção, ao menos 1 obrigatório):
   - Ruídos de impacto / batidas no piso
   - Portas ou portões batendo com força
   - Arrastamento de móveis
   - Música, conversas, gritos ou outros ruídos excessivos
   - Ruídos durante a noite ou madrugada
   - Reformas ou instalações fora dos horários permitidos
   - Problemas de padronização ou uso nas áreas comuns / estacionamento
   - Aplicação aparentemente desigual das regras ou falta de resposta da administração
   - Multas ou advertências sem procedimento claro ou oportunidade de esclarecimento
   - Não enfrento problemas no momento, mas apoio a iniciativa
   - Outros *(exibir campo de texto curto se marcado)*
8. **Frequência das ocorrências** (`radio`, obrigatório):
   - `Frequentemente`
   - `Ocasionalmente`
   - `Pontualmente`
   - `Não se aplica`
9. **Períodos em que ocorrem** (`checkbox` múltipla escolha):
   - `Manhã` | `Tarde` | `Noite` | `Madrugada` | `Horários variados` | `Não se aplica`
10. **Já comunicou formalmente à administração ou síndico?** (`radio`, obrigatório):
    - `Sim, sem solução`
    - `Sim, solução parcial`
    - `Sim, foi resolvido`
    - `Não comuniquei`
    - `Não sei como registrar`
11. **Existe alguma unidade relacionada ao problema? (Opcional e estritamente confidencial)** (`radio`):
    - `Prefiro informar reservadamente no contato individual`
    - `Sei qual é a unidade`
    - `Tenho suspeita, mas não certeza`
    - `Não sei / Não se aplica`
    - *Condicional:* Se marcar `"Sei qual é a unidade"` ou `"Tenho suspeita"`, exibir campo de texto opcional com destaque visual: **"Informação estritamente confidencial: este dado será acessado apenas pela organização da pesquisa e jamais será divulgado publicamente ou sem sua expressa autorização."**
12. **Como você estaria disposto(a) a participar desta iniciativa?** (`checkbox` múltipla seleção, ao menos 1 obrigatório):
    - Apenas receber informações sobre a iniciativa
    - Participar de um grupo privado de WhatsApp (se houver adesão suficiente)
    - Relatar problemas e compartilhar registros/provas de forma responsável
    - Apoiar reivindicações administrativas formais
    - Assinar abaixo-assinado ou documentos coletivos
    - Participar de assembleias presencialmente, quando possível
    - Ajudar a organizar a mobilização
    - Apoiar proposta de alteração ou aprimoramento do Regulamento Interno
    - Avaliar participação em medida jurídica coletiva após orientação de advogado (sem compromisso nesta etapa)
13. **Termo de Ciência e Consentimento (LGPD)** (`checkbox` obrigatório):
    - *"Li e compreendi que esta é uma iniciativa independente e voluntária de moradores, sem vínculo oficial com o condomínio ou administradora. Autorizo o armazenamento restrito destes dados em planilha privada sob controle exclusivo da organização da iniciativa para validar meu vínculo com a unidade, realizar contato individual e avaliar a adesão, ciente de que relatos individuais e indicações de unidades jamais serão compartilhados sem minha expressa autorização."*
    - Incluir link clicável **"Ler Política de Privacidade e LGPD"** que abre um modal limpo na própria página.

## 4. Documentos Legais Integrados (Modais na Página + Banner de Cookies)
1. **Modal — Política de Privacidade e Proteção de Dados (LGPD — Lei 13.709/2018):**
   - **Controlador/Responsável:** Comitê Independente de Moradores do Residencial Clube Brasil — iniciativa voluntária de moradores (contato: `comiteindependente.cb@gmail.com`).
   - **Finalidade exclusiva:** Verificar vínculo legítimo com uma das 120 unidades do condomínio, dimensionar a adesão por bloco/unidade e realizar contato individual prévio antes de eventual criação de grupo privado.
   - **Armazenamento e Segurança:** Dados armazenados em planilha privada com acesso restrito por autenticação em duas etapas, sem compartilhamento comercial, publicitário ou divulgação pública em grupos.
   - **Sigilo de Relatos:** Indicações de unidades ou relatos individuais não serão divulgados a terceiros nem incluídos em documentos coletivos sem autorização expressa do titular.
   - **Direitos do Titular:** Qualquer participante pode solicitar confirmação, correção ou exclusão definitiva de seus dados a qualquer momento pelo e-mail `comiteindependente.cb@gmail.com`.
   - **Canal Oficial:** Reforçar que esta pesquisa não substitui o protocolo formal de reclamações junto à administradora/síndico.
2. **Banner Discreto de Cookies e Armazenamento Local:**
   - Exibir banner discreto na base da tela informando: *"Este site utiliza apenas armazenamento técnico essencial para funcionamento da página e proteção contra envios duplicados, sem rastreamento publicitário invasivo. Ao continuar, você concorda com nossa Política de Privacidade."* com botões **"Entendi"** e **"Ver Política de Privacidade"**. (Preparado também para ciência caso o Pixel da Meta seja ativado para mensuração do anúncio).

## 5. Rodapé (Footer)
- Aviso institucional claro: *"Comitê Independente de Moradores do Residencial Clube Brasil — Iniciativa independente e voluntária de moradores (Novo Hamburgo/RS). Este site não possui vínculo institucional, autorização ou representação oficial do condomínio, do síndico ou da administradora."*
- Links para abrir os modais de **Política de Privacidade (LGPD)** e **Termos de Uso / Aviso de Cookies**.
- Contato direto para dúvidas antes do preenchimento: `comiteindependente.cb@gmail.com`.