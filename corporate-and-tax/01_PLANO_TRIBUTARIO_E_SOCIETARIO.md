# 🏢 Plano Tributário, Societário & CNAEs (`01_PLANO_TRIBUTARIO_E_SOCIETARIO.md`)

> **Objetivo:** Estabelecer a melhor estrutura jurídica e fiscal para a operação comercial da Yresá no Brasil, garantindo segurança patrimonial para o fundador e menor carga tributária legal.

---

## 1. Tipo Societário: Sociedade Limitada Unipessoal (SLU)

A Yresá opera sob o formato de **Sociedade Limitada Unipessoal (SLU)**:
- **Separação Patrimonial:** O patrimônio pessoal do fundador (Lucas Alencar) fica juridicamente separado do patrimônio e das obrigações da empresa.
- **Sócio Único:** Permite 100% das quotas sociais em nome do fundador, dispensando sócio figurativo ou exigências de capital social mínimo desproporcional.
- **Incompatibilidade com MEI:** O desenvolvimento de software, licenciamento de aplicativos e processamento de dados são atividades de natureza técnica/intelectual expressamente vedadas ao MEI (Lei Complementar nº 123/2006, Anexo XI).

---

## 2. Matriz de CNAEs (Classificação Nacional de Atividades Econômicas)

Para cobrir integralmente as operações do aplicativo móvel, do pórtico web, do Gateway e da inteligência artificial:

| CNAE | Descrição Oficial | Onde se Aplica no Ecossistema |
| :--- | :--- | :--- |
| **`6203-1/00` (Principal)** | Desenvolvimento e licenciamento de programas de computador customizáveis | Licenciamento do aplicativo `yresa-app` (Cronia) e planos de assinatura do software. |
| **`6202-3/00` (Secundário)** | Desenvolvimento de programas de computador sob encomenda | Engenharia e desenvolvimento de módulos e APIs da plataforma. |
| **`6209-1/00` (Secundário)** | Suporte técnico, manutenção e outros serviços em tecnologia da informação | Atendimento ao usuário, atualizações corretivas e suporte do produto. |
| **`6311-9/00` (Secundário)** | Tratamento de dados, provedores de serviços de aplicação e serviços de hospedagem na internet | Operação do microserviço de Gateway Mínimo e processamento de chamadas de IA. |
| **`6319-4/00` (Secundário)** | Portais, provedores de conteúdo e outros serviços de informação na internet | Manutenção do pórtico web institucional (`yresa-web`). |

---

## 3. Planejamento Tributário: Simples Nacional & Fator "R"

Os serviços de software e tecnologia no Simples Nacional enquadram-se na sistemática do **Fator R** (Art. 18, § 5º-J da Lei Complementar nº 123/2006):

$$\text{Fator R} = \frac{\text{Folha de Pagamento dos últimos 12 meses (incluindo Pró-Labore e encargos)}}{\text{Receita Bruta dos últimos 12 meses}}$$

1. **Se o Fator R for inferior a 28%:**
   - A empresa é tributada pelo **Anexo V**, com alíquota inicial pesada de **15,50%**.
2. **Se o Fator R for igual ou superior a 28%:**
   - A empresa é tributada pelo **Anexo III**, com alíquota inicial reduzida para **6,00%**.

### 3.1. Estratégia de Pró-Labore
A assessoria contábil da Yresá deve calcular mensalmente o Pró-Labore do fundador de forma que a razão $\frac{\text{Pró-Labore}}{\text{Faturamento}}$ permaneça sempre em patamar $\ge 28\%$. Isso garante a permanência no Anexo III, gerando economia tributária de até **9,5 pontos percentuais** sobre o faturamento bruto.

---

## 4. Arquitetura Societária Internacional & Fluxo de Royalties

### 4.1. Soberania da Matriz Brasileira & Subsidiária nos EUA
A **Yresá Tecnologia Ltda (Brasil)** é a controladora absoluta de todo o ecossistema. A eventual empresa nos EUA (`Yresa US LLC/Inc.`) opera como subsidiária integral pertencente ao CNPJ brasileiro:
- **Fluxo de Caixa Internacional:** O faturamento obtido de usuários internacionais nos EUA é recebido pela subsidiária americana e repatriado para a matriz brasileira a título de **Royalties de Licenciamento de Software** ou distribuição de lucros da subsidiária.
- **Propriedade Intelectual (PI):** A titularidade de 100% dos algoritmos, prompts, modelos ontológicos e patentes reside inegociavelmente na matriz brasileira.

### 4.2. O Modelo Híbrido de Faturamento (Nacional vs. Lojas)
1. **Canal Web & Desktop (Asaas):** Faturamento direto no Brasil via Pix (~1% de taxa) e Cartão Nacional (~2,99%). Margem máxima de rentabilidade e dinheiro em D+1.
2. **Canal Mobile (Apple App Store & Google Play):** Faturamento in-app nativo com conveniência de 1 clique (Face ID) sob a taxa reduzida de **15% (Small Business Program)**. A receita é classificada como **Exportação de Serviços** (tomador na Irlanda), usufruindo de alíquota tributária reduzida de **~3,05%** no Simples Nacional.

### 4.3. Diretriz para Investimento Externo e Aceleradoras (Y Combinator)
Em caso de ingresso em aceleradoras internacionais (como YC) ou captação com fundos de Venture Capital:
- A Yresá preserva a matriz brasileira no topo da estrutura societária.
- O investimento é recebido via **Investimento Estrangeiro Direto (RDE-IED via Banco Central do Brasil)** sob a forma de Mútuo Conversível Internacional, espelhando a jurisprudência e o modelo soberano adotado por grandes empresas globais (*Modelo Spotify*).
