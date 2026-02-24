# ImageNet Class Splits for Open-Set Recognition

This repository provides class splits of the ImageNet dataset for **Open-Set Recognition (OSR)** tasks. The 1000 classes of ImageNet-1K are divided into three semantic subsets (Animal, Object, Other). Each subset is further split into **ID (known classes)** and **OOD (unknown classes)** for training and evaluating OSR models.

## Directory Structure

```
imagenet_animial_split/
├── imagenet_animal_id_classes.txt      # Animal - ID (known classes)
├── imagenet_animal_ood_classes.txt    # Animal - OOD (unknown classes)
├── imagenet_object_id_classes.txt      # Vehicles & indoor objects - ID
├── imagenet_object_ood_classes.txt    # Vehicles & indoor objects - OOD
├── imagenet_other_id_classes.txt       # Other categories - ID
├── imagenet_other_ood_classes.txt     # Other categories - OOD
└── README.md
```

## Split Overview

| Subset | ID Classes | OOD Classes | Description |
|--------|------------|-------------|-------------|
| **Animal** | 236 | 162 | Animal-related classes (fish, birds, reptiles, etc.) |
| **Object** | 118 | 85 | Vehicles and indoor objects (cars, instruments, furniture, etc.) |
| **Other** | 237 | 162 | Other categories (clothing, architecture, daily objects, etc.) |

- **ID (In-Distribution)**: Known classes during training and testing; the model is required to classify them correctly.
- **OOD (Out-of-Distribution)**: Unknown classes during testing; the model should recognize them as "unknown".

## File Format

Each `.txt` file follows this format:

```
# Comment lines (starting with #)
# Total: N classes
# Format: class_id  class_name

n01440764	tench
n01443537	goldfish
n01484850	great white shark
...
```

- **class_id**: ImageNet/WordNet class ID (e.g., `n01440764`)
- **class_name**: Class name in English
- Fields are separated by **Tab**

## Usage Example

```python
# Load ID classes
with open('imagenet_animal_id_classes.txt') as f:
    for line in f:
        if line.startswith('#'):
            continue
        class_id, class_name = line.strip().split('\t')
        # class_id: n01440764, class_name: tench

# Or specify class_list_file when using PyTorch Dataset
# dataset = ImageNetDataset(..., class_list_file='imagenet_animal_id_classes.txt')
```

## Dependencies

- **ImageNet-1K** dataset (ILSVRC2012)
- Class IDs are consistent with the [official ImageNet mapping](https://github.com/tensorflow/models/blob/master/research/slim/datasets/imagenet_2012_validation_synset_labels.txt)

## Citation

If you use these splits, please cite this repository.

## License

These split files are free to use. The ImageNet dataset itself is subject to its official terms of use.
