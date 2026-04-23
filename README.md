# From Sinograms to CT Images
This repository contains the implementation of a comprehensive pipeline for Computed Tomography (CT) image reconstruction and denoising. Developed for the Intelligent Analysis of Biomedical Images course, the project explores the end-to-end process of generating synthetic phantoms, applying the Radon transform to create sinograms, reconstructing images using Filtered Back Projection (FBP), and finally training a Deep Learning denoiser to improve reconstruction quality under noisy and limited-angle conditions.

## Key Features & Project Structure
1. **Synthetic Dataset Generation:** 
   * Generates a dataset of 1,000 randomized $128 \times 128$ phantoms (combining Shepp-Logan with random ellipses).
   * Split into 800 training, 100 validation, and 100 testing samples.
2. **Forward & Inverse Physics (Radon & FBP):**
   * Computes the Radon transform to simulate X-ray projections (sinograms).
   * Reconstructs CT images from sinograms using Filtered Back Projection (FBP).
3. **Artifact Simulation:**
   * **Low-Dose Poisson Noise:** Simulates realistic low-photon noise using $I_0 = 10^4$.
   * **Limited-Angle CT:** Simulates artifacts by restricting projection angles to 120 degrees instead of the full 180 degrees.
4. **Deep Learning Denoiser:**
   * Implements a tiny U-Net-like Convolutional Neural Network (CNN) using PyTorch.
   * Trained to map noisy/artifact-heavy FBP reconstructions back to the clean ground-truth phantoms.
5. **Evaluation Metrics:**
   * Utilizes **PSNR** (Peak Signal-to-Noise Ratio) and **SSIM** (Structural Similarity Index Measure) to quantitatively evaluate reconstruction and denoising performance.
