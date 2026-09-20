# PLER — Peak Length Error Ratio

**Full-reference metric for geometric quality of 3D meshes**, with topology features and an optional ML perception predictor.

> Author: **Gleb Voronkov** · Non-commercial research license · Commercial use requires written permission.

## Why it matters
Standard mesh distances (Chamfer / Hausdorff) do not always match how humans perceive 3D distortion. PLER combines **center-based ray-casting**, error statistics, and **topological descriptors**, and can train a regressor against subjective scores (MOS).

## Features
- Ray-casting quality score with adaptive ray counts
- Topology analysis (vertices/faces/edges, genus, Euler characteristic)
- ML perception predictor (RandomForest / GBRT / MLP via scikit-learn)
- Cache + parallel casting (repeat runs up to ~1.8–3.7× faster in tests)
- Research / batch modes for degraded mesh series

## Quickstart
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python pler_metric.py models/simple_reference.obj models/simple_distorted.obj
python pler_advanced.py models/simple_reference.obj models/simple_distorted.obj
```

Create tiny demo meshes if needed:
```powershell
python create_test_models.py
```

## Method (short)
1. Load and normalize reference + distorted meshes (Open3D / Trimesh).
2. Cast rays from the model center; compare hit distances.
3. Aggregate MSE / mean / max / skew / kurtosis of ray errors.
4. Optionally enrich with topology scores and predict perceived quality.

## License & commercial use
This repository is released under a **Non-Commercial Research License** (see `LICENSE`).
Personal, educational, and academic research use with attribution is allowed.
**Commercial products/services require a separate license** — contact `mybook3@mail.ru` / Telegram `@Gleb_Voronkov`.

## Related
- Broader multi-metric Streamlit bench: [3d-quality-bench](https://github.com/GlebVoronkov03/3d-quality-bench)
- Related Scopus / RSCI work on XR content assessment and 3D reconstruction error (see `CITATION.cff`)

## Contact
Moscow · `mybook3@mail.ru` · Telegram `@Gleb_Voronkov` · [GitHub](https://github.com/GlebVoronkov03)