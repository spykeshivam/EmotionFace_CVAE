# EmotionFace_CVAE

Inputs to the system : Once the vae is trained on greyscale image with emotions conditioning, the decoder model is used to generate the artefacts. The input to this decoder is a 128 dimensional vector sampled randomly from the latent space and a Binary one-hot encoded vector specifying the desired emotion: Angry: [1, 0] or Happy: [0, 1]. 
The cVAE is deployed in 3 different modes. These are explained below with their data flow : 

## Training mode 
Forward and backward pass through the encoder and decoder to construct a good latent space that is conditioned for both the emotions.

## Reconstruction Mode
This is a Forward Pass only mode which means there is no backpropagation or weight updates. Below is how the data flows in this mode.
Input Image + Emotion Label -> Encoder -> Latent Space -> Decoder -> Reconstructed Image

## Generation Mode
This mode involves only the decoder and not the encoder like the above 2. In this mode, a 128 dimensional Latent vector is chosen using  Random sampling from N(0,1) distribution. An input expression (Happy or angry) is used to perform conditional decoding. This emotion condition guides the generation process. Multiple images can be generated using the function generate_faces. 
The system incorporates several methods to assess and visualize the generated outputs:
Original and reconstructed Images are displayed side-by-side to evaluate reconstruction quality. The images are Generated per emotion.

## Architectures

The two notebooks have the following architecture:

1. Encoder and Decoder both made up of deep convolution networks with FiLM layers used for conditioning
2. Encoder uses VGG that is fine tuned for face feature extraction.





