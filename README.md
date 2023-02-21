# The Carolinas Dataset

## Overview

The Carolinas dataset is a comprehensive collection of vehicle trajectory data obtained from two distinct points of view: eye-level and high-angle, as depicted in the following figures. The dataset consists of over 338,000 vehicle trajectories on highways across North Carolina and South Carolina, recorded at eight locations in five cities and towns within these two states, with a minimum trajectory duration of 4 seconds. In addition to trajectory data, the Carolinas dataset includes raw and annotated videos of highway traffic, spanning up to 7.5 hours and comprising 1.6 million frames and 33.47 million bounding box annotations.

![POV Figures](./images/POV_figures_all.png)

<p align="center">
    <img src="./images/figure1.png" width="200" />
    <img src="./images/figure2.png" width="200" />
    <img src="./images/figure3.png" width="200" />
    <img src="./images/figure4.png" width="200" />
</p>

By capturing traffic from eye-level and high-angle viewpoints, the Carolinas dataset offers various perspectives on incoming traffic from different camera angles. Additionally, it features a merging lane to the highway in every video, allowing researchers to study driving behavior while changing lanes near lane closures. These features provide researchers with a rich source of information for analyzing highway traffic patterns and behaviors. The dataset's geographical coverage, range of traffic scenarios, and rich annotations make it an invaluable resource for intelligent transportation systems research and development.

## Data Collection and Extraction

The videos were recorded in full HD resolution (1920 x 1080) at 60 frames per second (fps) and saved in the highest possible quality. Recordings were conducted at various intervals between 9 AM to 7 PM, strategically scheduled across morning, afternoon, and evening hours to capture a diverse representation of traffic patterns and naturalistic driver behaviors.

To extract vehicle trajectories from the videos, we combined YOLOv5 and ByteTrack. The trajectories of detected and tracked vehicles were extracted using the center of the bounding box as the coordinate at 5 fps and 60 fps. The data was extracted at 5 fps, as it is the frame rate used by most vehicle trajectory prediction models. Unique trajectories of a minimum of 4 seconds and above were included to facilitate the use of this dataset for real-world models with minor input and output windows. Stationary vehicles and vehicles moving away from the camera were filtered out, as they were not the focus of this dataset's applications. False detections were removed to improve the overall accuracy of the dataset. In the final step, interpolation was performed to fill in any missing data across frames.

![Data Extraction](./images/data_extraction.png)

## Dataset Format

The dataset comprises three components for each recording: the raw and annotated videos, and two data files that contain the annotated data and extracted trajectories, respectively. Trajectory data files are split into training, validation, and test sets. The annotation data file is in CSV format and includes information such as the frame number, vehicle identification number, coordinates of the bounding box center, vehicle type, and coordinates of the bounding box boundaries.

![Dataset Format](./images/dataset_format.png)

## Dataset Statistics

The Carolinas trajectory dataset consists of 338,000 trajectories extracted from 16 videos at the frame rate of 60 Hz and 5 Hz. The dataset is distributed uniformly between training, validation and test sets, with 70% belonging to training set, 20% belonging to validation set and 10% belonging to test set. The dataset consists of five different classes of vehicles and the distribution of different classes across training, validation and test set is presented in the following figure. It can be seen that dataset has around 90% cars and the rest 10% is divided between bus, truck, bike and motor categories. Similar trends were also observed in previous studies.

![Dataset Statistics](./images/graph_class.png)
