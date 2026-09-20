# PLER — Peak Length Error Ratio

**Full-reference metric for geometric quality of 3D meshes**, with topology features and an optional ML perception predictor.

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Non--Commercial-orange)](LICENSE)
[![Portfolio](https://img.shields.io/badge/Portfolio-project%20page-3a6b8c)](https://glebvoronkov03.github.io/gleb-web-portfolio/projects/pler.html)

> Author: **Gleb Voronkov** · Non-commercial research license · Commercial use requires written permission.

## Demo

![PLER comparison](assets/pler-comparison.png)

<p align="center"><img src="assets/pler-convergence.png" alt="PLER convergence" width="70%" /></p>

## Why it matters
Standard mesh distances (Chamfer / Hausdorff) do not always match how humans perceive 3D distortion. PLER combines **center-based ray-casting**, error statistics, and **topological descriptors**, and can train a regressor against subjective scores (MOS).

## Architecture

![PLER architecture](assets/pler-architecture.png)

```mermaid
flowchart LR
  Ref[Reference mesh] --> Norm[Normalize]
  Dist[Distorted mesh] --> Norm
  Norm --> Rays[Center ray-casting]
  Rays --> Stats[Error statistics]
  Norm --> Topo[Topology features]
  Stats --> Score[PLER score]
  Topo --> Score
  Score --> ML[Optional MOS regressor]
```

## Quickstart
```powershell
python -m venv .venv
# Windows: .\.venv\Scripts\Activate.ps1
# Linux/macOS: source .venv/bin/activate
pip install -r requirements.txt
python pler_metric.py models/simple_reference.obj models/simple_distorted.obj
python pler_advanced.py models/simple_reference.obj models/simple_distorted.obj
```

Create tiny demo meshes if needed: `python create_test_models.py`

## Results
- Cache acceleration up to **~1.8–3.7×** on repeat runs (local tests)
- Open3D / Trimesh pipeline with research batch modes for degraded mesh series
- Cross-validated against classic geometric metrics in [3d-quality-bench](https://github.com/GlebVoronkov03/3d-quality-bench)

## License & citation
**Non-Commercial Research License** (`LICENSE`). Personal / academic use with attribution OK.  
Commercial products/services → `mybook3@mail.ru` / Telegram `@Gleb_Voronkov`.  
See `CITATION.cff` for bibliographic metadata.

## Links
- Portfolio: [https://glebvoronkov03.github.io/gleb-web-portfolio/projects/pler.html](https://glebvoronkov03.github.io/gleb-web-portfolio/projects/pler.html)
- Related: [3d-quality-bench](https://github.com/GlebVoronkov03/3d-quality-bench)
- Contact: Moscow · `mybook3@mail.ru` · [@Gleb_Voronkov](https://t.me/Gleb_Voronkov)
