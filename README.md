# Gaze-Tracking-and-Point-Estimation-using-Intel-DL-Workbench---OpenVINO-Toolkit-Intel-DevCloud
# Computer Pointer Controller
With changing advancements, controls are swapping out with new methodology each day like first touch then came gesture later on motion capture and now presenting gaze control- revolutionizing the way you control your screen. Eye control a dream innovation come true-> who wants to hinder his movie experience with notifications pop-ups on screen while playing-> So now just gaze and swwipe it out. This is a buding innovation project with currently dealing with the gaze co-ordinate-> so the next step is to map those cordinates to your cursor position so that hand control will no longer be needed. This idea at present detects your face-> identifies facial features-> plots a three dimensional real world cordinate graph and gaze model  process out the x and y cordinate of that awesome plot. Amazed! You'll be once it come out in the market. 





## Project Set Up and Installation
>Setup the OpenVINO as guided at the Project set up page of Project3 Page1:
set up completely & initialize openVINO environment in a terminal


>Now setup a virual environment for the project:
$ python3 -m venv intel-iot
$ source intel-iot/bin/activate
(intel-iot) $ pip install -r requirements.txt


>Now, from inside (intel-iot) virtual environment-> Clone or Download the Project repository into the desired folder| extract the zip file 
>Starting with downloading required model for the Project:
1.
python3 /opt/intel/openvino/deployment_tools/open_model_zoo/tools/downloader/downloader.py --name landmarks-regression-retail-0009 --precision FP32 -o /home/aren/Downloads/project3/src/models
2.
python3 /opt/intel/openvino/deployment_tools/open_model_zoo/tools/downloader/downloader.py --name head-pose-estimation-adas-0001 --precision FP32 -o /home/aren/Downloads/project3/src/models
3.
python3 /opt/intel/openvino/deployment_tools/open_model_zoo/tools/downloader/downloader.py --name gaze-estimation-adas-0002 --precision FP32 -o /home/aren/Downloads/project3/src/models
4.
python3 /opt/intel/openvino/deployment_tools/open_model_zoo/tools/downloader/downloader.py --name face-detection-adas-binary-0001 --precision FP32-INT1 -o /home/aren/Downloads/project3/src/models





## Demo
How to run a basic demo of our Project:
> On WebCam, I'll insist you to run this on webcam because since we made local setup what stops us from operating on real world unlike workspace's camera issue:
python3 main.py --facedetectionmodel /home/aren/Downloads/project3/src/models/intel/face-detection-adas-binary-0001/FP32-INT1/face-detection-adas-binary-0001 --faciallandmarkmodel /home/aren/Downloads/project3/src/models/intel/landmarks-regression-retail-0009/FP16/landmarks-regression-retail-0009 --headposeestimationmodel /home/aren/Downloads/project3/src/models/intel/head-pose-estimation-adas-0001/FP16/head-pose-estimation-adas-0001 --gazeestimationmodel /home/aren/Downloads/project3/src/models/intel/gaze-estimation-adas-0002/FP16/gaze-estimation-adas-0002 --input cam --counter 10 --prob_threshold 0.5 --mouseprecision high --mousespeed fast --facedetectionmodel_show True --headposeestimationmodel_show True --faciallandmarkmodel_show True --gazeestimationmodel_show True
>Upon the video provided official and made for testing:
python3 main.py --facedetectionmodel /home/aren/Downloads/project3/src/models/intel/face-detection-adas-binary-0001/FP32-INT1/face-detection-adas-binary-0001 --faciallandmarkmodel /home/aren/Downloads/project3/src/models/intel/landmarks-regression-retail-0009/FP32/landmarks-regression-retail-0009 --headposeestimationmodel /home/aren/Downloads/project3/src/models/intel/head-pose-estimation-adas-0001/FP32/head-pose-estimation-adas-0001 --gazeestimationmodel /home/aren/Downloads/project3/src/models/intel/gaze-estimation-adas-0002/FP32/gaze-estimation-adas-0002 --input bin/test.mp4 --counter 10 --prob_threshold 0.5 --mouseprecision high --mousespeed fast --facedetectionmodel_show True --headposeestimationmodel_show True --faciallandmarkmodel_show True --gazeestimationmodel_show True





## Documentation
Command to start the Project:
python3 main.py [-h] --facedetectionmodel FACEDETECTIONMODEL
               [--facedetectionmodel_show FACEDETECTIONMODEL_SHOW]
               --faciallandmarkmodel FACIALLANDMARKMODEL
               [--faciallandmarkmodel_show FACIALLANDMARKMODEL_SHOW]
               --headposeestimationmodel HEADPOSEESTIMATIONMODEL
               [--headposeestimationmodel_show HEADPOSEESTIMATIONMODEL_SHOW]
               --gazeestimationmodel GAZEESTIMATIONMODEL
               [--gazeestimationmodel_show GAZEESTIMATIONMODEL_SHOW] --input
               INPUT --counter COUNTER [--cpu_extension CPU_EXTENSION]
               [--device {CPU,GPU,FPGA,VPU}] [--prob_threshold PROB_THRESHOLD]
               --mouseprecision {high,medium,low} --mousespeed
               {fast,medium,slow}


