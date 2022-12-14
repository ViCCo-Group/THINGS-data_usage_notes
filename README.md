# THINGS-data - Download and usage notes

Thank you for your interest in THINGS-data! [THINGS-data](https://doi.org/10.1101/2022.07.22.501123) is a collection of large-scale datasets for the study of natural object representations in brain and behavior. It includes functional magnetic resonance imaging (fMRI) data, magnetoencephalographic (MEG) recordings, and 4.70 million similarity judgments in response to thousands of images from the [THINGS object concept and image database](https://doi.org/10.1371/journal.pone.0223792).

This homepage gives hints on how to download the dataset and provides some information about the contents of the data files for the fMRI data in particular. If you encounter any technical difficulties, please get in touch with us!

# Download

We're excited to make THINGS-data openly accessible to researchers and the general public. We will make all contents of the dataset collection openly available upon publication of the manuscript. The manuscript is currently under review (date: Sept. 6th 2022). If you're interested in gaining early access, please get in touch with us (hebart [at] cbs.mpg.de)!

> 📘 Early access
>
> For early access, the data download is restricted to the figshare collection. The OpenNeuro and OSF repositories will become public once the THINGS-data manuscript is published.

## Download from figshare

THINGS-data is hosted as a collection of data objects on figshare. Once the collection is public or we have granted you early access, you can browse the collection and download individual parts which are relevant for your research. By default, clicking on the desired data object will prompt a browser download. If you plan to download larger data objects such as the raw MEG or fMRI datasets, it might make sense to start this process in the command line. Simply right-click on the “Download” button and copy the link address. Execute `wget https://figshare.com/copied/link/address` in the command line to begin the download process for that file. For longer downloads, it might make sense to run this process in the background with tools such as `screen` or `tmux`.

## Download from OpenNeuro

The raw fMRI and MEG datasets are available on [OpenNeuro](https://openneuro.org). You can find instructions on how to download data on the [OpenNeuro documentation](https://docs.openneuro.org/user-guide).

## Download from OSF

The behavioral dataset containing 4.7 million human similarity judgements is available on OSF and can be downloaded directly via your web browser.

# Usage notes

- [fMRI data](fmri_usage_notes.ipynb)

# How to cite
```
@article {Hebart2022.07.22.501123,
	author = {Hebart, M.N. and Contier, O. and Teichmann, L. and Rockter, A.H. and Zheng, C.Y. and Kidder, A. and Corriveau, A. and Vaziri-Pashkam, M. and Baker, C.I.},
	title = {THINGS-data: A multimodal collection of large-scale datasets for investigating object representations in brain and behavior},
	elocation-id = {2022.07.22.501123},
	year = {2022},
	doi = {10.1101/2022.07.22.501123},
	publisher = {Cold Spring Harbor Laboratory},
	URL = {https://www.biorxiv.org/content/early/2022/07/23/2022.07.22.501123},
	eprint = {https://www.biorxiv.org/content/early/2022/07/23/2022.07.22.501123.full.pdf},
	journal = {bioRxiv}
}
```
