# How to Contribute to the Repository - 🚧 UNDER CONSTRUCTION 🚧

We welcome neuroanatomists and other experts to further refine these segmentations, delineate additional ROIs, segment existing ROIs based on alternate research-based interpretations of best practice, etc, and make your updated data available on our open repository. 

Importantly, we use DataLad for version control of our data and require that contributors do so as well to maintain data provenance. Please note that this process requires basic command line experience. Please refer to the following resources and reach out to us if you have any questions or concerns!

[DataLad Introduction to The Command Line](https://handbook.datalad.org/en/latest/intro/howto.html#the-command-line)<br> 
[DataLad Handbook](https://handbook.datalad.org/en/latest/index.html)<br>
[DataLad Cheatsheet from Handbook](https://handbook.datalad.org/en/latest/basics/101-136-cheatsheet.html)<br>
[DataLad Cheatsheet (Jade Sea)](https://handbook.datalad.org/en/latest/basics/101-136-cheatsheet.html)

To contribute, please follow the steps below.

## STEP 1: Submit Contribution Request Form

Before getting started, please fill out the [Request Form](https://docs.google.com/forms/d/e/1FAIpQLSdppXSfL7RZ2jxo5t8ufh2jZ5tgNLaAKb5pzfOJ8md9F22PsQ/viewform?usp=sf_link) to provide us with your name, institution, updates or additions you plan to make to the repository data, and where researchers can find documentation on your data and/or segmentation protocol. We will then connect with you to confirm that your request has been approved and add you as a collaborator to the [DataLad GitHub repository](https://github.com/DCAN-Labs/bobsrepository). **You must have the appropriate permissions before proceeding with the next steps, otherwise your data will not be properly version controlled.**


## STEP 2: Using DataLad Version Control to Download, Update, and Contribute to the Repository

### Initial Setup and Requirements
**Install DataLad** following [these instructions](https://handbook.datalad.org/en/latest/intro/installation.html#installation-and-configuration) according to your operating system.

**Create GitHub account** (if you haven't already) [here](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github) and [install git](https://github.com/git-guides/install-git). We highly reccommend storing your credentials by going to your home directory on the command line and running:<br>
```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Create free Amazon AWS account** [here](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html?refid=em_127222&p=free&c=hp&z=1). This is required in order to download the repository via DataLad. Once you have set up an account, click on your username in the top right-hand corner of the screen and select `Security Credentials` from the drop down menu. Scroll down the page to the `Access keys` section, select `Create access key` in the upper right-hand corner of the section, and follow the prompts from there to obtain access and secret keys. **Make sure to copy and store your access and secret keys in a secure location to reference in the future!!**

### Clone the Repository Using DataLad
On the command line, cd into to the directory where you want to download the repository locally. If you installed DataLad in a virtual environment, remember to activate it. Export your AWS access and secret keys you obtained from setting up your Amazon AWS account as environmental variables:
```
export AWS_ACCESS_KEY_ID="<access key>"
export AWS_SECRET_ACCESS_KEY="<secret key>"
```

And then clone:
```
datalad clone https://github.com/bobsrepository.git
```

Note that the GitHub repository does not actually contain the annexed files themselves, but rather symlinks to the data files stored on AWS. To download the annexed file content from AWS, cd into the cloned repository folder and run `datalad get` the following (note that it will take a few minutes to download the full repository contents):
```
cd bobsrepository
datalad get . -r
```

### Updating the Data

Create a new GitHub branch using a descriptive branch name related to your intended data modifications and switch to that branch. For example, if you plan on segmenting an additional ROI that is currently not delineated in the the sourced version folder, name the folder `V1.0_<ROI>`
```
git checkout -b <YOUR-NEW-BRANCH>
```

You'll next make a new folder where you can make your modifications to the data. Before doing so, you must "unlock" the contents of the DataLad repository: files that are annexed for version control are write-protected to ensure file integrity by default. Therefore, before editing the files, you must use `datalad unlock`, otherwise you may jeopardize the version control and file integrity. 

First unlock the folder contents and then copy the entire contents of `V1.0` to a new folder with the same name as your new branch. Please only modify data within your newly created folder. 
```
datalad unlock V1.0
cp -r V1.0 <NEW-FOLDER-NAME>
```
Next save and push your changes by running:
```
datalad save -m "Description of changes"
git annex export master --to aws
datalad push --to github
```

From here, you can modify the files within your working directory as you please, just remember to use `datalad unlock <filename>` before making modifications. 

### Submitting a Pull Request Once Your Data is Ready to Share
Once you have completed your updates and are ready to share to the repository hosted on AWS, please ensure that you have run a final datalad save and push to your branch. Also ensure that the directory structure and filenames within your working directory match that of the source directory exactly in order to be in compliance with BIDS standards.

When ready, submit a [PR (pull request)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) to request to merge your branch with the main repository. We will then review your data and merge if there are no issues.




