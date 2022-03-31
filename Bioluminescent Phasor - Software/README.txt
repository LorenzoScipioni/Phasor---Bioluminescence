The MATLAB script "Bioluminescent_Phasor_Software.m" is monolithic, with all relevant function embedded in the file. 
For the sake of space, Dark and Bright calibration are presented here as average over the whole dataset, while they were originally composed by 180 and 100 frames, respectively.
The script was tested on a Windows 10 operating system with MATLAB 2021b and requires the "Signal Processing" and "Image Processing" toolboxes.

To run the script:

1. Double click on the file named "Bioluminescent_Phasor_Software.m", select "Change folder" when prompted
2. Run (F5) and follow the instructions:
	Dark file	: Dark.tif
	Bright file	: Bright.tif
	Experiment file : GeNL_HeLa_FRZ_exp10000ms_20f_sin+cos.tif
3. When prompted, select the area of the image corresponding to the SIN filter (left side of the image)
4. Without resizing the area, select (roughly) the same area on the intensity image on the right side

The script should run for approximately 30 seconds, will display the operations it is performing and will save three files:

1. An image of the phasor plot and corresponding angular histogram
2. An image of the intensity image and the Bioluminescence Emission Color image
3. A workspace with relevant parameters relative to the experiment file

CODE WORKFLOW:

Section 1: Camera Calibration
	a. Select file paths (dark calibration, bright calibration, experiment files)
	b. Load first calibration file and select user-defined areas for analysis
	c. All four channels are automatically aligned
	d. On the selected areas, compute pixelwise calibration using bright and dark calibration files
	e. Calibration is stored and unused parameters are deleted

Section 2: Experiment analysis
	a. Experiment files are loaded one at the time
	b. All four channels are smoothed and binned
	c. A threshold is selected to create a binary mask, from which the cells are selected
	d. The binary masks for each channel are registered
		NOTE: 	This operation is carried out in line 224 in automatic. 
			Change mode from 'Auto' to 'Manual' to choose threshold and cells manually
	e. Phasor transformation is computed
	f. Results are displayed and experimental parameters are saved

Lorenzo Scipioni - Laboratory for Fluorescence Dynamics @ UCI - 2022.01.29