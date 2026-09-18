# Windowed Variational Mode Decomposition with Gaussian-Kernel Mode Selection for Sex-Stratified Speech-Based Depression Screening

Code and analysis notebooks accompanying the paper *"Windowed Variational Mode Decomposition with Gaussian-Kernel Mode Selection for Sex-Stratified Speech-Based Depression Screening"* (Xavier Sánchez Corrales, Luyao Sun, Hao Jia, and Jordi Solé-Casals; submitted to *Computer Methods and Programs in Biomedicine*).

This repository contains the windowed Variational Mode Decomposition (VMD) pipeline, Gaussian-kernel-based mode selection, sex-stratified feature aggregation, and classification/validation code used to distinguish depressed from healthy speech in the DAIC-WOZ corpus. Speech is first split into discontinuity-aware chunks (bounded by speaker turns and by silences above a fixed duration threshold) and windowed independently within each chunk, so that temporal-dynamics features are never computed across an artificial splice in the recording.

## Data Availability

**The audio data and clinical metadata are not included in this repository.** The DAIC-WOZ corpus (*Distress Analysis Interview Corpus – Wizard of Oz*) is protected and distributed under a data use agreement by the **University of Southern California (USC), Institute for Creative Technologies**. Access must be requested directly from USC ICT: <https://dcapswoz.ict.usc.edu/>.

No participant audio, transcripts, or PHQ-8 scores are redistributed here or in any other public location associated with this project.

## Reproducing the Experiments

To replicate the results reported in the paper:

1. Request and download the DAIC-WOZ corpus directly from USC ICT (see above).
2. Run the generic segmentation notebook to produce, for each subject, a discontinuity-aware windows array and a window-level metadata table (including chunk boundaries) at each of the three window lengths evaluated in the paper (0.5 s, 1 s, 2 s). This notebook is not tied to a specific sex or window length; it processes all combinations in a single run.
3. Run the generic experimentation notebook to perform the windowed VMD decomposition, Gaussian-kernel mode selection, feature aggregation, classification, threshold calibration, leakage-free architecture selection, and the winner's-curse bias-control experiments, following exactly the procedure and hyperparameters described in Section 2 of the manuscript. Unlike the segmentation notebook, this one must be adapted to each sex and window-length combination separately (six runs in total: FEMALE/MALE x 0.5 s/1 s/2 s), by editing the configuration cell at the top of the notebook.

**References:**

> Sánchez Corrales, X., Sun, L., & Solé-Casals, J. (submitted). *Windowed Variational Mode Decomposition with Gaussian-Kernel Mode Selection for Sex-Stratified Speech-Based Depression Screening.* Computer Methods and Programs in Biomedicine.

Related, previously published work from the same research line (EMD-based analysis of the same corpus, precursor to the windowed VMD pipeline used here):

> Sánchez Corrales, X., Solé-Casals, J., Arroyo García, E., & Palao Vidal, D. (2025). *Analyzing Male Depression Using Empirical Mode Decomposition.* In Proceedings of the 18th International Joint Conference on Biomedical Engineering Systems and Technologies (BIOSIGNALS), pp. 886–892. SciTePress. DOI: [10.5220/0013157600003911](https://doi.org/10.5220/0013157600003911)

> Sánchez Corrales, X., & Solé-Casals, J. (2025). *Feature extraction from speech signals using empirical mode decomposition for depression detection: A comparative study with machine learning models.* Computer Speech & Language. DOI: [10.1016/j.csl.2025.101898](https://doi.org/10.1016/j.csl.2025.101898)

## Usage Restrictions

The code and notebooks in this repository are provided **for academic and research purposes only**. Commercial use, including incorporation into commercial products or services, is **not permitted** without prior written consent from the authors.

## Authors

**Xavier Sánchez Corrales** (Corresponding author)
Data and Signal Processing Research Group, University of Vic – Central University of Catalonia (UVic-UCC), Vic, Spain
xavier.sanchez.corrales@uvic.cat
ORCID: [0009-0002-4335-6851](https://orcid.org/0009-0002-4335-6851)

**Luyao Sun**
School of Data Science, The Chinese University of Hong Kong, Shenzhen, China; Smart Healthcare Digital Joint Laboratory, Nankai University, Tianjin, China
luyaosun@link.cuhk.edu.cn
ORCID: [0009-0008-0323-5709](https://orcid.org/0009-0008-0323-5709)

**Hao Jia**
School of Medicine, Nankai University, Tianjin, China; Tianjin Key Laboratory of Interventional Brain-Computer Interface and Intelligent Rehabilitation, Nankai University, Tianjin, China; Smart Healthcare Digital Joint Laboratory, Nankai University, Tianjin, China
haojia@nankai.edu.cn
ORCID: [0000-0003-1356-7463](https://orcid.org/0000-0003-1356-7463)

**Jordi Solé-Casals**
Data and Signal Processing Research Group, University of Vic – Central University of Catalonia (UVic-UCC), Vic, Spain; Department of Psychiatry, University of Cambridge, Cambridge, United Kingdom
jordi.sole@uvic.cat
ORCID: [0000-0002-6534-1979](https://orcid.org/0000-0002-6534-1979)
