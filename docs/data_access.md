# View or Download the BOBS Repository

## Organization of the BOBS Repository Data
The data structure and filenaming are organized following [BIDS standard](https://bids.neuroimaging.io/):
```
bobsrepository/
|__ sub-<LABEL>/
|   |__ ses-<AGE>mo/
|       |__ anat/
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-T1w.nii.gz
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-T1w.json
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-T2w.nii.gz
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-T2w.json
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-aseg_dseg.nii.gz
|           |__sub-<LABEL>_ses-<AGE>_space-INFANTMNIacpc_desc-aseg_dseg.json
|
|__ phenotype/
|   |__ sessions.json
|   |__ sessions.tsv
|
|__ dataset_description.json
|__ dseg.tsv
|__ README.md
|__ index.html #.bigsignore
|__ V1.0.zip #.bigsignore
```

##### Subject & Phenotypic Data 
The BIDS directory contains subject folders named by subject ID, which contain session folder named by the age at which the MRI images were acquired (e.g. `ses-1mo` means that the data was acquired at 1 month old chronological age). Each session folder contains the T1w and T2w image files and accompanying segmentation files under the `anat/` subdirectory. The repository also contains a `phenotype/` folder containing a global `sessions.tsv` file with a list of subject IDs and sessions as well as phenotypic information such as sex assigned and gestational age at birth (with full field descriptions available in `sessions.json`).

##### Additional BIDS Standard Files
Additional BIDS standard files in the repository include `README.md` and `dataset_description.json`, providing a brief description of the repository and dataset. The repository also contains `dseg.tsv`, which contains the FreeSurfer label descriptions (including the label numbers and default colors when visualized for each segmented brain region).

##### Additional Files (non-BIDS standard)
Finally, the repository contains a few files (e.g. `index.html` and `V1.0.zip`) that are not part of BIDS standard, but are included for ease of access and download. The `index.html` file is a webpage that provides a list of all the files in the repository and links to download individual files. The `V1.0.zip` file is a zipped version of the entire repository. As new versions become available, older versions will continue to be accessible via the zip file.

## How to Download 
Explore the repository contents and download individual files by clicking [here](https://bobsrepository.s3.amazonaws.com/index.html). For a comprehensive download of the entire V1.0 repository, click on [`Download Entire Repository`](https://bobsrepository.s3.us-east-2.amazonaws.com/V1.0.zip) at the bottom of the page.

The contents of the repository are also accessible and can be downloaded anonymously using open-source clients such as [Cyberduck](https://cyberduck.io/).
  
## Viewing the data on BrainBox 

If you wish to simply view the brain segmentations overlaid on their associated T1w and T2w images, we have created repositories on BrainBox for each of the age bins located here:

[BOBsRepository1mo](https://brainbox.pasteur.fr/project/BOBsRepository1mo)  
[BOBsRepository2mo](https://brainbox.pasteur.fr/project/BOBsRepository2mo)  
[BOBsRepository3mo](https://brainbox.pasteur.fr/project/BOBsRepository3mo)  
[BOBsRepository4mo](https://brainbox.pasteur.fr/project/BOBsRepository4mo)  
[BOBsRepository5mo](https://brainbox.pasteur.fr/project/BOBsRepository5mo)  
[BOBsRepository6mo](https://brainbox.pasteur.fr/project/BOBsRepository6mo)  
[BOBsRepository7mo](https://brainbox.pasteur.fr/project/BOBsRepository7mo)  
[BOBsRepository8mo](https://brainbox.pasteur.fr/project/BOBsRepository8mo)

The link will direct you to the first subject in the repository. To scroll, use the bar at the top left. 

![first brainbox screenshot](./images/brainbox_atfirst.png) ![second brainbox screenshot](./images/brainbox_scroll.png)

After selecting another subject's anatomical image to view, remember to also select the label set json with the matching subject ID to see the segmentation overlay. To select another subject to open in a new window, click the full file name, otherwise just click the space to the right of the file name to just change the subject within the frame (see arrows below). 

![third brainbox screenshot](./images/brainbox_newsubject.png)
