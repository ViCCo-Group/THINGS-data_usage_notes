```python
from os.path import join as pjoin
import pandas as pd
```

# THINGS-fMRI usage notes

For a detailed description of the data and the procedures that generated it, see [the THINGS-data preprint](https://doi.org/10.1101/2022.07.22.501123).

## Single trial responses

The single trial responses are arguably the easiest way to analyze the THINGS-fMRI data. It contains the magnitude of the fMRI response to each stimulus in each voxel with a single number. The single trial responses are provided in two formats: a) In table format, b) in volumetric format.

### Table format

Besides the fMRI response data, the table format contains metadata about each voxel (such as noise ceilings, pRF parameters, regions of interest) and about the stimulus (such as image file name, trial type, run and session). 


```python
# Let's assume you've downloaded the THINGS-fMRI data to this directory
basedir = '/Users/olivercontier/bigfri/openneuro/THINGS-data/THINGS-fMRI/derivatives'
# and the single trial responses in table format are in this subdirectory
betas_csv_dir = pjoin(basedir, 'betas_csv')
# and that you're interested in the data for the first subject
sub = '01'
```

The **ResponseData.h5** files contain the actual single trial responses. Rows are voxels, columns are trials.


```python
data_file = pjoin(betas_csv_dir, f'sub-{sub}_ResponseData.h5')
responses = pd.read_hdf(data_file)  # this may take a minute
print('Single trial response data')
responses.head()
```

    Single trial response data





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>voxel_id</th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>...</th>
      <th>9830</th>
      <th>9831</th>
      <th>9832</th>
      <th>9833</th>
      <th>9834</th>
      <th>9835</th>
      <th>9836</th>
      <th>9837</th>
      <th>9838</th>
      <th>9839</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>-0.089022</td>
      <td>0.041923</td>
      <td>0.169130</td>
      <td>-0.075151</td>
      <td>0.015963</td>
      <td>-0.010098</td>
      <td>-0.012468</td>
      <td>0.084902</td>
      <td>0.091878</td>
      <td>...</td>
      <td>0.024178</td>
      <td>-0.029775</td>
      <td>0.099759</td>
      <td>0.006796</td>
      <td>-0.044169</td>
      <td>0.018878</td>
      <td>-0.057514</td>
      <td>0.055157</td>
      <td>-0.036201</td>
      <td>-0.068705</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>-0.062508</td>
      <td>-0.037973</td>
      <td>-0.009769</td>
      <td>0.082478</td>
      <td>0.056631</td>
      <td>-0.015929</td>
      <td>-0.027017</td>
      <td>0.054912</td>
      <td>0.017544</td>
      <td>...</td>
      <td>-0.071025</td>
      <td>0.035286</td>
      <td>0.066276</td>
      <td>-0.092530</td>
      <td>-0.074624</td>
      <td>0.006528</td>
      <td>0.005477</td>
      <td>0.002302</td>
      <td>0.074685</td>
      <td>-0.096532</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>-0.070807</td>
      <td>-0.019326</td>
      <td>-0.019546</td>
      <td>-0.060038</td>
      <td>-0.024878</td>
      <td>0.052750</td>
      <td>0.163108</td>
      <td>0.037861</td>
      <td>-0.073247</td>
      <td>...</td>
      <td>0.045679</td>
      <td>0.075059</td>
      <td>-0.020386</td>
      <td>-0.034966</td>
      <td>-0.027783</td>
      <td>0.011068</td>
      <td>-0.025219</td>
      <td>0.012350</td>
      <td>0.029529</td>
      <td>0.006157</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0.006218</td>
      <td>0.016355</td>
      <td>-0.075845</td>
      <td>-0.109495</td>
      <td>-0.007062</td>
      <td>0.144785</td>
      <td>0.086463</td>
      <td>-0.047257</td>
      <td>0.011348</td>
      <td>...</td>
      <td>-0.050225</td>
      <td>0.016627</td>
      <td>0.083943</td>
      <td>-0.038645</td>
      <td>-0.014257</td>
      <td>0.050435</td>
      <td>0.032841</td>
      <td>-0.036794</td>
      <td>-0.000256</td>
      <td>0.033482</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>-0.014344</td>
      <td>-0.029792</td>
      <td>0.136358</td>
      <td>-0.118176</td>
      <td>0.007145</td>
      <td>0.036102</td>
      <td>0.036816</td>
      <td>0.015313</td>
      <td>0.035015</td>
      <td>...</td>
      <td>-0.104036</td>
      <td>-0.020143</td>
      <td>0.063932</td>
      <td>-0.080900</td>
      <td>0.010575</td>
      <td>-0.015148</td>
      <td>-0.085487</td>
      <td>0.118670</td>
      <td>0.073392</td>
      <td>-0.014972</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 9841 columns</p>
</div>



The **VoxelMetadata.csv** files contain additional information about each voxel, such as membership to ROIs, reliability measures, and noise ceilings.


