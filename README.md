# KU scRNA-seq Seminar

**건국대학교 이형우 교수님 연구실 온라인 세미나**
Single-cell RNA-seq 기초 분석 실습 — Google Colab + Seurat (R)

---

## 데이터셋

**GSE210543** — Human Retina scRNA-seq (Developmental & Adult)  
[Cell Ranger Web Summary 파일 →](data/web_summary/)

| 샘플 | 그룹 | Est. Cells | Mean Reads/Cell | Median Genes/Cell | 분석 |
|------|------|----------:|----------------:|------------------:|:----:|
| **16PCW** | Young | **8,601** | 43,243 | 1,084 | ✅ |
| **20PCW** | Young | **5,787** | 103,036 | 5,174 | ✅ |
| 12PCW | Young | 3,637 | 164,166 | 4,596 | — |
| 21PCW | Young | 3,948 | 139,139 | 1,953 | — |
| **Adult_2** | Old | **6,516** | 90,897 | 2,016 | ✅ |
| **Adult_3** | Old | **3,694** | 142,303 | 2,806 | ✅ |
| Adult_5 | Old | 3,487 | 168,631 | 2,529 | — |
| Adult_1 | Old | 884 | 412,206 | 2,807 | ❌ |
| Adult_4 | Old | 496 | 1,146,570 | 2,414 | ❌ |
| AMD_macula | AMD | 1,719 | 284,749 | 4,002 | — |
| AMD_peripheral | AMD | 1,794 | 267,813 | 3,584 | — |
| Unaffected_macula | Control | 3,557 | 101,143 | 5,102 | — |
| Unaffected_peripheral | Control | 3,527 | 112,731 | 4,765 | — |

> ✅ 세미나 분석 샘플 (Young 2 + Old 2) | ❌ 세포 수 부족 또는 품질 이슈

`data/filtered_feature_bc_matrix/`에 13개 샘플의 raw 10X 데이터(barcodes.tsv.gz, features.tsv.gz, matrix.mtx.gz)가 모두 포함되어 있습니다.

### 데이터 다운로드

**방법 1 — Git으로 전체 클론 (권장)**
```bash
git clone https://github.com/JeonghanSeo/KU-scRNAseq-seminar.git
```

**방법 2 — Git 없이 전체 다운로드 (Windows)**
1. 저장소 메인 페이지 상단의 초록색 **Code** 버튼 클릭
2. **Download ZIP** 클릭 → `KU-scRNAseq-seminar-main.zip` 다운로드
3. 압축 해제 후 `data/filtered_feature_bc_matrix/` 폴더에서 필요한 샘플 사용

**방법 3 — 필요한 샘플 폴더만 다운로드**
- 개별 파일: 저장소에서 `data/filtered_feature_bc_matrix/<샘플명>/` 폴더로 들어가 각 파일(barcodes.tsv.gz, features.tsv.gz, matrix.mtx.gz) 클릭 → 우측 상단 **Download raw file** 버튼
- 폴더 전체를 zip으로 받고 싶다면 [download-directory.github.io](https://download-directory.github.io/) 같은 서드파티 툴에 해당 폴더 URL(예: `https://github.com/JeonghanSeo/KU-scRNAseq-seminar/tree/main/data/filtered_feature_bc_matrix/16PCW`)을 붙여넣으면 그 샘플만 zip으로 받을 수 있습니다.

---

## 세미나 구성

### 메인 실습 노트북 — QC부터 Cell Type Annotation까지 (3시간)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JeonghanSeo/KU-scRNAseq-seminar/blob/main/notebooks/01_scRNAseq_full.ipynb)

| Step | 내용 | 시간 |
|------|------|------|
| 0 | 환경 설정 (패키지 1회 설치) | 10분 |
| 1 | 10X 데이터 불러오기 | 10분 |
| 2 | QC 이론 + 시각화 (nFeature / nCount / percent.mt) | 30분 |
| 3 | QC 필터링 (`nFeature > 200`, `nCount > 500`, `mt < 10%`) | 10분 |
| 4 | 정규화 — LogNormalize | 10분 |
| 5 | HVG 선택 | 5분 |
| — | **중간 체크포인트 저장** | — |
| 6 | Cell Cycle Scoring (optional) | 5분 |
| 7 | Scaling + PCA | 10분 |
| 8 | Integration — Harmony (Young vs Old) | 10분 |
| 9 | UMAP | 10분 |
| 10 | Clustering (Resolution sweep) | 15분 |
| 11 | FindAllMarkers | 15분 |
| 12 | Cell Type Annotation (망막 마커 기반) | 20분 |

### Advanced — CellChat & Monocle3 *(시간 여유 시)*

- CellChat: 세포 간 통신 네트워크 분석
- Monocle3: Pseudotime trajectory 분석 (Young → Old 발달 축)

---

## 시작하기

1. 위 Colab 배지 클릭
2. Runtime → Change runtime type → **R**
3. Google Drive 연결 후 데이터 경로 설정
4. Step 0부터 순서대로 실행

> 세션이 끊기면 Step 0 (라이브러리 로드) 후 중간 체크포인트 셀에서 재개 가능

---

## 참고 자료

- [Seurat 공식 문서](https://satijalab.org/seurat/)
- [Harmony](https://github.com/immunogenomics/harmony)
- [GSE210543 on GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE210543)
- [DoubletFinder (McGinnis et al., Cell Systems 2019)](https://doi.org/10.1016/j.cels.2019.03.003) — 노트북 Step 2에서 원리만 설명, 실행은 생략
