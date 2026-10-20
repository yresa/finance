# 💳 Conciliação Multicanal: Asaas vs. Apple App Store vs. Google Play (`01_CONCILIACAO_ASAAS_VS_LOJAS.md`)

> **Objetivo:** Estabelecer as regras de convivência, repasse e conciliação entre a cobrança direta nacional (Asaas) e as compras in-app nas lojas oficiais móveis.

---

## 1. Comparativo Técnico e Financeiro dos Canais

| Critério | Asaas (Desktop & Web) | Apple App Store (IAP) | Google Play Store (Billing) |
| :--- | :--- | :--- | :--- |
| **Público / Superfície** | Usuários no navegador web ou aplicativo desktop | Usuários de iPhone, iPad e Mac no app iOS/macOS | Usuários de celulares e tablets no app Android |
| **Meios Aceitos** | Pix instantâneo e Cartão de Crédito nacional | Apple Pay, cartões vinculados ao Apple ID, saldo | Google Pay, cartões vinculados, saldo Google Play |
| **Taxa / Comissão** | ~0,99% a 1,99% (Pix) · ~2,99% + R$ 0,40 (Cartão) | **15%** (Small Business Program) / 30% padrão | **15%** (até US$ 1 milhão/ano) / 30% padrão |
| **Prazo de Repasse** | D+1 (Pix imediato; Cartão D+30 ou antecipado) | Mensal (aproximadamente 33 dias após fechamento) | Mensal (aproximadamente dia 15 do mês subsequente) |
| **Risco de Chargeback** | Baixo no Pix; moderado no Cartão | Assumido pela Apple | Assumido pelo Google |
| **Conformidade de Lojas** | Permitido fora do app; restrito em links no iOS | **Obrigatório** pela Apple Guideline 3.1.1 no iOS | **Obrigatório** pelas políticas de cobrança do Google |

---

## 2. Inscrição Obrigatória no *Small Business Program*

Para manter a taxa de comissão em 15% (e não 30%):
1. **Apple Small Business Program:** Inscrever a SLU da Yresá assim que a conta Apple Developer corporativa for ativada e o CNPJ homologado via número D-U-N-S.
2. **Google Play 15% Service Fee Tier:** Habilitar a taxa reduzida de 15% nas configurações financeiras do Google Play Console para o primeiro US$ 1 milhão de faturamento anual.

---

## 3. Fluxo de Conciliação no Gateway

No banco administrativo do Gateway:
- A tabela `subscriptions` registra `billing_provider` (`asaas`, `apple`, `google`), o identificador da assinatura na respectiva plataforma e a data de renovação.
- O Gateway valida webhooks do Asaas para pagamentos diretos e o *Server-to-Server Notification V2* da Apple e do Google para renovações, reembolsos e cancelamentos automáticos.
