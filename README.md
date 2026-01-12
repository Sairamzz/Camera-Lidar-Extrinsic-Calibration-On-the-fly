# Camera Lidar Extrinsic Calibration On the fly

This project was done as a part of the EECE 7150 (Autonomous Field Robotics) course at Northeastern University.

## Project Overview:

This repository implements Camera–LiDAR extrinsic calibration on the fly (Online) system based on edge alignment between LiDAR depth discontinuities and camera image edges. The system is robust to small calibration drift and can automatically recover from injected translation or rotation offsets, making it suitable for field robotic deployment.

## Methodology:

<img width="2048" height="1039" alt="image" src="https://github.com/user-attachments/assets/41335b86-77a9-4ba5-8bb7-b33dc7afec21" />

## Experiments:

### 1: Translation-only Offset

In the first experiment, the system was initialized with a pure translational error of +2 cm along the X-axis, while the rotational component of the Camera–LiDAR extrinsic calibration was kept accurate. Camera intrinsics were assumed to be correct, and no artificial rotation was introduced. This setup tests the system’s ability to recover from realistic translational drift.

<img width="1618" height="926" alt="image" src="https://github.com/user-attachments/assets/d77b23f8-b22a-4040-a285-65c5464c5946" />

The system consistently recovers from a pure translation offset, with the translation error moving towards zero while rotation remains largely stable. This is because translation induces a uniform pixel shift, the edge alignment cost decreases reliably as informative scene structure becomes available, demonstrating robust and repeatable online correction for realistic translational drift.

### 2: Rotation + Translation Offset (R + t)

In the second experiment, both translation and rotation offsets were introduced simultaneously, creating a significantly more challenging calibration scenario. Unlike the translation-only case, the system must now correct coupled errors in both position and orientation.

<img width="1618" height="926" alt="image" src="https://github.com/user-attachments/assets/739f5a61-a93e-4bc2-95a7-48a69367731e" />

Rotation introduces depth dependent, non-uniform misalignment that couples with translation error, leading to higher alignment costs, slower convergence, and reduced recovery compared to the translation-only case.

## Limitations:

- Translation is optimized before rotation to reduce search complexity and improve stability.
- The method assumes a reasonably accurate initial calibration.
- Large initial rotational errors may require offline calibration.
- Dynamic objects are not explicitly filtered and may affect edge alignment.
- Grid search prioritizes robustness and interpretability over global optimality.

## VIDEOS:

### Lidar Cam Extrinsic Calibration - Huntington Ave (Offset t)

https://youtu.be/0B9H-6nphU8

### Lidar Cam Extrinsic Calibration - Huntington Ave (Offset R+t)

https://youtu.be/WRRvF5Muypc 

### Lidar Cam Extrinsic Calibration - ISEC Bridge (Offset R+t)

https://youtu.be/XeQe7aN0VMw

## Contributors
- [Sairam Sridharan](https://github.com/Sairamzz)
- Hamza Naeem
- Gowtham Parasuram
- Ronit Shetty
