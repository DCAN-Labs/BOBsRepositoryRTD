# How to Access Data
  
## Viewing the data on BrainBox - *TO DO: add screenshots*

If you wish to simply view the brain segmentations overlaid on their associated T1w and T2w images, we have created repositories on BrainBox for each of the age bins located here:

[BOBsRepository1mo](https://brainbox.pasteur.fr/project/BOBsRepository1mo)  
https://brainbox.pasteur.fr/project/BOBsRepository2mo  
https://brainbox.pasteur.fr/project/BOBsRepository3mo  
https://brainbox.pasteur.fr/project/BOBsRepository4mo  
https://brainbox.pasteur.fr/project/BOBsRepository5mo  
https://brainbox.pasteur.fr/project/BOBsRepository6mo  
https://brainbox.pasteur.fr/project/BOBsRepository7mo  
https://brainbox.pasteur.fr/project/BOBsRepository8mo

After selecting a specific anatomical to view, remember to also select the label set json with the matching subject ID to see the segmentation overlay.

## How to Download 
### Using Cyberduck to download data locally

We recommend using [Cyberduck](https://cyberduck.io/) to download the BOBs Repository image files locally. After downloading and opening Cyberduck, do the following to connect to the data repository bucket stored on Amazon Web Services S3 bucket:

1. Click *Open Connection*
2. In the dropdown menu at the top of the dialogue box, select *Amazon S3* and the Server box will automatically populate with *s3.amazonaws.com*
4. Check *Anonymous Login* (if you are unable to check this box, type "anonymous" into the Access Key ID field instead) 
5. Expand the More Options tab and enter for Path: `future/path/to/data`
6. Click *Connect*

![cyberduck screenshot](https://github.com/DCAN-Labs/bobsrepo/blob/main/cyberduck_screenshot.png)


### Organization of BOBS Repository Data in S3 Bucket
The top-level directory contains all participants folders named by subject ID, each of which contains session folders that indicate the age at which the MRI images were acquired (eg ses-1mo acquired at 1 month old chronological age). The T1w and T2w image files and accompanying segmentation files are located in the `anat` subdirectory under session following [BIDS Derivatives](https://bids-specification.readthedocs.io/en/stable/derivatives/introduction.html) data structure requirements.

In addition, the top-level directory also contains 2 files: a `dataset_description.json` and `participants.tsv` file that contain a description of the dataset and list of subject IDs and sessions, respectively, following [BIDS specification](https://bids-specification.readthedocs.io/en/stable/modality-agnostic-files.html#modality-agnostic-files). 

Here is an example of the directory structure using fake subject ID numbers:

![tree](https://github.com/DCAN-Labs/bobsrepo/blob/main/s3_tree.png)
