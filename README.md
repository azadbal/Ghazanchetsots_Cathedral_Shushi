# Ghazanchetsots_Cathedral_Shushi

### Summary 
A crowdsourced Photogrammetry reconstruction of the Ghazanchetsots Cathedral in Shushi, Artsakh (Nagorno-Karabakh Republic) for cultural hertiage documentation and preservation by extracted frames from pubclily available drone videos of the site from Youtube.  

----
## Sketchfab Mesh Preview
https://skfb.ly/6XyzY


## Introduction	
The project was started in Nov of 2020, during the midst of the 2nd Karabakh War. As the war waged on, important cultural heritage sites were at risk of being damaged or destroyed, especially the Ghazanchetsots Cathedral. 

To my knowledge, no 3D scans (Photogrammetry nor LIDAR) exist of the Cathedral. 3D scans are important for cultural heritage documentation and digital preservation, Archeology, History, Cartography, amongts other things.  

When I started this project, the Ghazanchetsots Cathedral in Shushi was hit with artilary on two separate occasions, causing immense damage. Since then, the city has been occupied by Azerbaijan has the cathedral desecrated with graffiti. As a result, this reconstruction project is even more important for the purposes of reconstructing and digitially preserving the cathedral in a less dire condition.

The focus of this project was to find various drone videos of the site, to download and extract frames to be able to fully reconstruct the Cathedral. Of course, I am only limited to what exists publically on the internet, but I'm hoping that over time, more footage of the site turns up and that can be aligned to the dataset to create a more complete, denser, and higher quality 3D reconstruction.  

In this README, I outline my work and discuss the methods used to achieve the reconstruction results. I have also attached the RealityCapture PPI license of this project for anyone to be able to download the data and replicate my results for free using RealityCapture. 


## Method

I started the hunt to find drone videos of the Ghazanchetsots Cathedral due to the fact that drone videos tend to include many lateral move shots (which is favorable for photogrammetry reconstructions) as well as their relative stability (due to gimbals) compared to handheld videos.


### Video/Images Sources

Title: Discover Armenia | Visit Artsakh | 4K Drone Footage
Author: Lilit Asatryan
Video: (https://youtu.be/CLK5WJUAnBc)[https://youtu.be/CLK5WJUAnBc]

Title: Armenia & Artsakh - A Bird's Eye View - 4K Drone Footage 🇦🇲 - 
Author: apotize (Apo Avedissian) - 
Video: (https://youtu.be/EoRpaXtlmqo)[https://youtu.be/CLK5WJUAnBc]

Note: The frames for Lilit Asatryan's drone video are not from the Youtube video, but rather from the original footage from her drone. To achieve a higher quality reconstruction, I reached out to Lilit, the drone pilot and was able to get in contact with her to see if she still had access to the unedited shots of the Cathedral, which she did and she transfered them to me. Due to github LFS budget limitations, I have not included the source videos in the reposoitory.

All frames used for reconsutrction can be found in /Image_Data/HQ_frames/ which is what you need to replicate the full mesh that I reconstructed. 

### Software Used
Frame extraction: (FFmpeg)[https://ffmpeg.org/], more specifically (Free Video to JPG Converter)[https://www.dvdvideosoft.com/products/dvd/Free-Video-to-JPG-Converter.htm] which is a nice UI for FFMpeg.
Photogrammetry: (Reality Capture)[https://www.capturingreality.com/]

### Data Alignment
The model is reconstructed from three drone shots of the cathedral, which didn't have too much overlap. Initially, Reality Capture was able to align the frames from all three shots into a single component, but there were too much misalignments for my taste. 

To fix the misalingments, I used Control Points to manually find and mark common features between the shots. The result was much better than the initial misalignment, although it could be better.

Initially, I aligned the frames from one drone dataset so that I can ensure the lens distortion is consistent across all the data (to not introduce more alignment issues). Once all the data from one drone video dataset was aligned, I locked their positions and added the data from the other drone shot. Of course, no EXIF data was available for any of these videos, so it wasn't clear what cameras/lenses were used. I used the K + Brown4 and tangential2 Disortion Model for Alignment. 

The alignment and registeration can be found in \RealityCapture_Data\Alignment_and_Registeration\, both as a Reality Capture component file (which can be used in any new Reality Capture project), or as a CSV file with the CommaSeparated_Name_X-Y-Z_Omega-Phi-Kappa format. 

### Reconstruction
The reconstruction was done with "Downscale 2" of the 4k frames. The final reconstructed area is much larger than what I chose to crop down to, which is only the cathedral. This was done as an artistic choice to focus more on the subject rather than the surrounding. 

### PPI License
Reality Capture has a licesning method called Pay-Per-Image, which I used to process and license this project. You can reconstruct this dataset with Reality Capture for free by using the PPI License. It can be found in \RealityCapture_Data\PPI_License\

-----

## Location Context - 
" Built between 1868 and 1887, the cathedral was consecrated in 1888. It was damaged during the March 1920 massacre of Armenians of the city by Azerbaijanis and experienced a decades-long decline, well into the Soviet period.During the first Nagorno-Karabakh War Azerbaijan used the cathedral as an armoury to store hundreds of missiles. Subsequently, during the 2020 war, it was damaged by shelling.

The cathedral was extensively restored in the aftermath of the first war and reconsecrated in 1998. It is landmark of Shusha and Karabakh and is a listed cultural and historical monument of the unrecognised Republic of Artsakh. Standing 35 metres (115 ft) high, Ghazanchetsots is one of the largest Armenian churches in the world." - [Wikipedia](https://en.wikipedia.org/wiki/Ghazanchetsots_Cathedral)
