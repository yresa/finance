# 🧾 Emissão Fiscal & Automação de NFS-e (`02_EMISSAO_FISCAL_E_NFSE.md`)

> **Objetivo:** Garantir a emissão automatizada e o cumprimento de 100% das obrigações fiscais perante a Fazenda Municipal sem sobrecarga operacional humana.

---

## 1. Fluxo de Emissão Fiscal com o Asaas

Para as assinaturas e recargas contratadas via **Pix** ou **Cartão de Crédito** no Brasil:

1. **Gatilho de Pagamento Confirmado:** O usuário efetua o pagamento via Asaas (Pix ou cartão).
2. **Webhook do Gateway:** O Asaas dispara o evento `PAYMENT_RECEIVED` para o endpoint seguro do Gateway (`POST /api/v1/billing/webhook/asaas`).
3. **Módulo Fiscal Automatizado:**
   - O Asaas possui integração nativa com o sistema de Nota Fiscal de Serviços Eletrônica (NFS-e) da maioria dos municípios brasileiros.
   - O Asaas gera a NFS-e com o código de tributação correspondente ao CNAE `6203-1/00` (licenciamento de software) e envia o link do PDF/XML diretamente para o e-mail do assinante.
4. **Guarda Obrigatória:** O registro numérico da NFS-e é mantido nos servidores fiscais pelo prazo decadencial/prescricional de **5 (cinco) anos**, em conformidade com o Código Tributário Nacional (art. 173) e a LGPD (art. 16, I).

---

## 2. Tratamento Fiscal das Lojas de Aplicativos (Apple & Google)

Nas compras realizadas diretamente pelo fluxo *In-App Purchase* (IAP):

1. **A Relação Comercial:** A Apple Inc. e o Google LLC atuam como distribuidores comerciais perante o consumidor final, emitindo o recibo fiscal direto da loja ao usuário de iPhone ou Android.
2. **Repasse Líquido à Yresá (*Net Payout*):** A Apple e o Google transferem mensalmente à conta bancária da SLU da Yresá o valor líquido já descontada a comissão de 15% (sob o *Small Business Program*).
3. **Contabilização:** A assessoria contábil emite mensalmente a nota fiscal de prestação de serviços referente ao valor repassado líquido (ou conforme a orientação contábil sobre exportação/prestação de serviços de intermediação das lojas).
