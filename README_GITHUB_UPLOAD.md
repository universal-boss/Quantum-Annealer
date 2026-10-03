# Quantum Annealer — GitHub Multi-Part Upload Manifest

**Round 50 Audited Baseline**  
All files in this folder are **strictly < 18.00 MB** each and 100% compliant with GitHub's file upload limits. Includes all models, provenance sidecars (.sha256, .meta.json), and tests.

---

## 📦 Package Inventory & Logical Structure

| Part # | Package Name | Size | Contents & Purpose |
|:---:|---|:---:|---|
| **00** | `00_Complete_Source_Code_and_Reports_NO_MODELS.zip` | ~3.8 MB | Complete Python source code, tests, HTML reports, and web dashboard (< 4 MB) |
| **01** | `01_Core_Source_and_Engines.zip` | ~1.8 MB | Complete Python source code (`optimizer.py`, `data_layer.py`, `portfolio_engine.py`, `math_engine/`, `core/`, `data/`, `ml_alpha/`, `workers/`, configs) |
| **02** | `02_Web_Dashboard_and_Workstation.zip` | ~0.3 MB | Web dashboard, TradingView direct workstation engine, full drawing tools, proxy server, and single-CSV export |
| **03** | `03_Audit_Delivery_and_Tests.zip` | ~0.4 MB | Complete test suites (`tests/`), verification scripts (`verify_fixes_r*.py`), and audit reports (`_AUDIT_DELIVERY/`) |
| **04** | `04_CSVs_Databases_and_HTML_Reports.zip` | ~1.4 MB | Universe CSVs, database tables (`qa_db/`), and HTML research reports |
| **05** | `05_Vision_Artifacts_and_Embeddings.zip` | ~10.7 MB | Vision Transformer ONNX model (`vit_v3_fused.onnx`), embeddings, and prototype banks |
| **06** | `06_Archetype_Momentum.zip` | ~11.4 MB | Momentum ML Alpha model + .sha256 sidecar (`models/ml_alpha_momentum.pkl`) |
| **07** | `07_Archetype_Quality.zip` | ~11.4 MB | Quality ML Alpha model + .sha256 sidecar (`models/ml_alpha_quality.pkl`) |
| **08** | `08_Archetype_Defensive.zip` | ~11.4 MB | Defensive ML Alpha model + .sha256 sidecar (`models/ml_alpha_defensive.pkl`) |
| **09** | `09_Archetype_Flow.zip` | ~11.4 MB | Institutional Flow GAT model + .sha256 sidecar (`models/ml_alpha_flow.pkl`) |
| **10** | `10_Archetype_IPO_and_Prebreakout.zip` | ~11.8 MB | IPO model, Pre-breakout model + .sha256 sidecars, and Regime HMM artifact |
| **11** | `11_Feature_Cache_Part1.zip` | ~13.4 MB | Feature Cache Parquets + .meta.json sidecars (Subset 1/4) |
| **12** | `12_Feature_Cache_Part2.zip` | ~14.0 MB | Feature Cache Parquets + .meta.json sidecars (Subset 2/4) |
| **13** | `13_Feature_Cache_Part3.zip` | ~16.9 MB | Feature Cache Parquets + .meta.json sidecars (Subset 3/4) |
| **14** | `14_Feature_Cache_Part4.zip` | ~13.9 MB | Feature Cache Parquets + .meta.json sidecars (Subset 4/4) |
| **15** | `15_DeepAlpha_Model_Part01_of_09.zip` .. `Part09_of_09.zip` | ~13 MB each | DeepAlpha Master Model (`models/ml_alpha_model.pkl`) + .sha256 split across 9 parts |

---

## 🚀 How to Restore the Complete Tree (for GLM or Local Deployment)

To unpack and reconstruct the complete, identical repository:

```bash
# 1. Create target folder and enter it
mkdir -p quantum_annealer && cd quantum_annealer

# 2. Unzip all packages
for f in /path/to/Quantum_Annealer_GitHub_Upload/*.zip; do
    unzip -o "$f"
done

# 3. Reassemble the DeepAlpha Master Model
cat models/ml_alpha_model.pkl.part* > models/ml_alpha_model.pkl
rm -f models/ml_alpha_model.pkl.part*

# 4. Verify integrity
python3 _AUDIT_DELIVERY/verify_fixes_r50.py
python3 _AUDIT_DELIVERY/verify_fixes_r49.py
python3 _AUDIT_DELIVERY/verify_fixes.py
python3 -m pytest tests/test_round50_regressions.py -q 2>/dev/null || true
```
