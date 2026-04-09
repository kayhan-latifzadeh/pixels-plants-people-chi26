[![DOI](https://img.shields.io/badge/DOI-10.1145%2F3772318.3791826-blue)](https://doi.org/10.1145/3772318.3791826)


# Pixels, Plants, and People: Affective Evaluation of Urban Green Spaces

<img src="dataset-logo.png" alt="Dataset Logo" width="300">

**Note:** Please download the raw dataset from [Zenodo](https://zenodo.org/records/18348490).

**Abstract:** Urban green spaces are critical for well-being, yet planners lack scalable ways to anticipate how environments will be perceived by users. We conducted an experiment with 27 participants who viewed 30 images of urban spaces while eye movements and brain activity were recorded. Image composition, parsed into 14 urban classes and aggregated as vegetation versus non-vegetation, systematically predicted responses. A higher proportion of vegetation drew more visual attention and was associated with higher attractiveness ratings, while images with less greenery elicited stronger pupillary responses. Brain signal analysis showed topographic patterns in theta and alpha activity between *pleasant* and *unpleasant* scenes, although differences were not statistically significant. Taken together, our findings highlight systematic links between urban scene composition, user attention, and affective responses. We release our dataset and software to support further research. &#91;[ACM DL](https://doi.org/10.1145/3772318.3791826)&#93; &#91;[ResearchGate](https://www.researchgate.net/publication/400976800_Pixels_Plants_and_People_Affective_Evaluation_of_Urban_Green_Spaces)&#93;


## Affective ratings and trials data

The (comma-delimited) affective ratings file `data/trials_info.csv` has 10 columns:

- `participant_id`: (string) Unique participant identifier  
- `stimulus_id`: (int) Numerical ID of the image  
- `stimulus_order_in_experiment`: (int) Presentation order of the stimulus within the experiment  
- `stimulus`: (string) Filename of the presented stimulus (image file)  
- `start_ts`: (int) Unix timestamp in milliseconds marking the start of stimulus presentation  
- `end_ts`: (int) Unix timestamp in milliseconds marking the end of stimulus presentation  
- `Emotional Valence`: (int) Numerical scale for emotional valence 
- `Safety`: (int) Numerical scale for safety 
- `Satisfaction`: (int) Numerical scale for satisfaction  
- `Calmness`: (int) Numerical scale for calmness  

Example:  
```csv
participant_id,stimulus_id,stimulus_order_in_experiment,stimulus,start_ts,end_ts,Emotional Valence,Safety,Satisfaction,Calmness
P002,1,9,point-1/20230418_133037.jpg,1687341166543,1687341223920,6,6,7,6
...
```

The file `data/justifications_on_top_three_choices.txt` contains the free-form comments participants provided to justify their top three image selections. After rating all 30 images, participants were shown a grid of thumbnails and asked to select their three preferred images and explain their choices. Each line follows the format:

```
[Participant ID: PXX, Image: N, Rank: M] justification text
```

Example:
```
[Participant ID: P002, Image: 11, Rank: 3] "Working" community, emotional bond with the building and because this is on my way back home. Also this green benches are connected to gathering with friends, talking, sharing and bonding.
```

### Locating files per participant

Each row in `data/trials_info.csv` corresponds to one trial. For example, participant `P002` viewing stimulus `1` (presented 9th in the experiment) has the following associated files:

- **EEG:** `data/eeg-data/P002_1.csv`
- **Fixation:** `data/fixation-data/P002_STIMULUS_1_ORDER_9.csv`
- **Pupil:** `data/pupil-data/P002_STIMULUS_1_ORDER_9.csv`

In general, EEG files follow the pattern `{participant_id}_{stimulus_id}.csv`, while fixation and pupil files follow `{participant_id}_STIMULUS_{stimulus_id}_ORDER_{stimulus_order}.csv`, where `stimulus_order` corresponds to the `stimulus_order_in_experiment` column in `data/trials_info.csv`.

## Materials

### Original images

The original image files used in our experiment are located in `data/original_images`. The table below shows how each image file in this directory maps to its corresponding image ID.

| Image ID | Path |
|---|---|
| 1 | point-1/20230418_133037.jpg |
| 2 | point-1/20230418_133256.jpg |
| 3 | point-1/20230418_133356.jpg |
| 4 | point-1/20230418_133426.jpg |
| 5 | point-1/20230418_133728.jpg |
| 6 | point-1/20230418_133916.jpg |
| 7 | point-1/20230418_134755.jpg |
| 8 | point-1/20230418_135041.jpg |
| 9 | point-1/20230418_140344.jpg |
| 10 | point-1/20230418_140607.jpg |
| 11 | point-2/20230424_135239.jpg |
| 12 | point-2/20230424_140208.jpg |
| 13 | point-2/20230424_140227.jpg |
| 14 | point-2/20230424_140441.jpg |
| 15 | point-2/20230424_140627.jpg |
| 16 | point-2/20230424_141140.jpg |
| 17 | point-2/20230424_141444.jpg |
| 18 | point-2/20230424_141503.jpg |
| 19 | point-2/20230425_165113.jpg |
| 20 | point-2/photo_2023-06-13_18-55-41.jpg |
| 21 | point-3/20230425_151402.jpg |
| 22 | point-3/20230425_160733.jpg |
| 23 | point-3/20230425_162255.jpg |
| 24 | point-3/20230425_162637.jpg |
| 25 | point-3/20230425_162852.jpg |
| 26 | point-3/20230425_162958.jpg |
| 27 | point-3/20230425_163340.jpg |
| 28 | point-3/20230425_163529.jpg |
| 29 | point-3/20230425_164135.jpg |
| 30 | point-3/20230425_164230.jpg |

### Screenshots

The directory `data/screenshots` contains another set of 30 images (1.png–30.png). Each filename corresponds directly to an image ID. These images represent the exact viewport shown to participants during the experiment and are provided to facilitate mapping the recorded gaze data to the displayed stimuli.

## Eye-tracking data

The (comma-delimited) pupil dilation files in `data/pupil-data` have 5 columns:

  - `timestamp`: (int) Unix timestamps in milliseconds
  - `BPOGX`: (int) The best position of gaze x-coordinate, relative to the top-left corner of the screenshot in pixels
  - `BPOGY`: (int) The best position of gaze y-coordinate, relative to the top-left corner of the screenshot in pixels
  - `LPD`: (float) Left eye pupil dilation in pixels
  - `RPD`: (float) Right eye pupil dilation in pixels

  Example:
  ```csv
  timestamp,BPOGX,BPOGY,LPD,RPD
  4,681,434,21.64396,20.08436
  ...
  ```

The (comma-delimited) eye fixation files in `data/fixation-data` have 4 columns:

  - `timestamp`: (int) Time in milliseconds relative to the beginning of the trial
  - `FPOGX`: (int) Fixation positions of X, relative to the top-left corner of the screenshot in pixels
  - `FPOGY`: (int) Fixation positions of Y, relative to the top-left corner of the screenshot in pixels
  - `FPOGD`: (float) Fixation duration in seconds

  **Note:** The first 5000 ms correspond to the **image viewing period**. Rows with `timestamp > 5000` were recorded while the participant was rating the image and can be excluded if only the viewing period is of interest.

  Example:
  ```csv
  timestamp,FPOGX,FPOGY,FPOGD
  487,664,467,2.45837
  ...
  ```

## EEG data

The (comma-delimited) EEG files in `data/eeg-data` have 18 columns:

- `Timestamp`: (int) Unix timestamp in milliseconds  
- `EEG 1`: (float) EEG channel 1 (Fz) in microvolts  
- `EEG 2`: (float) EEG channel 2 (C3) in microvolts  
- `EEG 3`: (float) EEG channel 3 (Cz) in microvolts  
- `EEG 4`: (float) EEG channel 4 (C4) in microvolts  
- `EEG 5`: (float) EEG channel 5 (Pz) in microvolts  
- `EEG 6`: (float) EEG channel 6 (PO7) in microvolts  
- `EEG 7`: (float) EEG channel 7 (Oz) in microvolts  
- `EEG 8`: (float) EEG channel 8 (PO8) in microvolts  
- `Accelerometer X`: (float) Accelerometer X in g  
- `Accelerometer Y`: (float) Accelerometer Y in g  
- `Accelerometer Z`: (float) Accelerometer Z in g  
- `Gyroscope X`: (float) Gyroscope X in deg/s  
- `Gyroscope Y`: (float) Gyroscope Y in deg/s  
- `Gyroscope Z`: (float) Gyroscope Z in deg/s  
- `Battery Level`: (int) Battery level in percent  
- `Counter`: (float) Sample counter  
- `Validation Indicator`: (int) Validation indicator (1 = valid, 0 = invalid/sample dropped)

Example:  
```csv
Timestamp,EEG 1,EEG 2,EEG 3,EEG 4,EEG 5,EEG 6,EEG 7,EEG 8,Accelerometer X,Accelerometer Y,Accelerometer Z,Gyroscope X,Gyroscope Y,Gyroscope Z,Battery Level,Counter,Validation Indicator
1687340939292,-15.333,-20.953,-17.089,-13.984,-2.449,-22.575,-22.588,-19.858,-0.036,0.87,-0.468,0.641,1.373,0.397,66.667,308202.0,1.0
...
```

**Note:** The first `3 * 250 = 750` samples in each file correspond to the **rest period prior to the trial**, and the remaining samples correspond to the **trial period**. 

## Citation

If you use the dataset, please cite us using this bibliographic reference:

* Kayhan Latifzadeh, Parvin Emami, Fariba Emami, Saravanakumar Duraisamy, Luis A. Leiva. 2026. **Pixels, Plants, and People: Affective Evaluation of Urban Green Spaces**. <em>In Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems</em>. https://doi.org/10.1145/3772318.3791826


```bibtex
@inproceedings{latifzadeh2026pixels,
  title={Pixels, Plants, and People: Affective Evaluation of Urban Green Spaces},
  author={Latifzadeh, Kayhan and Emami, Parvin and Fariba, Emami and Duraisamy, Saravanakumar and Leiva, Luis A.},
  booktitle={Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems},
  year={2026},
  doi={10.1145/3772318.3791826}
}
```

## Related papers

Our dataset has been used in the paper(s) listed below. If you use the dataset in your publications, please email us, and we will include your paper here.

TBA.
