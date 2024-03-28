# ConFUse-net

Medical image segmentation, which involves identifying regions of interest in medical images, is an important tool in the diagnosis, treatment, and monitoring of various ailments. For much of the past decade, convolutional neural networks (CNN’s) have been used with great success for segmentation tasks. In particular a U-shaped encoder/decoder CNN architecture called U-net has become popular for medical image segmentation. 

Although U-net performs very well for many image segmentation tasks, its performance is constrained by one inherent limitation: it struggles to capture long-range dependencies. Inspired by the recent success of the Vision Transformer, a new type of segmentation network has appeared in the literature which combines aspects of U-net and Transformer architectures. In this paper, we analyze three such hybrid U-net/Transformer architectures: UTNet, UCTransNet, and Swin-Unet. 

Inspired by the Channel Transformer module proposed in UCTransNet, we also propose an extension to UTNet which replaces the network’s skip connections with a Convolutional Fusion (ConFuse) module. Our experiments show that the proposed network, which we’ve called ConFUse-net, can significantly improve the segmentation performance of UTNet, particularly when limited training data is available.
