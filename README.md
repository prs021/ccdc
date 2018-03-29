# CCDC
Algorithm developed for Continuous Change Detection and Classification (CCDC) of land cover using all available Landsat data. Please contact Zhe Zhu (zhe.zhu@ttu.edu) at Department of Geosciences, Texas Tech University if you have any questions. 

CCDC Software is available online now!

The Most Recent 13.01 CCDC Software for Change Detection software is [here](https://drive.google.com/file/d/1WiVLh4yWQ44JdQj87Wgh7lBLs32Px1xI/view?usp=sharing). It would work both for Analysis Ready Data and Collection 1 data. It would only work for 64 bits Linux machine. 

The Classification software is not provided at the moment, as it required training data to run the software.

Note that the output from CCDC will be thousands of Matlab files that contains all sorts of information for each time serie models as follows: 

1. "t_start": when the time series model gets started

2. "t_end": when the time series model gets ended
 
3. "t_break": when the first break (change) is observed

4. "coefs": the coefficients for each time series model for each spectral band

5. "rmse": the RMSE for each time series model for each spectral band

6. "pos": the position of each time series model (location)
 
7. "change_prob": the probability of a pixel that have undergone change (between 0 and 100)
 
8. "num_obs": the number of "good" observations used for model estimation

9. "category": the quality of the model estimation (what model is used, what process is used)
 
10. "magnitude": the magnitude of change (difference between model prediction and observation for each spectral band)

You need to extract those information from thousand of Matlab file to generate change maps or used as input for change detection. 

How to use the code:

1. Install Matlab Runtime Compilier version 8.1 for Linux 64-bit [here] (http://ssd.mathworks.com/supportfiles/downloads/R2017b/deployment_files/R2017b/installers/glnxa64/MCR_R2017b_glnxa64_installer.zip)

2. Download all available Landsat CDR data from [espa](https://espa.cr.usgs.gov/) and put them into BIP ENVI format. This including stacking spectral bands in sequence of Blue, Green, Red, NIR, SWIR1, SWIR2, TIR, Fmask. Each image is in its sub-folders.

3. CD to the image folder where all the images are saved in each individual subfolders. If your CCDC software is save in this location /zhezhu/ccdc/, you can just type /zhezhu/ccdc/CCDC_ChangeARD13_01 1 1 to Run the standalone sotware on one core. If you want to run on N cores, you will need to write script to submit job to each individual cores by CCDC_ChangeARD13_01 i n (i=1,2,3...n; where n is the total number of cores, and i is which core to run the current job). Note that CCDC is extremly computational expensive. Please use as many cores as you can on your Linux clusters. The computing time for one path/row for 500~1000 images takes 1 hour to 5 hours for 500 cores running in parallel. 

Please cite the following

paper 1: Zhu, Z. and Woodcock, C. E., Continuous monitoring of forest disturbance using all available Landsat imagery, Remote Sensing of Environment (2012), doi:10.1016/j.rse.2011.10.030.(paper for CCDC version 1.0.)

paper 2: Zhu, Z. and Woodcock, C. E., Continuous change detection and classification of land cover using all available Landsat data, Remote Sensing of Environment (2014), doi.org/10.1016/j.rse.2014.01.011.(paper for CCDC version 7.3.)

paper 3: Zhu, Z., Woodcock, C. E., Holden, C., and Yang, Z., Generating synthetic Landsat images based on all available Landsat data: Predicting Landsat surface reflectance at any given time, Remote Sensing of Environment (2015), doi.org/10.1016/j.rse.2015.02.009.(paper for CCDC version 11.4.)

This algorithm has been applied to many parts of the world and you can see all located where it has been applied [here] (https://github.com/bullocke/Landsat-Database/blob/master/PRmap.geojson).

You can download the PPT with GIF images that explain the CCDC algorithm at this [link] (https://www.dropbox.com/s/1jzfte8mjy4qzzr/CCDC_algorithm_intro.pptx?dl=0).

You can learn the CCDC algorithm and its current status at this [link]
(https://landsat.usgs.gov/sites/default/files/documents/Zhu_070915_CC.mp4).
