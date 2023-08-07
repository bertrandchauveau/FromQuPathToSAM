# FromQuPathToSAM

This repository contains the code used to segment objects from histopathological slides with Segment Anything Model (SAM). It is part of an unpublished project currently under review at a scientific journal.

The code is written in Python, commented and presented in a format compatible with a Google Colaboratory implementation (last checked August 6, 2023). For a detailed description of the context, please see the related manuscript which will be cited here after acceptance.

The code for SAM inference is based on the tutorial provided in the official SAM repository by Meta (https://github.com/facebookresearch/segment-anything), with the related paper: Kirillov A, Mintun E, Ravi N, Mao H, Rolland C, Gustafson L, et al. Segment Anything. arXiv; 2023. Available from: http://arxiv.org/abs/2304.02643.

Here, as in the example of a kidney biopsy provided in the notebook, objects were annotated with points in the QuPath software (https://github.com/qupath/qupath), using the point tool and depending on classes. Points’ coordinates were then extracted with the software interface. The provided code converts the absolute coordinates (at the whole slide image level) to relative coordinates (at the level of a tile) and provides them as inputs to SAM in order to segment each object. A minimal post-processing step is applied, to avoid invalid masks that could disturb the overall segmentation and visibility.

Here are the results with a kidney biopsy image, considering three classes (tubule, glomerulus and vessel) and using one foreground point per object.
![SAM_forgithub](https://github.com/bertrandchauveau/FromQuPathToSAM/assets/110421330/26abe95f-3c12-470c-ba7f-917069cc5891)

Please note that a QuPath extension dedicated to SAM was developed by Ko Sugawara in June 2023: https://github.com/ksugar/qupath-extension-sam and the related paper: Sugawara K. Training deep learning models for cell image segmentation with sparse annotations. bioRxiv; 2023. p. 2023.06.13.544786. Available from: https://www.biorxiv.org/content/10.1101/2023.06.13.544786v1. This extension allows a direct implementation of SAM within QuPath for interactive annotations. To give more insights on this extension, an illustrative video of SAM-aided annotations within QuPath in a kidney biopsy is provided.