arguments documentation:
  -h, --help            show this help message and exit
  --facedetectionmodel FACEDETECTIONMODEL
                        path to face detection model file with no extension.
  --facedetectionmodel_show FACEDETECTIONMODEL_SHOW
                        FLAG for showing output from face detection model
  --faciallandmarkmodel FACIALLANDMARKMODEL
                        path to facial landmark detection model file with no
                        extension.
  --faciallandmarkmodel_show FACIALLANDMARKMODEL_SHOW
                        FLAG for showing output from facial landmark detection
                        model
  --headposeestimationmodel HEADPOSEESTIMATIONMODEL
                        path to head pose estimation model file with no
                        extension.
  --headposeestimationmodel_show HEADPOSEESTIMATIONMODEL_SHOW
                        FLAG for showing output from head pose estimation
                        model
  --gazeestimationmodel GAZEESTIMATIONMODEL
                        path to gaze estimation model file with no extension.
  --gazeestimationmodel_show GAZEESTIMATIONMODEL_SHOW
                        FLAG for showing output from gaze estimation model
  --input INPUT         path to video file, 'cam' for webcam-0
  --counter COUNTER     number of frames spared when for making the mouse
                        movement
  --cpu_extension CPU_EXTENSION
                        extesion full path if any, CPU only allowed
  --device {CPU,GPU,FPGA,VPU}
                        device to use for inference
  --prob_threshold PROB_THRESHOLD
                        probability for model detections
  --mouseprecision {high,medium,low}
                        precision for the mouse
  --mousespeed {fast,medium,slow}
                        Speed of the mouse when moving





## Benchmarks
benchmark results of running our model on multiple hardwares and multiple model precisions; these score was made over the frames captured by webcam live: 
 FACIAL_PRES  HEAD_PRES LANDMARK_PRES  GAZE_PRES  LOAD_TIME INFRN_TIME     FPS
   FP32-INT1       FP16          FP32  FP32-INT8   1.129078  0.030706  28.756701
   FP32-INT1       FP16          FP16  FP32-INT8   1.125621  0.030946  28.507840
   FP32-INT1       FP32          FP16  FP32-INT8   1.083417  0.030947  28.493245
   FP32-INT1       FP32          FP16       FP32   0.753548  0.031025  28.440205
   FP32-INT1       FP16          FP32       FP32   0.880105  0.031221  28.347590
   FP32-INT1  FP32-INT8     FP32-INT8  FP32-INT8   1.434808  0.031249  28.306473
   FP32-INT1       FP16     FP32-INT8  FP32-INT8   1.185536  0.031261  28.313425
   FP32-INT1  FP32-INT8          FP32  FP32-INT8   1.384385  0.031394  28.039110
   FP32-INT1  FP32-INT8     FP32-INT8       FP16   1.290341  0.031411  28.153285
   FP32-INT1  FP32-INT8          FP16       FP16   1.124802  0.031451  28.106844
   FP32-INT1  FP32-INT8          FP16  FP32-INT8   1.409338  0.031532  27.865519
   FP32-INT1       FP32     FP32-INT8  FP32-INT8   1.218725  0.031610  27.858197
   FP32-INT1       FP16     FP32-INT8       FP16   0.975494  0.031688  27.924223
   FP32-INT1  FP32-INT8          FP32       FP32   1.052218  0.031758  27.802485
   FP32-INT1       FP16     FP32-INT8       FP32   0.879785  0.031861  27.786306
   FP32-INT1  FP32-INT8     FP32-INT8       FP32   1.133898  0.031947  27.707372
   FP32-INT1  FP32-INT8          FP32       FP16   1.176758  0.032123  27.490473
   FP32-INT1       FP32          FP16       FP16   0.897963  0.032126  27.624159
   FP32-INT1       FP16          FP32       FP16   0.907482  0.032213  27.481284
   FP32-INT1       FP32          FP32       FP16   0.827884  0.032243  27.466822
   FP32-INT1  FP32-INT8          FP16       FP32   1.089703  0.032285  27.396703
   FP32-INT1       FP16          FP16       FP32   0.927107  0.032581  27.167603
   FP32-INT1       FP32          FP32       FP32   0.814021  0.034655  25.624704
   FP32-INT1       FP32     FP32-INT8       FP32   0.737817  0.038746  22.931412
   FP32-INT1       FP32     FP32-INT8       FP16   0.974489  0.038899  22.904247
   FP32-INT1       FP16          FP16       FP16   0.986387  0.040078  22.130213
   FP32-INT1       FP32          FP32  FP32-INT8   1.166512  0.043026  20.669722





## Results
>We have been getting better result over the figure of FP32 at all four model
>We need to understand what happened-> ideally FP16 is fast but no here because-> FP16 ut the tensor to half and got agility out of GPU computation speed-> but here working with CPU which is made to work smoth with full float precision FP32 inference is better here
>Callibre of a device very well defines the processing speed, power and agility, here I worked inside Virtual Machine 
>FP32 is calliberately CPU oriented more of optimized as per performance-> got better result with this precision
>I didn't got my hand over compute stick to test whether the project is inferencing at par on FP32 on it or is it FP16 or INT8 wining the race there





### Edge Cases
certain situations that will break your inference flow: 
>lighting changes: at off light conditions- in a darker setting model will fail to detection -> face, facial landmark, head position and gaze on the screen 
>multiple people in the frame: again in such a nullifying condition the model fails to validate all four detail recorded and corporately work together for gaze detection 
some of the edge cases encountered:
>with frequent diming of lightning inferecing freezes to work properly
>frame skip trade off can be very well scence at lower inferencing
>gaze cordinates doesn't changes untill rest three models properly specifies that new values or models are properly running & recording new states
>at present it can't work over multiples faces so  basically it captures a single face whose marks with greater accuracy than other can be recorded and process out whole thing for that single one
