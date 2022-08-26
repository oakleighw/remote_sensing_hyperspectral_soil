# Loading, Visualisation & Trial Regression of Hyperspectral Soil Imagery
## Data
- This repository includes code for working with hyperspectral soil data, contained within npz files.
- The data worked with included 1732 patches of varying size.
- Each data 'patch' included the field view 'full image' and cropped inner (non-shrubbery) region 'masked image'.
- Each 'image' consisted of 150 bands.
<p align="center">
  <img src = "/imgs/bandImg.jpg" alt="image of masked and unmasked soil patch image" width="400" img align="middle" />
</p>

## dataset.ipynb
- This builds on the 'starter pack' supplied by the challenge (A competition to accurately predict soil parameters [k, P, Mg, pH] using the hyperspectral imagery).
https://platform.ai4eo.eu/seeing-beyond-the-visible/data
- Visualises ground truth values.
<p align="center">
  <img src = "/imgs/groundTruth.jpg" alt="ground truth variable values histogram" width="600" img align="middle" />
</p>

- Gets central tendency metrics of pixel values over bands and visualises this.

<p align="center">
  <img src = "/imgs/bandDeviation.jpg" alt="mean and deviation of pixel values over bands" img align="middle" />
</p>

- Reduces dimensionality using PCA, examines explainable variance ratio and takes the top two PCA values (Capture over 96% of total variance).

<p align="center">
  <img src = "/imgs/variationRatio.jpg" alt="Explainable variance ratio of PCA values" img align="middle" />
</p>

## PCA_visuals.ipynb
- Visualises PCA-transformed pixel values (Shows unmasked images are outlier-full).

<p align="center">
  <img src = "/imgs/outliers.jpg" alt="masked transformed pixels versus unmasked - visualized" img align="middle" />
</p>

<p align="center">
  <img src = "/imgs/colourization.jpg" alt="masked transformed PCA 1 & 2 values visualized by P value" img align="middle" />
</p>

- Visualises Averaged PCA (and median) values over each image.
<p align="center">
  <img src = "/imgs/averaged.jpg" alt="masked transformed PCA 1 & 2 values (averaged per image) visualized by P value" img align="middle" />
</p>

## truncatedSVD_transform.ipynb
- Dimensionality reduction using truncatedSVD (Replicates workflow at end of dataset.ipynb).

## truncSVD_Visuals.ipynb
- Similar to PCA_visuals but for truncatedSVD.

## PCA_SVD_Regression.ipynb
- Attempts to fit transformed datasets - (Masked average PCA-transformed values per Image/ Masked average SVD-transformed values per Image) to several regressors.

# Outcome
- The PCA and truncatedSVD transformed hyperspectral imagery is not linearly seperable. Shown by visualised transformed pixel data and poor MSE values when fitted with simpler regressors.
- More complex regression methods (Deep Learning?) need to be assessed, along with other dimensionality reduction algorithms (TSNE?).
