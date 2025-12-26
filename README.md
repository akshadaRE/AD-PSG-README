# **Polysomnographic Markers of Slow-Wave Sleep Alteration in Alzheimer’s Disease**
# **Introduction**
Alzheimer’s disease (AD) represents a growing global health burden, with prevalence increasing rapidly due to population aging. In the United States alone, an estimated 6.9 million individuals aged 65 years and older currently live with Alzheimer’s dementia, a figure projected to rise to approximately 13.8 million by 2060 in the absence of effective disease-modifying therapies. Despite advances in symptomatic management, early diagnosis and mechanistic understanding of AD remain critical challenges.
Recent years have seen substantial progress in the application of machine learning–based approaches for early AD detection, particularly using neuroimaging modalities such as MRI and PET. These methods have demonstrated that subtle physiological and structural changes can be leveraged for early disease characterization. In contrast, polysomnography (PSG) remains comparatively underutilized in AD research, despite growing evidence linking sleep disruption, especially slow-wave sleep (SWS), to amyloid clearance, synaptic homeostasis, and neuroinflammatory regulation.
Notably, a recent systematic review identified 28 studies investigating PSG-derived sleep parameters in Alzheimer’s disease, of which 24 were suitable for meta-analytic synthesis, highlighting both the relevance of sleep physiology in AD and the relative scarcity of large-scale, integrative analytical approaches. This gap suggests an opportunity to apply modern computational and analytical frameworks, analogous to those used in neuroimaging, to PSG data in order to better characterize sleep microarchitecture alterations associated with AD.
In this study, we focus on slow-wave sleep (SWS) and its electrophysiological features in Alzheimer’s disease, comparing PSG-derived metrics between AD patients and cognitively normal controls using publicly available datasets. ***By combining sleep neurophysiology with data-driven analysis, this work aims to contribute to a more comprehensive understanding of sleep-related biomarkers in Alzheimer’s disease.***

# **Methods**
### *Datasets*
This study will utilize publicly available polysomnography (PSG) datasets to characterize slow-wave sleep (SWS) features relevant to Alzheimer’s disease. Pipeline development and initial validation will be conducted using the Sleep-EDF Expanded dataset, which provides overnight PSG recordings with EEG, EOG, and EMG channels alongside standardized sleep stage annotations. Sleep-EDF will be selected due to its unrestricted access, standardized acquisition protocols, and widespread use in sleep research.
Following validation, the analytical framework will be extended to larger population-based cohorts available through the National Sleep Research Resource (NSSR), such as SHHS, MrOS, and MESA Sleep. These datasets will enable evaluation of the generalizability of SWS-related findings across broader populations relevant to Alzheimer’s disease risk.

### *Signal Preprocessing*
Raw PSG signals will be harmonized across datasets by standardizing channel labels, referencing schemes, and sampling frequencies. EEG data will be resampled to a common frequency (200–256 Hz) to ensure comparability. Signals will be band-pass filtered between 0.3 and 40 Hz, and notch filtering at 50 or 60 Hz will be applied to remove line noise.
Artifact-contaminated epochs will be identified and excluded using automated amplitude- and variance-based thresholds. EOG and EMG channels will be used to assist in detecting ocular and muscle artifacts. When necessary, Independent Component Analysis (ICA) may be applied to further reduce residual non-neural signal contamination

### *Sleep Staging and SWS Identification*
Sleep will be segmented into 30-second epochs in accordance with AASM guidelines. Where available, manually scored sleep stage annotations will be used. Otherwise, validated automated sleep staging algorithms will be applied and cross-checked for consistency.
Slow-wave sleep (SWS; N3) epochs will be identified based on standard AASM criteria, characterized by high-amplitude delta activity in the 0.5–2 Hz range occupying at least 20% of the epoch. To confirm stage validity, delta power density will be compared across NREM stages, ensuring physiological consistency of identified SWS epochs.

### *SWS Macroarchitecture*
Macrostructural characteristics of SWS will be quantified, including total SWS duration, percentage of total sleep time spent in SWS, latency to first SWS episode, number of SWS bouts, and mean bout duration. These measures will be selected due to their established sensitivity to aging and neurodegenerative processes.

### *SWS Microarchitecture*
Power spectral density will be computed for SWS epochs using Welch’s method. Delta-band power (0.5–4 Hz) will be quantified and normalized to total NREM power to account for inter-individual variability.
Slow oscillations will be detected within SWS using zero-crossing–based approaches in the 0.5–1 Hz frequency range. Extracted features will include slow oscillation density, amplitude, and slope, reflecting cortical network integrity during deep sleep.

### *Spatial Analysis*
For multichannel EEG recordings, regional differences in slow-wave activity will be examined by comparing delta power across frontal, central, and occipital leads. Frontal dominance of slow-wave activity will be quantified as an indicator of normal SWS organization, with deviations interpreted in the context of Alzheimer’s-related cortical dysfunction.
Feature-based computational analyses will be conducted to examine the similarity of slow-wave sleep patterns between sleep-deprived individuals and patients with Alzheimer’s disease. Dimensionality reduction and clustering approaches will be used to visualize overlap in SWS feature space, while distance-based metrics will quantify the degree of convergence between groups. These analyses are intended to assess neurophysiological pattern similarity rather than clinical prediction or diagnostic classification.

### *Statistical Analysis*
Exploratory comparisons will be performed within and between datasets where applicable. Statistical tests will be selected based on data distribution, and analyses will be adjusted for age and sex when metadata permit. Multiple comparisons will be controlled using false discovery rate (FDR) correction.

### *Implementation*
All analyses will be conducted in Python, using MNE-Python for EEG preprocessing, YASA for sleep-related feature extraction, and standard scientific libraries including NumPy, SciPy, and Matplotlib.

### *Study Status*
*This work is currently in the early implementation phase, with preprocessing and SWS feature extraction pipelines under development and planned extension to NSSR cohorts.*

**Bold**
*Italic*


```code block```
