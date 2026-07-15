# Analiza wpływu zakłóceń obrazu na stabilność reprezentacji generowanych przez głębokie sieci neuronowe z uwzględnieniem klas obrazów

Repozytorium projektu magisterskiego: analiza odporności klasyfikatorów ImageNet-1k na zaburzenia obrazu (ImageNet-C) na poziomie poszczególnych klas.

## Opis

Praca analizuje pięć wytrenowanych modeli (ResNet-50, ResNet-101, ResNet-152, ViT-B/16, ViT-B/32) na benchmarku ImageNet-C (15 typów zaburzeń × 5 poziomów nasilenia). Celem jest identyfikacja klas konsekwentnie podatnych i odpornych na zaburzenia w różnych architekturach, analiza wpływu typu i intensywności zaburzenia na degradację skuteczności, porównanie CNN vs. ViT, oraz zastosowanie cech statystycznych obrazu i metod XAI (GradCAM++, Attention Rollout) do wyjaśnienia obserwowanych zjawisk.

## Struktura repozytorium

- `analysis/` - wyniki i skrypty analizy per-class
- `baseline/` - ewaluacja bazowa modeli (clean accuracy)
- `notebooks/` - notebooki Google Colab (główna analiza, geometria embeddingów, XAI)
- `xai/` – analizy GradCAM++ i Attention Rollout

## Modele

- ResNet-50, ResNet-101, ResNet-152
- ViT-B/16, ViT-B/32

## Dane

- ImageNet-1k (walidacyjny zbiór, HuggingFace `datasets`)
- ImageNet-C (biblioteka `imagecorruptions`, z własną implementacją `glass_blur`)

## Środowisko

- Google Colab Pro (NVIDIA A100 / Tesla T4)
- Python, PyTorch, torchvision, HuggingFace `datasets`, numpy, pandas, matplotlib, scipy, scikit-image, nltk

## Autor

Natalia Pyzara, Politechnika Wrocławska
