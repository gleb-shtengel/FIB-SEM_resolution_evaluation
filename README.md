# Evaluation of FIB-SEM resolution

In order to evaluate the actual resolution in the acquired FIB-SEM datasets we analyzed the transitions of the edges of the ribosomes abundant within the cell volumes. Ribosomes are macromolecular machines consisting of RNA and associated proteins. Their small size (20–30 nm), abundance in the cytoplasm of living cells, and the fact that they are stained with high EM contrast makes them good candidates for resolution evaluation.
First, we selected volumes of approximately 1000–2000 x 1000 x 1000 pixels in cultured cell datasets. These volumes were selected in the middle of datasets in areas with large number of ribosomes. We then calculated histograms of grey level values in these volumes and subtracted ~0.8 * histogram max to bring the average cytoplasmic material signal level close to 0. We then used the Laplacian of Gaussian (LoG) algorithm (part of Python scikit-image package ) to select blobs. We set the limit of standard deviation for LoG between 1 and 2.5 pixels (all these datasets have 4-nm voxels) to ensure that selected blobs were predominantly ribosomes. Filters were used to exclude the following blobs: average value below zero (this meant LoG algorithm failed), edge value above 0.4 times of max value or 37%–63% transition longer than 15nm (the latter two happen where there is another blob or another feature with high signal level in close proximity—making subsequent edge transition analysis inaccurate), amplitudes below certain threshold, so that at least approximately 3000 blobs per dataset were remained for analysis. The edge transitions in all three directions were analyzed for these remaining blobs, in particular we determined 37%–63% transitions (the value used by Zeiss in their resolution estimation) and 20%–80% transitions (close to 1 sigma value).

The original draft of the paper is located here:
https://www.biorxiv.org/content/10.1101/2020.11.13.382457v1

FIB-SEM resolution was aveluated using ribosomes for each cell data set in the paper. In order to accelerate the data download and processing, we cropped a small subset (1Gb-3Gb) of the EM data for each fdata set. The Pyton notebooks work with these cropped subsets.
The Python notebooks for all sell data sets can be downloaded directly from this respository.
The cropped EM data subsets are too large to be held at GitHub, they can be downloaded from DropBox:

HeLa2: https://www.dropbox.com/s/yx3qm1bu5inbh2b/HeLa_Cell2_subset.tif.zip?dl=0

HeLa3: https://www.dropbox.com/s/ix4imwyjgpm4wvw/HeLa_Cell3_subset.tif.zip?dl=0

HeLa4: https://www.dropbox.com/s/jvvn9u0hnqd1vty/HeLa_Cell4_subset.tif.zip?dl=0

Jurkat_Cell1: https://www.dropbox.com/s/ukng1a4awf16fi5/Jurkat_Cell1_subset.tif.zip?dl=0

Macrophage_Cell2: https://www.dropbox.com/s/bk2929930t6529a/Macrophage_Cell2_subset.tif.zip?dl=0

SUM159_Cell2: https://www.dropbox.com/s/f9sa2pxe3hwtl2n/SUM159_Cell2_subset.tif.zip?dl=0

TCell_attckging_Caner_Cell:  https://www.dropbox.com/s/sflvjro5g18hus6/TCell_attacking_Cancer_Cell_subset.tif.zip?dl=0

Finally, the entire package (Python notebooks and EM data subsets) can be downloaded from this alternative location:
https://www.janelia.org/lab/hess-lab/research/high-throughput-3d-electron-microscopy/3d-fib-sem-enabling-3d-connectomics-1
