# Loading, Visualisation & Trial Regression of Hyperspectral Soil Imagery
## Data
- This repository includes code for working with hyperspectral soil data, contained within npz files.
- The data worked with included 1732 patches of varying size.
- Each data 'patch' included the field view 'full image' and cropped inner (non-shrubbery) region 'masked image'.
- Each 'image' consisted of 150 bands.

## dataset.ipynb
- This builds on the 'starter pack' supplied by the challenge (A competition to accurately predict soil parameters [k, P, Mg, pH] using the hyperspectral imagery).
- Visualises ground truth values.
- Gets central tendency metrics of pixel values over bands and visualises this.
- Reduces dimensionality using PCA, examines explainable variance ratio and takes the top two PCA values (Capture over 96% of total variance).

## PCA_visuals.ipynb
- Visualises PCA-transformed pixel values.
- Visualises Averaged PCA (and median) values over each image.
- Shows unmasked images are outlier-full.

## truncatedSVD_transform.ipynb
- Dimensionality reduction using truncatedSVD (Replicates workflow at end of dataset.ipynb).

## truncSVD_Visuals.ipynb
- Similar to PCA_visuals but for truncatedSVD.

## PCA_SVD_Regression.ipynb
- Attempts to fit transformed datasets - (Masked average PCA-transformed values per Image/ Masked average SVD-transformed values per Image) to several regressors.

# Outcome
- The PCA and truncatedSVD transformed hyperspectral imagery is not linearly seperable. Shown by visualised transformed pixel data and poor MSE values when fitted with simpler regressors.
- More complex regression methods (Deep Learning?) need to be assessed, along with other dimensionality reduction algorithms (TSNE?).
