# ccdc
Algorithm developed for Continuous Change Detection and Classification (CCDC) of land cover using all available Landsat data.

CCDC Software is  available online now!

The Change Detection software is here: https://www.dropbox.com/sh/4j3i5rtheujfjo1/AAA-3iH3iEgUxZeqMak7wNzRa?dl=0

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

1. Install Matlab Runtime Compilier version 8.1 for Linux 64-bit (http://www.mathworks.com/supportfiles/MCR_Runtime/R2013a/MCR_R2013a_glnxa64_installer.zip)

2. Download all available Landsat CDR data (http://landsat.usgs.gov/CDR_LSR.php) and put them into BIP ENVI format. This including stacking spectral bands in sequence of Blue, Green, Red, NIR, SWIR1, SWIR2, TIR, Fmask. Each image is in its sub-folders.

3. Run the standalone on many cores on your Linux clusters. The computing time for one path/row for 500~1000 images takes 1 hour to 12 hours for 600 cores running in parallel. 

Please cite the following

paper 1: Zhu, Z. and Woodcock, C. E., Continuous monitoring of forest disturbance using all available Landsat imagery, Remote Sensing of Environment (2012), doi:10.1016/j.rse.2011.10.030.(paper for CCDC version 1.0.)

paper 2: Zhu, Z. and Woodcock, C. E., Continuous change detection and classification of land cover using all available Landsat data, Remote Sensing of Environment (2014), doi.org/10.1016/j.rse.2014.01.011.(paper for CCDC version 7.3.)

paper 3: Zhu, Z., Woodcock, C. E., Holden, C., and Yang, Z., Generating synthetic Landsat images based on all available Landsat data: Predicting Landsat surface reflectance at any given time, Remote Sensing of Environment (2015), doi.org/10.1016/j.rse.2015.02.009.(paper for CCDC version 11.4.)

This algorithm has been applied to many parts of the world and you can see all located where it has been applied at here (https://github.com/bullocke/Landsat-Database/blob/master/PRmap.geojson).

You can download the PPT with GIF images that explain the CCDC algorithm at this link (https://www.dropbox.com/s/1jzfte8mjy4qzzr/CCDC_algorithm_intro.pptx?dl=0).

Bellow are all the revisions made for CCDC since its first publication (1.0 version)

Change Probability Threshold = 0.99

Number of Consecutive Observations = 6

Maximum Number of Coefficients = 8

CCDC Version = 13.07

******************************************************************************************************

Revisions: $ Date: 10/01/2015 $ Copyright: Zhe Zhu

Version 13.07  Fix a bug for persistent snow and falied Fmask pixels (06/17/2015)

Version 13.06  Connect time for all models (05/28/2015)

Version 13.05  Fix a bug in snow percent (05/19/2015)

Version 13.04  Change T_const in Tmask (03/31/2015)

Version 13.03  Update iteratively before 24 observations (03/22/2015)

Version 13.02  Adjust mini RMSE based on temporal variability (03/22/2015)

Version 13.01  Add more categories and update i_start in the end (03/14/2015)

Version 13.00  Fit curve for disturbed peroid (03/13/2015)

Version 12.20  Convert BT to from K to C before analysis (03/12/2015)

Version 12.19  Fit for permanent snow if it is > 75 percent (03/12/2015)

Version 12.18  No change detection if clear observation < 25 percent (03/12/2015)

Version 12.17  Use median value for very simple model & change magnitude (02/24/2015)

Version 12.16  Finding changes in all water pixels (02/24/2015)

Version 12.15  Use the original multitemporal cloud mask (02/15/2015)

Version 12.14  Do not need example_img in images folder (02/09/2015)

Version 12.13  More infromation in "category" (11/10/2014)

Version 12.12  Fit for pixels where Fmask fails (11/09/2014)

Version 12.11  Fix a bug in num_fc (11/09/2014)

Version 12.10  Better multietmporal cloud detection at the beginning (11/06/2014)

Version 12.09  Detect change for land pixel (water/snow speical case) (10/31/2014)

Version 12.08  Speed up by reducing time for RMSE and model computing (10/17/2014)

Version 12.07  mini rmse should be larger than 10 percent of the mean (10/13/2014)

Version 12.06  Fit model again when there are a 33 percent more in time (10/08/2014)

Version 12.05  Use subset of bands (2-6) for detecting surface change (10/01/2014)

Version 12.04  Only apply Tmask during model initialization (09/29/2014)

Version 12.03  Use subset of bands (3-5) for detecting surface change (09/01/2014)

Version 12.02  Fix a bug in model intialization (08/14/2014)

Version 12.01  Use subset of bands (3-6) to reduce atmosphere influence (08/04/2014)

Version 12.00  Detect change based on probability (07/19/2014)

Version 11.06  No need to change folder name & faster in speed (06/06/2014)

Version 11.05  Improve calculation of temporally adjusted RMSE (04/23/2014)

Version 11.04  Revise "rec_cg.category" for different fit processes (04/01/2014)

Version 11.03  Add "rec_cg.magnitude" as change magnitude indicator (04/01/2014)

Version 11.02  Change very simple fit with mean value (04/01/2014)

Version 11.01  Do not need metadata in the image folder to run CCDC (03/25/2014)

Version 11.00  Use change vector magnitude as hreshold for change (03/25/2014)

Version 10.13  Use subset of bands (1-6) to reduce atmosphere influence (01/31/2014)

Version 10.12  More accurate number of days per year "num_yrs" (01/30/2014)

Version 10.11  RMSE updates with time series fit (01/26/2014)

Version 10.10  Update temperature extreme in recent studies (01/16/2014)

Version 10.09  Find break in max value in any of the band (01/08/2014)

Version 10.08  Add very simple fit (median) for start & end of timeseries (10/21/2013)

Version 10.07  Better multitemporal cloud detection (10/19/2013)

Version 10.06  Add "Tmax_cg" for last step noise removal (10/18/2013)

Version 10.05  Use subset of bands (2-6) to avoid atmosphere influences (10/18/2013)

Version 10.04  Let dynamic fitting for pixels at the beginning (09/23/2013)

Version 10.03  Able to detect change at the verying beginning (09/06/2013)

Version 10.02  Add mini years "mini_yrs" in model intialization (09/03/2013)

Version 10.01  Reduce time for calcuating "v_dif" (09/02/2013)

Version 10.00  Fit for beginning and end of the time series (08/31/2013)

Version 9.09   Only fit more than 50 percent of Landat images overlap area (08/28/2013)

Version 9.08   Force model fit for persistent snow pixels (08/27/2013)

Version 9.07   Add "rec_cg.category", "rec_cg.change_prob", and "recc_cg.num_obs" (08/20/2013)

Version 9.06   Remove mininum rmse "mini" and minimum years "mini_yrs" (08/16/2013)

Version 9.05   Model gets more coefficients with more observations (08/16/2013)

Version 9.04   Fix a bug in calculating temporally adjusted rmse (08/01/2013)

Version 9.03   Fit curve again after one year (03/28/2013)

Version 9.02   Use "mini = T_const/T_cg" for small rmse cases (03/26/2013)

Version 9.01   Remove out of range pixels before time series analysis (02/09/2013)

Version 9.00   Using 8 coefficients and lasso fit (02/01/2013)

Version 8.04   Use "max v_slope" instead of "average v_slope" (01/16/2013)

Version 8.03   Start initialization when "time_span" > 1 year (01/16/2013)

Version 8.02   Fix a bug in not fitting models at the begining (01/16/2013)" (08/20/2013)

Version 8.01   Fix a bug in counting "i" and "i_span"(01/13/2013)

Version 8.00   Temporally changing RMSE (01/09/2013)

Version 7.03   Continuous Change Detection and Classification (CCDC) (07/11/2012)

Version 1.00   Continous Monitoring of Forest Disturbance Algorithm (CMFDA) (07/13/2010)
