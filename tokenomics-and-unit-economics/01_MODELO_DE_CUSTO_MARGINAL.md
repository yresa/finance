# ⚡ Modelo de Custos Marginais & Unit Economics (`01_MODELO_DE_CUSTO_MARGINAL.md`)

> **Objetivo:** Mapear a anatomia dos custos de computação de inteligência artificial por trás de cada interação mnemônica, garantindo que o plano de assinatura tenha margem operacional saudável e sustentável.

---

## 1. Tabela de Custos de APIs (Google Cloud Vertex AI / Paid API)

A consolidação em provedor único no Google Cloud unifica o faturamento corporativo:

| Modelo / Funcionalidade | Finalidade no `yresa-app` | Unidade de Cobrança | Custo Unitário Estimado (US$) | Custo Convertido Estimado (R$ ~5,50) |
| :--- | :--- | :--- | :--- | :--- |
| **Gemini 3.5 Flash-Lite** | Sínteses rápidas, extração de entidades e indexação | 1M tokens (entrada/saída) | ~US$ 0,075 / 1M input · ~US$ 0,30 / 1M output | ~R$ 0,0004 por reflexão média (1k tokens) |
| **Gemini 3.6 Flash** | Diálogos reflexivos aprofundados e resumos biográficos | 1M tokens | ~US$ 0,10 / 1M input · ~US$ 0,40 / 1M output | ~R$ 0,0015 por diálogo denso (3k tokens) |
| **Gemini Transcribe 3.5** | Transcrição de áudio e separação de vozes (*diarization*) | Por minuto de áudio processado | ~US$ 0,006 / minuto | ~R$ 0,033 por minuto de áudio gravado |
| **Gemini Multimodal Live API** | Sessão de voz em tempo real (*conversação fluida ao vivo*) | Por minuto de áudio bidirecional em streaming | ~US$ 0,020 / minuto | ~R$ 0,110 por minuto de voz ao vivo |

---

## 2. Anatomia de Consumo Mensal por Perfil de Assinante

### Perfil Médio de Assinante Ativo (Uso Típico Contemplativo):
- **Reflexões de Texto (Flash-Lite / Flash):** 60 reflexões e sínteses no mês $\rightarrow$ **~R$ 0,08**
- **Gravação de Áudios e Transcrição:** 60 minutos de relatos em voz no mês $\rightarrow$ **~R$ 1,98**
- **Sessões de Voz ao Vivo (Live API):** 20 minutos de conversa ao vivo no mês $\rightarrow$ **~R$ 2,20**
- **Custo Total de Computação de IA por Usuário:** **~R$ 4,26 / mês**

---

## 3. Análise de Margem Operacional Bruta (Gross Margin)

Para o **Plano Membro Mensal a R$ 29,90/mês**:

### Cenário 1: Pagamento Direto no Asaas (Pix / Cartão)
- **Receita Bruta:** R$ 29,90
- **Impostos (Simples Nacional Fator R a 6%):** - R$ 1,79
- **Taxa de Gateway Asaas (~1,99% Pix/Cartão):** - R$ 0,60
- **Custo de IA / Google Cloud (Perfil Médio):** - R$ 4,26
- **Margem de Contribuição Líquida:** **R$ 23,25 por usuário/mês** (**~77,7% de margem bruta**)

### Cenário 2: Assinatura In-App via Apple App Store / Google Play (15% de Comissão)
- **Receita Bruta:** R$ 29,90
- **Comissão da Loja (15% - Small Business Program):** - R$ 4,49
- **Receita Líquida Recebida:** R$ 25,41
- **Impostos sobre repasse líquido (~6%):** - R$ 1,52
- **Custo de IA / Google Cloud (Perfil Médio):** - R$ 4,26
- **Margem de Contribuição Líquida:** **R$ 19,63 por usuário/mês** (**~65,6% de margem bruta**)

> [!TIP]
> **Conclusão:** Mesmo absorvendo os 15% de taxa da Apple e do Google pela conveniência do Apple Pay / Google Pay, a margem de contribuição permanece acima de **65%**, garantindo alta sustentabilidade para o negócio.
