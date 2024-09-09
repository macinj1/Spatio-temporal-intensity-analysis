# Spatio-temporal-intensity-analysis

The present code allows you to extract the intensity of a image sequence.
The main feature is subdivision of each image in N x M matrix of your region
of interest (ROI). As a result, the evolution of intensity is recorded in a
matrix with time in the z-axis. From each curve, a Fast Fourier Transform
(FFT) is applied and the main moves computed. 

The code reads two types of data: 
- Videos using mp4 or avi extension
- Multipage tiff join to a color/gray image of the experiment. If this
option is used, both files (multipage tiff and color image) should be called
with the same name and the multipage tiff may include "_intensity". E.g. 
the color image is "HOX.tif", the multipage tif is "HOX_intensity.tif". 

Once the code runs, follow the instruction in the Command Windows. There
you will select the ROI, rotate the image, and determine the suitable
mesh for your image. 

The curve of the intensity signal is smoothed using a 2% value of the 
signal length. Next, FFT is applied and the most important modes of 
oscillation are selected by using the mean value of the intensity signal 
as threshold. 

The output variables shown in the Workspace are: 
- Settings: all the parameters used are saved here; 
- image: used to extract the information of the data set; 
- imageRotated: rotated image with the selected angles; 
- imageCropped: cropped image from imageRotated, define ROI for analysis;
- imageMesh: shows the mesh selected for the analysis, overlay on image; 
- Frame: allocated all the frames to be analysed; 
- Images: all the frames in Frame rotated and cropped to extract intensity; 
- Intensity_values: collect the mean intensity of each cell of all
frames, it is organised as Image dimension; 
- fft_intensity: contains the FFT of all intensity in "Intesity_values",
it is organised as a 2D table in which coordinates of Images matrix are
now index coordinates; 
- fft_peaks_locs: contains the wave numbers of the most prominent modes 
above the threshold; 
- fft_peaks_ints: contains the magnitude of the peaks in the previous
variable. 