```python
vox_f = pjoin(betas_csv_dir, f'sub-{sub}_VoxelMetadata.csv')
voxdata = pd.read_csv(vox_f)
voxdata.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>voxel_id</th>
      <th>subject_id</th>
      <th>voxel_x</th>
      <th>voxel_y</th>
      <th>voxel_z</th>
      <th>nc_singletrial</th>
      <th>nc_testset</th>
      <th>splithalf_uncorrected</th>
      <th>splithalf_corrected</th>
      <th>prf-eccentricity</th>
      <th>...</th>
      <th>lSTS</th>
      <th>rSTS</th>
      <th>lPPA</th>
      <th>rPPA</th>
      <th>lRSC</th>
      <th>rRSC</th>
      <th>lTOS</th>
      <th>rTOS</th>
      <th>lLOC</th>
      <th>rLOC</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>39</td>
      <td>33</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-0.030530</td>
      <td>-0.062982</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>39</td>
      <td>34</td>
      <td>1.102513</td>
      <td>11.799193</td>
      <td>0.070108</td>
      <td>0.131029</td>
      <td>4.941197</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>39</td>
      <td>35</td>
      <td>2.134454</td>
      <td>20.743164</td>
      <td>0.121099</td>
      <td>0.216036</td>
      <td>11.064742</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>39</td>
      <td>36</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-0.040901</td>
      <td>-0.085290</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>40</td>
      <td>33</td>
      <td>0.446367</td>
      <td>5.105714</td>
      <td>0.034924</td>
      <td>0.067491</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 41 columns</p>
</div>




```python
print('available voxel metadata:\n', voxdata.columns.to_list())
```

    available voxel metadata:
     ['voxel_id', 'subject_id', 'voxel_x', 'voxel_y', 'voxel_z', 'nc_singletrial', 'nc_testset', 'splithalf_uncorrected', 'splithalf_corrected', 'prf-eccentricity', 'prf-polarangle', 'prf-rsquared', 'prf-size', 'V1', 'V2', 'V3', 'hV4', 'VO1', 'VO2', 'LO1 (prf)', 'LO2 (prf)', 'TO1', 'TO2', 'V3b', 'V3a', 'lEBA', 'rEBA', 'lFFA', 'rFFA', 'lOFA', 'rOFA', 'lSTS', 'rSTS', 'lPPA', 'rPPA', 'lRSC', 'rRSC', 'lTOS', 'rTOS', 'lLOC', 'rLOC']


The voxel indices can be used to reconstruct a volume, e.g. for visualizing results obtained from the single trial responses. Alternatively, the brain mask can be used for that purpose (see below). Membership of each voxel to the available ROIs is dummy coded, e.g. in `voxdata["V1"]` or `voxdata["rFFA"]`. The population receptive field parameters are encoded in the following columns: `prf-eccentricity`, `prf-polarangle`, `prf-size`, and `prf-rsquared`. Finally, different reliability estimates are available in the columns: `nc_testset`, `nc_singletrial`, `splithalf_uncorrected`, and `splithalf_corrected`.

The **StimulusMetadata.csv** files contain information about the file name of the image shown in each trial, which run and session a given trial occured in, and the trial_type. 


```python
# Stimulus metadata
stim_f = pjoin(betas_csv_dir, f'sub-{sub}_StimulusMetadata.csv')
stimdata = pd.read_csv(stim_f)
stimdata.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>trial_type</th>
      <th>session</th>
      <th>run</th>
      <th>subject_id</th>
      <th>trial_id</th>
      <th>stimulus</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>train</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>dog_12s.jpg</td>
    </tr>
    <tr>
      <th>1</th>
      <td>train</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>mango_12s.jpg</td>
    </tr>
    <tr>
      <th>2</th>
      <td>train</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>spatula_12s.jpg</td>
    </tr>
    <tr>
      <th>3</th>
      <td>test</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>3</td>
      <td>candelabra_14s.jpg</td>
    </tr>
    <tr>
      <th>4</th>
      <td>train</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>panda_12s.jpg</td>
    </tr>
  </tbody>
</table>
</div>



> 🚨 Trial types
>
> The THINGS-fMRI experiment presented participants with three different trial types:
> - `train`: Participants passively viewed an object image.
> - `test`: Same as train, but these trials belonged to a set of 200 images which were presented in each session. It's main purpose is to allow for estimating the reliability of the single trial responses in a given voxel.
> - `catch`: Participants saw a non-object image and responded with a button press. This was included to ensure participants were engaged throughout the experiment.
>
> Note: Catch trials are excluded from the single trial responses in table format as they are likely not of interest for most applications. However, catch trials are included in the volumetric format in order to make it possible to account for them in analyses.

### Volumetric format

## Raw data

## ICA noise regressors

## Regions of interest

## Brain masks

## Cortical flat maps


```python

```
