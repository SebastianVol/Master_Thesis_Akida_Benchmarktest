# Master_Thesis_Akida_Benchmarktest

The code for the thesis may be found in the two folders, which are separated into chapters of the thesis. 

Folder Keyword_Spotting

This folder contains the code for the keyword spotting benchmark.

The UltraTrail paper can be found here: 
https://www.embedded.uni-tuebingen.de/assets/publications/PalomeroBernardo_UltraTrail_TCN_Accelerator.pdf

The general procedure of the keyword spotting benchmark was:

1. Train a CNN model
2. Quantize the CNN model
3. Convert the quantized CNN model to an Akida model
(4. Optionally) Performe edge learning with previously unseen keywords

The general structure of this section is as follows: 

1. Create_Data_Set: Create the data set from the "Google Speech Command Data Set" with different processes.
2. Float_To_Int: Normalizes the respective data set created from before and casts it into uint8 
3. Edge/UltraTrail: Contains the code for the CNN to SNN conversion and training

The following abbreviations in the names of the notebooks stand for:

- No abbreviation: These notebooks belong to the procedures that utilize a data set which was created according to the
                   UltraTrail Experimental setup. 

- Edge: These notebooks belong to the procedures that utilized a balanced data set of the 10 keywords from an inital data set and
        3 newly added keywords, namely: backward, forward, and follow. Also, including 10% of "silence" and the "unknown"
        category.

- Just_Edge: These notebooks belong to the procedures that utilized a data set only containing newly added keywords,
             namely: backward, forward, and follow.
          
- SNR: These notebooks belong to the procedures that utilize a data set where the test set has a fixed SNR.

- All: These notebooks belong to the procedures that utilize a data set which uses all recordings from the 
       "Google Speech Command Data Set", even for recordings that have a shorter duration than one second. 
       
- UltraTrail: Contains the training of the models after the UltraTrail experimental setup

- EdgeModel: Contains the training of the models which were used of edge learning

- OnChip: These notebooks were run on the development kit from BrainChip. 



Folder EEG Abnormally Detection

This folder contains the code for the abnormal EEG-signal detection.

The general procedure of the EEG-signal benchmark for each fold was:

1. Train a CNN model
2. Quantize the CNN model
3. Convert the quantized CNN model to an Akida model


EEG_OnChip: This notebook contains the power measurement from the Akida model used for abnormal EEG-signal detection.
            This was run on the development kit from BrainChip.
            
Final_ChronoNet_5Fold: Contains the code of 5-fold cross-validation implementation of the ChronoNet architecture. 
A description of the architecture can be found here: https://arxiv.org/abs/1802.00308


Final_Create_Data: Contains the code of the uint8 EEG data-set creation. Note that the ChronoNet was trained with the raw 64-bit
                   float data. For the creation of the float precision data set the casting part was simply commented out. 
                   Therefor, no additional notebook is needed, since nothing else in the code changes.
                   
Final_EEG_5Fold: This notebook contains the code of the Akida SNN model which was used to detect abnormal EEG-signals. The
                 procedure in each fold is shown above. 
