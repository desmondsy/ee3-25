# ee3-25

## Abstract
The aim of this coursework is to train a descriptor network
such that it is able to perform accurately in the evaluation
tasks: matching, verification and retrieval, on noisy image patches. The N-HPatches dataset (https://github.com/hpatches/hpatches-dataset) contains different patch sequences (which represent some local part of a larger image), each patch sequence contains a reference image plus 5 homographies of that image. A homography is essentially a transformation of the image. A noisy version of each patch sequence is also provided, with noise levels ranging from low to high.

To do this, two CNN architectures are used sequentially. First, a U-Net autoencoder is used to denoise the patches, followed by an L2-Net that outputs 128x1 descriptors for the denoised patches, which are used to represent the patch and differentiate itself from other patches. Three identical L2-Nets are merged together to create a 'triplet network', each computing the descriptor vector (len: 128) for an anchor, positive, and negative patch. The triplet network is trained via a triplet loss metric, such that descriptors from the anchor and positive patch have a low distance between them, and the negative and anchor patch have a large distance between them. Lastly, the descriptor vectors are evaluated on 3 tasks (matching, verification, retrieval) based on the H-Patches Benchmark (https://github.com/hpatches/hpatches-benchmark). A final model is trained on successful modifications of the baseline code.
