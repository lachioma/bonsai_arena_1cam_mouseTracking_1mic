# bonsai_arena_1cam_mouseTracking_1mic
Bonsai project for arena with 1 or 2 cameras, mouse tracking, and audio recording.


![image](https://user-images.githubusercontent.com/29898879/123439527-d67d8a00-d59f-11eb-9ee7-0bf41f580aad.png)


## About timestamps
* Timestamps are all in the same clock, and are the time of the day converted into seconds (e.g. 1:24 PM -> 48241.574144 s), so that it is sequential and can be easily read as numbers by Matlab.
* To load timestamps from a csv file in Matlab, just use the following commands:
```
[filename_csv, path_csv] = uigetfile('*.csv');
T = readmatrix(fullfile(path_csv,filename_csv), ...
        'OutputType','double', 'Delimiter','');
```

* For the camera, the timestamps are for each acquired frame.
* For the microphone, the timestamps are every 100 ms. The AudioCapture node has a property named BufferLength, which I initially set to 100 ms. This means that every 100 ms (corresponding to 192000*0.1 nr. of samples), the mic audio file is updated with the new samples and a single timestamp is also stored.
The script `get_microphone_timestamps__script.m` calculates the timestamps of every sample in the audio file.

## About settings
* To change IP address of a camera, click on MjpegStream module and change its property SourceUrl.
* To change where to save files, you need to change the filename property of *all* the “sink” modules (the purple ones, on the right side of the Workflow)
