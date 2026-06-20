# nvdiffrast-Wheel

Custom **nvdiffrast** Wheel für CUDA 13.0 + Blackwell GPU (sm_120).

Optimiert für **HuggingFace ZeroGPU** und **PSHuman** auf Blackwell Hardware.

## 🎯 Specs

| Komponente | Version |
|---|---|
| **Python** | 3.10 |
| **PyTorch** | 2.11.0 + cu130 |
| **CUDA** | 13.0 |
| **GPU Arch** | **12.0 (Blackwell / ONLY)** |
| **nvdiffrast** | latest (konfigurierbar) |

## 🚀 Workflow

Der GitHub Actions Workflow (`build_nvdiffrast_cu130.yml`) baut das Wheel automatisch.

**Manuell triggern:**
1. GitHub → **Actions** → *Build nvdiffrast Wheel (torch 2.11.0 + CUDA 13.0 + Blackwell)*
2. **Run workflow** → Optional: nvdiffrast ref eingeben (Branch/Tag/Commit)
3. **Run** → 20–40 Min. warten

**Release:**
Nach erfolgreichem Build wird ein GitHub Release mit dem Wheel erstellt.
- Tag: `nvdiffrast-torch2.11.0-cu130`
- Artifacts: `nvdiffrast-*-cp310-cp310-linux_x86_64.whl`

## 📦 Installation

Die `.whl`-URL aus dem Release kopieren und in `requirements.txt` eintragen:

```
https://github.com/Painter3000/nvdiffrast_wheel/releases/download/nvdiffrast-torch2.11.0-cu130/nvdiffrast-XXX-cp310-cp310-linux_x86_64.whl
```

Dann wie gewohnt installieren:
```bash
pip install -r requirements.txt
```

## ⚙️ Build-Details

- ✅ `--no-build-isolation` → exakt torch 2.11.0, kein Downgrade
- ✅ `--index-url cu130` → CUDA 13.0 Wheel, nicht CPU
- ✅ `FORCE_CUDA=1` → Kompilierung ohne physische GPU
- ✅ `sm_120` enthalten → Blackwell RTX PRO 6000 unterstützt
- ✅ CUDA 13.0.1 Container → konsistente Build-Umgebung

## 🔗 Verwendung in PSHuman

Ersetze in PSHuman `requirements.txt`:
```diff
- # disabled_blackwell_incompatible: nvdiffrast
+ https://github.com/Painter3000/nvdiffrast_wheel/releases/download/nvdiffrast-torch2.11.0-cu130/nvdiffrast-XXX-cp310-cp310-linux_x86_64.whl
```

---

**Status:** ⏳ Build erfolgreich!

Teil der Blackwell-Kompatibilisierungs-Pipeline für PSHuman.
