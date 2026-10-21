# Yresá Finance — Backlog de Governança Econômica & Sustentabilidade

> Documento vivo para registro de diretrizes financeiras, precificação, unit economics, conciliação multicanal e compliance tributário do ecossistema Yresá.

---

## Estrutura de Cada Item do Backlog
Cada item registrado neste documento responde a cinco perguntas fundamentais:
1. **O quê?** (Título e resumo claro da ação de engenharia financeira)
2. **Por que fazer?** (Fundamentação ontológica, margem operacional ou conformidade fiscal)
3. **Quando fazer?** (Critério ou gatilho de ativação operacional)
4. **Como fazer?** (Estratégia de cálculo, regras contábeis e APIs integradas)
5. **Critério de Conclusão** (Como sabemos que está pronto e validado)

---

## 📋 Itens Mapeados no Backlog

### [FIN-01] Hidrômetro Numérico (`token_ledger`) e Rastreamento Atuarial de Custos de IA

* **Status:** Backlog
* **Iniciativa / Épico:** Hidrômetro Numérico & Inteligência Atuarial
* **Prioridade:** Alta (Sustentabilidade do Modelo de Negócio)
* **Domínios / Módulos Envolvidos:** `tokenomics-and-unit-economics/02_HIDROMETRO_E_LIMITES_DE_COTAS.md`, `yresa/cloud`
* **Referências:** Tabela de Custos do Gemini Vertex AI, Política Zero-Knowledge.

#### 1. Contexto & Por Que Fazer
Para assegurar que o plano de assinatura (R$ 29,90) mantenha uma margem de contribuição saudável (superior a 65%), o Gateway precisa rastrear os custos reais de computação gerados por cada usuário, sem violar a privacidade de suas memórias. O Hidrômetro Numérico grava exclusivamente metadados contábeis na tabela `token_ledger`.

#### 2. Quando Fazer (Gatilhos de Ativação)
- Concomitante ao desenvolvimento da rota de proxy Gemini no Gateway em `yresa/cloud`.
- Antes de liberar a Cota de Descoberta para os primeiros usuários de teste.

#### 3. Como Fazer (Estratégia Cirúrgica)
1. Criar a tabela `token_ledger` (ID, user_id, modelo, tokens_input, tokens_output, voice_seconds, timestamp).
2. No Gateway Go, capturar o cabeçalho de resposta do Gemini com a contagem de tokens processados.
3. Gravar de forma assíncrona o registro atuarial após responder a requisição do usuário.
4. Calcular o custo financeiro acumulado por usuário para checagem de teto de cota.

#### 4. Riscos Mitigados
- Previne usuários com consumo desproporcional (*heavy users*) que possam gerar margem negativa para a empresa.
- Mantém conformidade com a política de *Zero-Storage* (zero gravação de texto pessoal no servidor).

#### 5. Critério de Conclusão
- Cada chamada ao Gemini registrada na tabela com tokens e custo em USD/BRL calculados com precisão.

---

### [FIN-02] Pipeline de Conciliação Financeira Multicanal (Asaas vs. Apple Pay vs. Google Play)

* **Status:** Backlog
* **Iniciativa / Épico:** Conciliação Financeira Multicanal
* **Prioridade:** Alta (Fechamento de Caixa & Tesouraria)
* **Domínios / Módulos Envolvidos:** `payment-channels-and-settlement/01_CONCILIACAO_ASAAS_VS_LOJAS.md`
* **Referências:** Apple StoreKit, Google Play Billing, API do Asaas.

#### 1. Contexto & Por Que Fazer
A receita da Yresá entra por múltiplos canais com prazos de repasse e taxas distintas: Asaas (Pix imediato / D+1 / taxa ~1,99%), Apple App Store (repasse mensal líquido após comissão de 15%) e Google Play (repasse mensal líquido de 15%). Uma esteira unificada de conciliação evita discrepâncias entre o que foi vendido e o que caiu no banco.

#### 2. Quando Fazer (Gatilhos de Ativação)
- Quando o aplicativo for submetido nas lojas com In-App Purchase habilitado.

