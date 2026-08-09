# Skin Cancer Classifier 🔬

A deep-learning image classifier that distinguishes **benign vs. malignant** skin lesions from dermatoscopic images, built with fast.ai.

> ⚠️ **Educational demo only — not a diagnostic tool.** This is a learning project, not validated for clinical use. Always consult a dermatologist for any real skin concern.

## The Problem
Early detection of malignant skin lesions saves lives. In a screening context the two error types are not equal: a **false negative** (missing a real cancer) is far more costly than a **false positive** (flagging a harmless mole). So this project treats **recall on malignant lesions** — not overall accuracy — as the metric that matters.

## The Data
- Dataset: `fanconic/skin-cancer-malignant-vs-benign` (Kaggle)
- ~3,600 dermatoscopic images, two classes (benign / malignant), pre-split into train/test folders.

## Approach
- Framework: fast.ai (PyTorch under the hood)
- Model: ResNet18, pretrained on ImageNet, fine-tuned for 3 epochs (transfer learning)

## Results
- **Accuracy: ~88%**
- **Malignant recall: 87%** ← the headline metric (catches 87% of cancers)
- See `confusion_matrix.png`. Of 660 test images: 39 malignant lesions missed (false negatives), 42 benign flagged (false positives).
- Reviewing the model's most confident errors (`plot_top_losses`) showed they cluster around **occluding hairs, low contrast, and ambiguous coloring**.

## Limitations & Next Steps
Small dataset, binary only, not clinically validated. Next: multi-class (7-type) lesion classification and better handling of hair-occluded images.

## Tech Stack
fast.ai · PyTorch · ResNet18 · Google Colab
