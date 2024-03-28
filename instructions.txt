These instructions explain step-by-step how to configure and run the project within Google Drive and Google Colab. I recommend using Google Colab to run the project, as this makes importing libraries and data very easy; however, the instructions can be adapted to other circumstances if need be. 

1. Download the Synapse dataset.
	a. Navigate to: https://www.synapse.org/#
	b. Click on "Register Now" to create an account, or login by clicking "Log In To Synapse" (a Synapse account is required to download the necessary dataset).
	c. Once you've created/logged into your account, navigate to: https://www.synapse.org/#!Synapse:syn3193805/wiki/217789
	d. Click on the "Files" tab. 
	e. Locate and expand the "Abdomen" directory. Note: this directory will not be visible unless you're logged into Synapse.
	f. Locate the file "RawData.zip" (1.531 GB). Click the corresponding download icon on the far right. This will add the file to your download list. 
	g. Click on the "Download Cart" button (the download icon on the far left).
	h. Scroll down until you see "RawData.zip" and click the grey download icon on the right.
	i. After a few seconds you should see RawData.zip in your downloads folder. 

2. Upload the dataset to Google Drive (if using Colab to run project). 
	a. Log into Google Drive.
	b. Unzip and upload (or vice versa) the project directory and navigate to the data/multi-class folder.
	c. Within the folder, upload RawData.zip but do not unzip. 

3. Configure the notebook.
	a. Open UTNet.ipynb.
	b. Ensure that all of the required dependencies listed in dependencies.txt are installed.
		i. When working in Colab, the only library that I needed to install was einops.
		ii. This library can be installed by running either "pip install einops" in a terminal window or "!pip install einops" in a cell.
	c. Within the "Constants" cell, modify the first six lines so that the paths match your environment. NOTE: if running in Colab, you can leave  ii, iii, iv, and v alone!
		i. ZIP_PATH: the absolute path to RawData.zip. This will likely start with "/content/drive/MyDrive/" and from there you'll need to type your specific path.
		ii. TRAIN_IMG_PATH: the path to the training images (which we'll eventually unpack from RawData.zip). 
		iii. TRAIN_MASK_PATH: the path to the training masks (which we'll eventually unpack from RawData.zip).
		iv. TEST_IMG_PATH: the path to the testing images (which we'll eventually unpack from RawData.zip).
		v. TEST_MASK_PATH: the original dataset does not contain testing masks because it was used for a competition. Thus a testing mask directory doesn't exist yet, but we will create one in a minute. 
		vi. NET_PATH: the path to the folder which stores trained models. You will likely need to change the portion between "/content/drive/MyDrive/" and "/Final Project/models".
	d. Run notebook cells until you come across one titled "Unpack the zipped file from Google Drive..." (should be about three down from Constants). 
	e. Uncomment the line "!{command}" and run the cell. This will start unpacking RawData.zip into the Colab environment. Once that is complete, you should see a "RawData" directory on the left of the page under the file tree. 
	f. As mentioned, the original dataset doesn't contain any testing masks, so we need to include some ourselves.
		i. Under RawData/Testing, add a new folder called "label". 
		ii. Remove all of the files currently in RawData/Testing/img.
		iii. Move some images and corresponding masks from RawData/Training/img and RawData/Training/label to RawData/Testing/img and RawData/Testing/label, respectively. In our experiments, we've been moving the first 10 images (img0001.nii.gz-img0010.nii.gz) and masks (label0001.nii.gz-label0010.nii.gz) to testing.

4. You should now be ready to run the remainder of the notebook. 