#### 3. Como Fazer (Estratégia Cirúrgica)
1. Estabelecer modelo de dados unificado de assinatura com campo `origin_channel` (`asaas`, `apple_iap`, `google_play`).
2. Mapear o recebimento dos relatórios financeiros mensais da Apple e Google (Settlement Reports).
3. Alimentar a planilha mestre de DRE Mínimo com as entradas reais líquidas consolidadas.

#### 4. Riscos Mitigados
- Elimina descasamento de fluxo de caixa entre a despesa imediata de IA (fatura Google Cloud) e o repasse das lojas (ciclo de 30-45 dias).

#### 5. Critério de Conclusão
- DRE mensal refletindo com 100% de exatidão a receita líquida e o saldo em conta corrente.

---

### [FIN-03] Formalização Societária SLU e Enquadramento Simples Nacional Fator R (6%)

* **Status:** Backlog
* **Iniciativa / Épico:** Estruturação Societária & Tributária
* **Prioridade:** Alta (Governança Corporativa & Eficiência Tributária)
* **Domínios / Módulos Envolvidos:** `corporate-and-tax/01_PLANO_TRIBUTARIO_E_SOCIETARIO.md`
* **Referências:** Legislação do Simples Nacional, Anexo III vs. Anexo V, CNAE 62.01-5-01.

#### 1. Contexto & Por Que Fazer
Empresas de software (SaaS) no Brasil podem ser tributadas pelo Anexo V do Simples Nacional (alíquota inicial pesada de 15,5%) ou pelo Anexo III (alíquota inicial leve de 6%), desde que a folha de pagamento/pró-labore represente pelo menos 28% da receita bruta (regra do **Fator R**). A estrutura correta reduz o pagamento de impostos em mais de 60% legalmente.

#### 2. Quando Fazer (Gatilhos de Ativação)
- Imediatamente antes de receber as primeiras receitas reais de assinantes pagantes.

#### 3. Como Fazer (Estratégia Cirúrgica)
1. Abrir a Sociedade Limitada Unipessoal (SLU) com capital social adequado e CNAEs de desenvolvimento de software e portais.
2. Alinhar com a contabilidade a emissão mensal do pró-labore do fundador calibrado para manter o Fator R $\ge 28\%$.
3. Cadastrar a empresa nos programas de pequena empresa da Apple e Google para garantir a taxa de 15% nas lojas.

#### 4. Riscos Mitigados
- Previne autuações fiscais e bitributação de faturamento.
- Garante a maior margem líquida possível nos primeiros anos da operação.

#### 5. Critério de Conclusão
- CNPJ ativo com alíquota inicial comprovada de 6% no Simples Nacional.

---

### [FIN-04] Emissão Fiscal Automatizada e Parametrização Tributária de NFS-e

* **Status:** Backlog
* **Iniciativa / Épico:** Faturamento Asaas & Automação Fiscal
* **Prioridade:** Média-Alta (Compliance Fiscal)
* **Domínios / Módulos Envolvidos:** `corporate-and-tax/02_EMISSAO_FISCAL_E_NFSE.md`
* **Referências:** API de Notas Fiscais do Asaas, Secretaria Municipal da Fazenda.

#### 1. Contexto & Por Que Fazer
Toda venda a consumidor final no Brasil exige a emissão da respectiva Nota Fiscal de Serviço eletrônica (NFS-e). O processo manual para dezenas ou centenas de assinantes é inviável e gera passivo fiscal.

#### 2. Quando Fazer (Gatilhos de Ativação)
- Após a liberação do cadastro municipal de prestador de serviços da empresa.

#### 3. Como Fazer (Estratégia Cirúrgica)
1. Configurar o módulo de emissão automática de NFS-e nativo da conta do Asaas.
2. Parametrizar a emissão com o código municipal correto de serviço de informática/SaaS.
3. Agendar a emissão para ocorrer automaticamente após a compensação do pagamento.

#### 4. Riscos Mitigados
- Elimina multas por atraso ou omissão de emissão fiscal.
- Entrega imediata da nota fiscal no e-mail do cliente, aumentando a credibilidade da marca.

#### 5. Critério de Conclusão
- NFS-e gerada e enviada por e-mail automaticamente em cada transação de teste aprovada.
