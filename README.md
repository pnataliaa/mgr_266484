# Analiza wpływu zakłóceń obrazu na stabilność reprezentacji generowanych przez głębokie sieci neuronowe z uwzględnieniem klas obrazów
# mgr_266484

Repozytorium projektu magisterskiego: analiza odporności klasyfikatorów ImageNet-1k na zaburzenia obrazu (ImageNet-C) na poziomie poszczególnych klas.

## Opis

Praca analizuje pięć wytrenowanych modeli (ResNet-50, ResNet-101, ResNet-152, ViT-B/16, ViT-B/32) na benchmarku ImageNet-C (15 typów zaburzeń × 5 poziomów nasilenia). Celem jest identyfikacja klas konsekwentnie podatnych i odpornych na zaburzenia w różnych architekturach, analiza wpływu typu i intensywności zaburzenia na degradację skuteczności, porównanie CNN vs. ViT, analiza cech statystycznych obrazu jako predyktorów odporności, geometria przestrzeni embeddingów oraz metody XAI (GradCAM++, Attention Rollout).

## Struktura repozytorium

```
mgr_266484/
├── analysis/       # wyniki i skrypty analizy per-class (ranking klas, korelacje, statystyki)
├── baseline/       # ewaluacja bazowa modeli (clean accuracy) na ImageNet-1k
├── corrupted/      # dane / wyniki po zastosowaniu zaburzeń ImageNet-C
├── data/           # pliki danych pomocniczych (m.in. per_image.csv, agg_class_corruption.csv, class_image_features.csv)
├── embeddings/     # zapisane embeddingi warstwy przedostatniej (geometria: compactness, dispersion, margin, drift)
├── figures/        # wygenerowane wykresy do pracy (raincloud, dumbbell, macierze korelacji itd.)
├── hf_cache/       # cache modeli/danych HuggingFace (niewersjonowane - duże pliki)
├── notebooks/      # notebooki Google Colab
│   ├── 04_main_analysis.ipynb        # główna analiza per-class
│   ├── 06_embedding_geometry.ipynb   # geometria embeddingów (compactness, dispersion, margin, boundary_crossing_rate)
│   └── ...                           # XAI (GradCAM++, Attention Rollout), feature instability
├── results/        # zagregowane wyniki końcowe (tabele, metryki modeli)
└── xai/            # analizy wyjaśnialności: GradCAM++, Attention Rollout, tabele IoU
```

## Modele

- ResNet-50, ResNet-101, ResNet-152
- ViT-B/16, ViT-B/32

## Dane

- ImageNet-1k (zbiór walidacyjny, HuggingFace `datasets`)
- ImageNet-C (biblioteka `imagecorruptions`, z własną implementacją `glass_blur` ze względu na niekompatybilność z aktualnym numpy/scikit-image)

## Środowisko

- Google Colab Pro (NVIDIA A100 SXM4 40GB / Tesla T4 15GB)
- Python: PyTorch, torchvision, HuggingFace `datasets`, numpy, pandas, matplotlib, scipy, scikit-image, PIL, nltk, tqdm
- seed=42

## Uwagi

- Duże pliki (cache modeli, surowe dane, wygenerowane obrazy) są wyłączone z repozytorium (patrz `.gitignore`) i przechowywane lokalnie / na Google Drive.

## Autor

Natalia Pyzara, Politechnika Wrocławska
