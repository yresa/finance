# 🛡️ Governança Financeira & Proteção de Segredos (`GOVERNANCE.md`)

> Regras de integridade, sigilo e boas práticas para manutenção dos registros financeiros da Yresá.

---

## 1. Princípio do Sigilo e Minimização de Dados (Zero PII Financeiro)

1. **Nunca comitar dados bancários brutos ou pessoais:** Extratos bancários com nomes de clientes, CPFs, chaves Pix privadas ou números de contas correntes jamais devem ser adicionados ao versionamento Git.
2. **Utilizar Dados Agregados e Modelos:** O repositório armazena blueprints, fórmulas de custo unitário (*Unit Economics*), tabelas de alíquotas fiscais, modelos de DRE e relatórios agregados anônimos.
3. **Segredos e Credenciais de APIs:** Chaves de API do Asaas, Stripe, Apple App Store Connect API e Google Play Developer API vivem exclusivamente em variáveis de ambiente protegidas (`.dev.vars`, Cloudflare Secrets ou Cofre Seguro de CI/CD), nunca em texto claro.

---

## 2. Ciclo de Fechamento Contábil e Conciliação

O fechamento financeiro do ecossistema segue o ritmo mensal:

1. **Dia 01 ao Dia 05 de cada mês:**
   - Fechamento da fatura consolidada do Google Cloud (Vertex AI / Gemini API);
   - Conciliação dos repasses líquidos (*net payouts*) da Apple App Store e do Google Play;
   - Exportação e conferência do relatório de NFS-e emitidas via Asaas perante a Secretaria Municipal de Finanças.
2. **Dia 10:**
   - Apuração do Simples Nacional (DAS) pela assessoria contábil da SLU, verificando o cumprimento da meta de $\ge 28\%$ do Fator R.
3. **Dia 20:**
   - Fechamento do DRE Mínimo do ciclo anterior e conferência da métrica de *Gross Margin* por assinante ativo.
