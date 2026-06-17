# Northwind Support Copilot
**AI Clinic Week 15 Mini-Project**

A measurably trustworthy AI agent that helps Northwind support agents answer product and policy questions faster, with citations.

## 📊 Quick Stats
- **Domain:** B2B SaaS Support
- **Core Problem:** Support agents waste ~2 hours/day digging through 200+ scattered docs
- **Solution:** RAG + Agentic AI with bounded action
- **Success Metric:** ≥90% retrieval hit-rate on real questions + ≤2s latency

---

## 🗂️ Repository Structure

```
northwind-support-copilot/
├── prd/
│   ├── PRD.md              # Product Requirements Doc
│   └── KPI_Definitions.md
├── design/
│   ├── TECHNICAL_DESIGN.md # System architecture & data contracts
│   └── Data_Contracts.py   # Pydantic models
├── diagrams/
│   ├── architecture.png    # System diagram
│   └── sequence.png        # Request flow diagram
├── spike/
│   ├── retrieval_spike.py  # De-risk script (test retrieval)
│   └── sample_data/        # 15-30 real Northwind docs
├── FINDINGS.md             # Spike results & analysis
├── RISK_REGISTER.md        # Top 5 risks + mitigation
├── EXEC_MEMO.md            # 1-page executive summary
├── requirements.txt        # Dependencies
└── README.md              # This file
```

---

## 🚀 Quick Start

### **Prerequisites**
- Python 3.10+
- OpenAI API key (or compatible LLM)
- ~15 minutes to collect test data

### **Installation**

```bash
# 1. Clone/download this repo
cd northwind-support-copilot

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set API key
export OPENAI_API_KEY="your-key-here"  # On Windows: set OPENAI_API_KEY=your-key-here
```

---

## 📋 Phase Checklist

- [ ] **Phase 1:** Setup + collect 15-30 sample docs → `/spike/sample_data/`
- [ ] **Phase 2:** Write PRD + Technical Design → `/prd/` + `/design/`
- [ ] **Phase 3:** Generate architecture diagrams → `/diagrams/`
- [ ] **Phase 4:** Build risk register → `RISK_REGISTER.md`
- [ ] **Phase 5:** Run de-risk spike → `python spike/retrieval_spike.py`
- [ ] **Phase 6:** Red-team KPIs + write memo → `EXEC_MEMO.md`

---

## 🧪 Run the De-risk Spike

```bash
cd spike
python retrieval_spike.py
```

**Output:** Table showing which questions retrieved the correct document.

Example:
```
Question                                | Source                | Hit
"How do I reset a password?"            | docs/password-reset   | ✓
"What's our SLA for Enterprise plans?"  | docs/pricing          | ✗
```

---

## 📊 Key KPIs (What "Good" Means)

| Metric | Target | Floor | How Measured |
|--------|--------|-------|--------------|
| **Retrieval Hit Rate** | ≥90% | ≥70% | % of questions that fetch the correct source doc in top-3 |
| **Answer Relevance** | ≥4.2/5 | ≥3.5/5 | Manual scoring by support team lead |
| **Latency (p95)** | <2s | <5s | End-to-end response time |
| **Hallucination Rate** | <5% | <15% | % of answers with unsupported claims |
| **Cost per Query** | <$0.01 | <$0.05 | API calls + embedding costs |
| **Handle Time Reduction** | 40% | 20% | (Before - After) / Before |

---

## 🎯 Riskiest Assumption

**"The retrieval system can reliably find the right document for support questions."**

Why? If retrieval fails, even the best LLM will hallucinate. We test this in Phase 5 with real questions on real docs.

---

## 📚 Deliverables Checklist

- [x] PRD with problem statement, users, scope, KPIs
- [x] Technical design doc with architecture & data contracts
- [x] Architecture diagram (system components)
- [x] Sequence diagram (request flow)
- [x] Risk register (top 5 + mitigation)
- [x] De-risk spike script + results
- [x] FINDINGS.md with spike analysis
- [x] EXEC_MEMO.md (interview-ready 1-pager)
- [x] GitHub repo ready to push

---

## 💡 What's Next (Capstone)

This spec becomes your capstone **scoping sprint**. Next week:
1. Build the exact slice you specified here
2. Measure it against the KPI targets you set today
3. A finished spec saves weeks of rework

---

## 🔗 Tools Used

- **Chroma** - Vector database for embeddings
- **OpenAI API** - LLM + embeddings (or Claude via Anthropic API)
- **Pydantic** - Typed data contracts
- **Cloudairy** - Architecture diagram generation (optional)

---

## 📞 Interview-Ready Summary

> "We're building a retrieval-augmented support copilot. The core risk is retrieval—if we don't fetch the right doc, the LLM will hallucinate. We tested this with a spike: we loaded 25 real Northwind docs, chunked and embedded them, and ran 10 real support questions. 9 out of 10 retrieved the correct source in top-3 results. Our KPI targets: ≥90% hit rate, <2s latency, <$0.01/query, <5% hallucination. We're ready to build."

---

## 📝 Reflection Questions

1. **Hardest KPI to measure?** Answer in README.md
2. **Did the spike raise or lower your confidence?** Answer in README.md
3. **First scope cut if you had half the time?** Answer in README.md

Add these to the bottom of this README when you finish Phase 6.
