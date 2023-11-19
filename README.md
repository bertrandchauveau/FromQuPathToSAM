# FromQuPathToSAM

This repository contains the code used to segment objects from histopathological slides with Segment Anything Model (SAM).

The code is written in Python, commented and presented in a format compatible with a Google Colaboratory implementation (last checked August 6, 2023). For a detailed description of the context, please see the related manuscript publisehd in Pathology (Segment Anything by Meta as a foundation model for image segmentation: a new era for histopathological images. Pathology. 2023 Sep 26:S0031-3025(23)00242-8. doi: 10.1016/j.pathol.2023.09.003, https://www.pathologyjournal.rcpa.edu.au/article/S0031-3025(23)00242-8/fulltext).

The code for SAM inference is based on the tutorial provided in the official SAM repository by Meta (https://github.com/facebookresearch/segment-anything), with the related paper: Kirillov A, Mintun E, Ravi N, Mao H, Rolland C, Gustafson L, et al. Segment Anything. arXiv; 2023. Available from: http://arxiv.org/abs/2304.02643.

Here, as in the example of a kidney biopsy provided in the notebook, objects were annotated with points in the QuPath software (https://github.com/qupath/qupath), using the point tool and depending on classes. Points’ coordinates were then extracted with the software interface. The provided code converts the absolute coordinates (at the whole slide image level) to relative coordinates (at the level of a tile) and provides them as inputs to SAM in order to segment each object. A minimal post-processing step is applied, to avoid invalid masks that could disturb the overall segmentation and visibility.

<a target="_blank" href="https://colab.research.google.com/github/bertrandchauveau/FromQuPathToSAM/blob/main/SAM_histopathology.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

Here are the results with a kidney biopsy image, considering three classes (tubule, glomerulus and vessel) and using one foreground point per object.
![SAM_forgithub](https://github.com/bertrandchauveau/FromQuPathToSAM/assets/110421330/26abe95f-3c12-470c-ba7f-917069cc5891)

Please note that a QuPath extension dedicated to SAM was developed by Ko Sugawara in June 2023: https://github.com/ksugar/qupath-extension-sam and the related paper: Sugawara K. Training deep learning models for cell image segmentation with sparse annotations. bioRxiv; 2023. p. 2023.06.13.544786. Available from: https://www.biorxiv.org/content/10.1101/2023.06.13.544786v1. This extension allows a direct implementation of SAM within QuPath for interactive annotations. To give more insights on this extension, an illustrative video of SAM-aided annotations within QuPath is displayed in the manuscript as supplementary material (also available here: https://drive.google.com/file/d/1nnlA3qHcrNq4PhTLN5Ih-MAUs8vKv1qp/view?pli=1).
