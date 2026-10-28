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

## 2. Tratamento Fiscal das Lojas de Aplicativos (Apple & Google) — Regime de Exportação de Serviços

Nas compras realizadas pelo fluxo de assinaturas nas lojas oficiais móveis (Apple App Store e Google Play Store):

### 2.1. Natureza Jurídica: Exportação de Software para a Irlanda
* **Apple:** O contrato de desenvolvedor é firmado com a **Apple Distribution International Ltd.** (Hollyhill Industrial Estate, Cork, Irlanda — VAT IE9700053D).
* **Google:** O contrato de distribuição é firmado com a **Google Ireland Limited** (Gordon House, Barrow Street, Dublin 4, Irlanda — VAT IE6388047V).
* **Enquadramento Tributário:** A Receita Federal do Brasil classifica formalmente essas operações como **Exportação de Serviços** com tomador no exterior.

### 2.2. O Benefício Fiscal da Exportação (Redução para ~3,05%)
Pela Constituição Federal (Art. 149 e 156) e pela Lei Complementar nº 123/2006, a exportação de serviços possui **imunidade/isenção de PIS, COFINS e ISS**:
* **Alíquota Padrão Nacional (Anexo III):** 6,00%
* **Alíquota Real sobre Receitas de Lojas no Exterior:** **~3,05%** (recolhe apenas CPP 2,60%, IRPJ 0,24% e CSLL 0,21%).
* A economia tributária líquida na receita das lojas é de quase **50% dos impostos da empresa**.

### 2.3. Roteiro Operacional de Emissão Mensal (1 Nota por Loja)
O fundador **não deve emitir dezenas de notas fiscais individuais** para cada usuário de iPhone ou Android:
1. No último dia do mês, baixe o *Financial Report* consolidado no App Store Connect e no Google Play Console.
2. Identifique o **Valor Bruto Total** faturado pelas assinaturas no mês (em USD ou BRL).
3. Converta o valor bruto para Reais usando a **Taxa PTAX de Venda** oficial do Banco Central do Brasil referente ao último dia do mês.
4. Emita apenas **1 (uma) NFS-e mensal única** para a Apple Distribution International e **1 (uma) NFS-e mensal única** para a Google Ireland no portal da prefeitura.
5. **Campo de Tributação:** Selecione *"Exportação de Serviços com não-incidência de ISS"*.
6. A comissão de 15% retida pelas lojas é lançada na contabilidade como **Despesa Operacional de Intermediação Comercial**, sem bitributação.
