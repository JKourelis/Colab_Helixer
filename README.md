# Helixer: Unofficial Google Colab Interface

<div align="center">
  <img src="https://raw.githubusercontent.com/weberlab-hhu/Helixer/main/img/helixer.svg" height="200" alt="Helixer Logo">
</div>

<div align="center">

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Jm2TLn2eZ1Dkctyb4EvUYE0b39O2UQNC?usp=sharing)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Paper](https://img.shields.io/badge/bioRxiv-2023.02.06.527280-red.svg)](https://doi.org/10.1101/2023.02.06.527280)
[![Original Paper](https://img.shields.io/badge/Bioinformatics-btaa1044-blue.svg)](https://doi.org/10.1093/bioinformatics/btaa1044)

</div>

## Overview

This Google Colab notebook provides an easy-to-use interface for **Helixer**, a deep learning tool for *ab initio* gene structure prediction developed by Weber et al. This implementation makes Helixer accessible through a step-by-step notebook interface with intelligent parameter optimization and comprehensive result handling.

**🚀 [Click here to open the Helixer Colab notebook](https://colab.research.google.com/drive/1Jm2TLn2eZ1Dkctyb4EvUYE0b39O2UQNC?usp=sharing)**

> **Note**: This is an unofficial Google Colab implementation. All credit for the Helixer model, methodology, and scientific contributions goes to the original authors. This notebook simply provides a convenient interface for running their published tool.

## Key Features of This Interface

- **🧬 Access to Helixer**: Easy access to deep learning gene annotation for eukaryotic genomes
- **🎯 Intelligent Parameter Optimization**: Automatic parameter selection based on assembly quality and lineage
- **📊 Assembly Quality Assessment**: Comprehensive N50/N90 analysis with quality-based recommendations
- **☁️ Google Drive Integration**: Automatic upload of results with organized folder structure
- **📋 Multiple Output Formats**: Standard GFF3, Geneious-compatible GFF3, and extracted sequences
- **🔧 Advanced Configuration**: Full control over prediction parameters for specialized applications
- **📱 User-Friendly**: Clean step-by-step interface with detailed progress tracking

## Supported Lineages and Models

### Available Models
- **🍄 Fungi**: Optimized for fungal genomes
- **🌱 Land Plants**: For terrestrial plant species
- **🐟 Vertebrates**: Mammalian, fish, and other vertebrate genomes
- **🐛 Invertebrates**: Arthropods, nematodes, and other invertebrates

### Assembly Quality Guidelines
The interface automatically optimizes parameters based on your assembly quality:

- **🏆 Excellent (N50 > 1 Mb)**: Chromosome-level assemblies - uses aggressive settings for maximum speed (up to 5x faster)
- **🥈 Good (N50 100kb-1Mb)**: Scaffold-level assemblies - uses standard optimized settings (2-3x faster)
- **🥉 Fair (N50 10-100kb)**: Contig-level assemblies - uses conservative settings for reliability
- **⚠️ Poor (N50 < 10kb)**: Highly fragmented - uses minimal safe settings

## Input Methods

### 1. Google Drive Path
Access files directly from your Google Drive:
- Navigate through folder structures
- Support for compressed files (`.gz`, `.zip`, `.bz2`)
- Automatic file validation

### 2. File Upload
Upload genome files directly to Colab:
- Drag-and-drop interface
- Real-time compression detection
- Format validation

## Configuration Options

### Intelligent Parameter Modes

- **Auto-Optimized** *(Recommended)*: Automatically selects the best parameters based on your assembly quality and lineage. Provides optimal speed while maintaining safety.

- **Conservative**: Uses safe parameters that work for any assembly quality. Slower but guaranteed to work.

- **Manual**: Full control over all parameters for advanced users.

### Key Parameters

- **Peak Threshold** (0.1-1.0): Minimum genic score to accept gene candidates
  - `0.6`: High sensitivity for effector annotation
  - `0.8`: Standard balanced annotation
  - `0.9-0.95`: High precision, fewer false positives

- **Subsequence Length**: How much genome the neural network processes at once
  - Automatically optimized based on assembly N50
  - Larger values = faster processing for good assemblies
  - Must be shorter than 50% of assembly N50

- **Batch Size**: Number of sequences processed simultaneously
  - Auto-selected based on GPU memory
  - Larger values = faster processing

### Advanced Features

- **Assembly Statistics**: Comprehensive genome quality assessment including N50/N90, GC content, and gap analysis
- **Overlap Processing**: Improved accuracy at sequence boundaries (recommended for final annotations)
- **Phase Prediction**: CDS reading frame prediction for complete gene models
- **Custom Thresholds**: Fine-tune sensitivity vs precision for specific applications

## System Requirements

- **Platform**: Google Colab with GPU runtime
- **Memory**: A100 GPU strongly recommended for large genomes
- **Runtime**: Works with T4, V100, or A100 GPUs (A100 preferred for complex assemblies)
- **File Size**: Maximum 1 GB genome files, minimum 25 kbp sequences
- **Internet**: Required for model downloads and Google Drive integration

## Workflow

1. **Installation**: Automated setup of Helixer, dependencies, and HelixerPost processor
2. **File Input**: Choose Google Drive path or upload file directly
3. **Assembly Analysis**: Automatic quality assessment and parameter recommendations
4. **Configuration**: Set lineage model and optimization mode
5. **Model Download**: Automatic download of appropriate lineage model
6. **Prediction**: Complete pipeline execution with progress monitoring
7. **Results**: Comprehensive output package with multiple file formats

## Output Files

Each annotation generates:
- **Standard GFF3**: Compatible with most bioinformatics tools
- **Geneious-compatible GFF3**: Optimized for genome visualization software
- **Protein sequences**: For BUSCO validation and functional annotation
- **Transcript sequences**: For RNA-seq analysis and expression studies
- **CDS sequences**: For phylogenetic analysis and codon usage
- **Gene sequences**: For promoter analysis and regulatory studies
- **Comprehensive statistics**: Detailed annotation metrics and assembly analysis
- **Results archive**: ZIP package containing all outputs and documentation

## Performance Expectations

### Speed Improvements by Assembly Quality
- **Excellent assemblies**: 1.5-5x faster than baseline settings
- **Good assemblies**: 1.7-3x faster with optimized parameters
- **Fair assemblies**: 1-2x faster with conservative settings
- **Poor assemblies**: Baseline speed with maximum safety

### Annotation Quality (BUSCO expectations)
- **Excellent assemblies**: >95% complete gene models
- **Good assemblies**: 90-95% complete gene models
- **Fair assemblies**: 85-90% complete gene models
- **Poor assemblies**: <85% (limited by assembly quality)

## Citation

If you use this notebook in your research, please cite the Helixer papers:

**Helixer—de novo Prediction of Primary Eukaryotic Gene Models**  
Holst, F., Bolger, A., Günther, C., Maß, J., Triesch, S., Kindel, F., Kiel, N., Saadat, N., Ebenhöh, O., Usadel, B., Schwacke, R., Bolger, M., Weber, A.P.M., & Denton, A.K. (2023)  
*bioRxiv* [https://doi.org/10.1101/2023.02.06.527280](https://doi.org/10.1101/2023.02.06.527280)

**Helixer: Cross-species gene annotation of large eukaryotic genomes using deep learning**  
Stiehler, F., Steinborn, M., Scholz, S., Dey, D., Weber, A.P.M., & Denton, A.K. (2020)  
*Bioinformatics* [https://doi.org/10.1093/bioinformatics/btaa1044](https://doi.org/10.1093/bioinformatics/btaa1044)

<details>
<summary>BibTeX format</summary>

```bibtex
@article{holst2023helixer,
    title={Helixer—de novo Prediction of Primary Eukaryotic Gene Models},
    author={Holst, Felix and Bolger, Anthony and Günther, Christopher and Maß, Janina and Triesch, Sebastian and Kindel, Felicitas and Kiel, Niklas and Saadat, Nima and others},
    journal={bioRxiv},
    year={2023},
    doi={10.1101/2023.02.06.527280}
}

@article{stiehler2020helixer,
    title={Helixer: Cross-species gene annotation of large eukaryotic genomes using deep learning},
    author={Stiehler, Felix and Steinborn, Marvin and Scholz, Stephan and Dey, Daniela and Weber, Andreas PM and Denton, Alisandra K},
    journal={Bioinformatics},
    volume={37},
    number={6},
    pages={793--799},
    year={2021},
    doi={10.1093/bioinformatics/btaa1044}
}
```

</details>

## Troubleshooting

**Common Issues:**

- **GPU Memory**: Reduce batch size or use smaller subsequence lengths for large genomes
- **Poor Predictions**: Verify correct lineage model selection and check assembly quality
- **Slow Performance**: Use Auto-Optimized mode and ensure A100 GPU selection
- **File Errors**: Verify FASTA format and check for compressed file support

**Parameter Guidelines:**
- Always use **Auto-Optimized mode** for best results
- **Conservative mode** for problematic assemblies
- **Manual mode** only for advanced users with specific requirements
- Subsequence length should be < 50% of assembly N50

## Disclaimer

This Google Colab notebook is an independent implementation created to make Helixer more accessible. All scientific credit, model development, and methodological contributions belong to the original Helixer team. This notebook serves purely as a user interface wrapper around their published work and does not represent any original research or model development.

For the official Helixer implementation and latest updates, please visit the [official Helixer repository](https://github.com/weberlab-hhu/Helixer).

## License

This Colab interface implementation is released under the MIT License. Helixer itself is governed by its own license terms - please refer to the [official Helixer repository](https://github.com/weberlab-hhu/Helixer) for model licensing information.

## Related Resources

- [Official Helixer Repository](https://github.com/weberlab-hhu/Helixer)
- [Helixer Paper (2023)](https://doi.org/10.1101/2023.02.06.527280)
- [Original Helixer Paper (2020)](https://doi.org/10.1093/bioinformatics/btaa1044)
- [BUSCO Gene Set Validation](https://busco.ezlab.org/)

---

**Author**: Jiorgos Kourelis  
**Last Updated**: July 23, 2025