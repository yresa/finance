# 💧 Hidrômetro Numérico & Sustentabilidade da Cota de Descoberta (`02_HIDROMETRO_E_LIMITES_DE_COTAS.md`)

> **Objetivo:** Estabelecer a sustentabilidade da degustação gratuita (Cota de Descoberta) e as regras operacionais do hidrômetro numérico do Gateway.

---

## 1. O Hidrômetro Numérico do Gateway (`token_ledger`)

Para proteger o princípio da soberania e do *Zero-Storage*, o Gateway Mínimo **nunca registra o que o usuário disse ou escreveu**. Ele anota unicamente números em `token_ledger`:

```sql
CREATE TABLE token_ledger (
    id SERIAL PRIMARY KEY,
    user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    model_name VARCHAR(64) NOT NULL,
    tokens_input INT NOT NULL DEFAULT 0,
    tokens_output INT NOT NULL DEFAULT 0,
    voice_seconds INT NOT NULL DEFAULT 0,
    timestamp TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```

---

## 2. A Cota de Descoberta Gratuita (Custo de Aquisição Controlado)

A Cota de Descoberta gratuita foi desenhada para encantar o usuário por valor real, sem exigir cartão de crédito e sem risco de surpresa:

- **Franquia Inicial Gratuita:**
  - Até 100 reflexões/sínteses mnemônicas (Gemini Flash);
  - Até 30 minutos de áudio gravado e transcrito (Gemini Transcribe 3.5);
  - Até 15 minutos de conversação por voz ao vivo (Gemini Live API).
- **Custo Unitário Máximo da Cota por Usuário Cadastrado:**
  - Texto: ~R$ 0,15
  - Transcrição: ~R$ 0,99
  - Voz ao vivo: ~R$ 1,65
  - **Custo Total de Aquisição (CAC Direto de IA):** **~R$ 2,79 por usuário que testa a Cota completa.**

---

## 3. Sustentabilidade e Prevenção de Abuso

1. **Vínculo por Conta Google / Apple ID:** Cada identidade social possui direito a uma única Cota de Descoberta associada ao seu `id` único.
2. **Rate Limit na Borda e no Gateway:** Limitação de chamadas por minuto para evitar scripts automatizados maliciosos que possam consumir créditos em lote.
3. **Extensão Graciosa:** Concessão discricionária de créditos adicionais a critério do fundador para usuários de alta afinidade comunitária, com custo marginal residual.
