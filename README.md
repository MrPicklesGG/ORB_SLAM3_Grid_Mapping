# ORB_SLAM3_Grid_Mapping
A modified version of ORB-SLAM3 which can create 2D grid map online or offline for AGV navigation.

# Instruction

## Offline
1. `./Examples/Monocular/mono_kitti Vocabulary/ORBvoc.txt Examples/Monocular/KITTI00-02.yaml /PATH_TO_KITTI/KITTI/00`
2. `pip install transforms3d`
3. `python pointCloudToGridMap2D.py`

## Online
### Dataset
1. In the terminal, run:

`roscore`.

2. Open a new terminal, run:

`rosrun ORB_SLAM3 Monosub 5 3 29 -25 48 -12 0.55 0.50 1 5`.

3. In another terminal, run:

`rosrun ORB_SLAM3 Monopub Vocabulary/ORBvoc.txt Examples/Monocular/KITTI00-02.yaml /PATH_TO_KITTI/KITTI/00 0`.

### Rosbag
1. In the terminal, run:

`roscore`.

2. Open a new terminal, run: 

`rosrun ORB_SLAM3 Monopub Vocabulary/ORBvoc.txt Examples/Monocular/mono.yaml -1 /camera/image_raw`.

3. In another terminal, run:

`rosrun ORB_SLAM3 Monosub 30 5 2 -2 2 -2 0.55 0.50 1 5`.

4. One more terminal, run:

`rosbag play /PATH_TO_ROSBAG/bags/xxx.bag -r 0.5`.

### Your Own Camera
1. In the terminal, run:

`roscore`.

2. Open a new terminal, run: 

`rosrun ORB_SLAM3 Monopub Monopub Vocabulary/ORBvoc.txt Examples/Monocular/mono.yaml -1 /usb_cam/image_raw`.

3. In another terminal, run:

`rosrun ORB_SLAM3 Monosub 30 5 2 -2 2 -2 0.55 0.50 1 5`.

4. One more terminal, run:

`roslaunch usb_cam-test.launch`.
