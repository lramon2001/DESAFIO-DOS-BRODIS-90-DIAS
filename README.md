# 🐀 Desafio dos Brodis — 90D

Um placar **estático** (HTML + CSS + JS) para acompanhar um desafio de 90 dias com:

- **70% Assiduidade** (check-ins / feitos vs meta)
- **30% Performance** (melhora percentual em exercícios)
- **Cálculo automático** na tabela
- **Salvamento automático no navegador** via `localStorage` (não perde ao atualizar/fechar)
- **Exportação de backup** em JSON

> Visual dark + “sports brand vibe” , com líder destacado automaticamente.

---

## ✅ Regras (resumo)

- ❌ Não vale caminhada (mesmo que gaste 200 cal)
- ❌ Não vale alongamento/aquecimento como treino
- ❌ Não pode chamar mais camaradas (bonde fechado)
- ⚠️ Bom senso: nada de treino migué (esteira no modo passeio, bike ergométrica mole, elíptico no conforto etc.)

---

## 📊 Métricas avaliadas

- 🏃 **Corrida 1km** (pace em `m:ss`) — **peso 2**
- 💪 **Flexões** (reps sem pausa) — **peso 1**
- 🦍 **Barra fixa** (reps) — **peso 2**
- 🔥 **Abdominais** (reps) — **peso 1**

### Cálculo da melhora percentual

**Repetições**  
`Melhora(%) = ((final - inicial) / inicial) × 100`  
Se `inicial = 0`, usamos **1** como base (pra não quebrar o cálculo).

**Corrida (pace)**  
`Melhora(%) = ((pace_inicial - pace_final) / pace_inicial) × 100`  
> O pace é convertido para **segundos** antes do cálculo.

### Cap de melhora

- Melhorias positivas são limitadas a **+100% por exercício**
- Regressão (piorou) continua valendo (pode ficar negativo)

---

## 🧮 Pontuação

- Cada exercício gera pontos com: `melhora% × peso`
- Total máximo de pontos de performance = **600**  
  (Corrida 200 + Barra 200 + Flex 100 + Abd 100)
- Performance final exibida em **0–100**: `perf100 = (pontos/600)×100`
- **Score Final**: `0.7×assiduidade% + 0.3×perf100`

---

## 🚀 Como rodar

### Opção 1 — abrir direto
Abra o arquivo no navegador:

- `index_localstorage.html`

### Opção 2 — servidor local (recomendado)
Evita alguns bloqueios de browser e fica mais parecido com produção:

**Python**
```bash
python -m http.server 8080
```
Depois acesse:
- http://localhost:8080/

---

## 💾 Salvamento no navegador (localStorage)

O app salva automaticamente tudo no seu navegador usando a chave:

- `brodis90d_v1`

### Botões
- **Resetar**: limpa inputs e apaga o `localStorage`
- **Exportar JSON**: baixa um arquivo com os dados salvos (backup)

⚠️ Importante: `localStorage` é **por dispositivo e por navegador**.  
Se abrir no celular e no PC, serão dados diferentes (a menos que você exporte/importa).

---

## 🌐 Deploy no GitHub Pages

Este repo funciona bem no GitHub Pages (site estático).  
Se você já tem o workflow em `.github/workflows/pages.yml`, é só dar push na `main` e configurar:

`Settings → Pages → Source: GitHub Actions`

---

## 📁 Estrutura sugerida do repo

```
/
├─ index_localstorage.html
├─ index.html (opcional)
└─ .github/
   └─ workflows/
      └─ pages.yml
```

---

## 🧱 Próximos upgrades (ideias)

- Importar JSON (restaurar backup / “sincronizar” manualmente)
- PWA instalável (ícone no iPhone/Android, modo app)
- Exportar CSV
- Modo telão / ranking animado

