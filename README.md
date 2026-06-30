# KU scRNA-seq Seminar

**건국대학교 이형우 교수님 연구실 온라인 세미나**  
Single-cell RNA-seq 기초부터 고급 분석까지 — Google Colab + Seurat (R)

---

## 데이터셋

**GSE210543** — Human Retina scRNA-seq (Developmental & Adult)

| 샘플 | 그룹 | 세포 수 |
|------|------|--------|
| 16PCW | Young (발달기) | 8,601 |
| 20PCW | Young (발달기) | 5,787 |
| Adult_2 | Old (성체) | 6,516 |
| Adult_3 | Old (성체) | 3,694 |

---

## 세미나 구성

### Part 1 — QC & Preprocessing
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JeonghanSeo/KU-scRNAseq-seminar/blob/main/notebooks/01_QC_and_preprocessing.ipynb)

- 10X Genomics 데이터 구조 이해
- QC 지표 (nFeature, nCount, percent.mt) 이론 및 시각화
- 필터링 기준: `nFeature > 200`, `nCount > 500`, `percent.mt < 10%`
- 정규화 (LogNormalize) 및 고변이 유전자(HVG) 선택

### Part 2 — Integration, Clustering & Annotation
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JeonghanSeo/KU-scRNAseq-seminar/blob/main/notebooks/02_integration_clustering_annotation.ipynb)

- Cell Cycle Scoring (optional regression)
- Harmony Integration (Young vs Old 배치 보정)
- PCA → UMAP 시각화
- Clustering Resolution 비교 (0.2 ~ 0.8)
- FindAllMarkers + 망막 세포 타입 어노테이션

### Part 3 (Advanced) — CellChat & Monocle3 *(준비 중)*

- CellChat: 세포 간 통신 네트워크 분석
- Monocle3: Pseudotime trajectory 분석

---

## 시작하기

1. **Colab 열기**: 위 배지 클릭
2. **Runtime 설정**: Runtime → Change runtime type → **R**
3. **Google Drive 연결**: 노트북 안내에 따라 데이터 경로 설정
4. 셀 순서대로 실행

---

## 참고 자료

- [Seurat 공식 문서](https://satijalab.org/seurat/)
- [GSE210543 on GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE210543)
