# ORB-SLAM3

This repository is a modified version of [ORB_SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)

---

## Summary
- Succesfully tested in **Debian GNU/Linux 12 (bookworm)** and **ROS2 Humble Hawksbill**(with OpenCV 4.2.0)
- Updated from C++11 to C++14
- Fixed unexpected <span style="color:red">error</span> when start **STEREO** mode with **Rectified** camera type
- Fixed : SegmentationFault ; occurring on saving KeyFrameTrjectory.txt
- In **mono_tum.cc**, added support for toggling the Pangolin viewer via a 4th CLI argument (`true` or `false`)

## Modifications made:
- Updated CMakeLists.txt to use cmake version - 3.25+
- Updated CMakeLists.txt to incorporate requried libraries such as DBoW2, g2o, & Sophus correctly
- Updated file paths in .h files towards required libraries
- In **mono_euroc.cc** around line 83 change the last argument of the function to true \
"ORB_SLAM3::System SLAM(argv[1],argv[2],ORB_SLAM3::System::MONOCULAR, true);" \
which is false by default and then rebuild the package.
- Uncommented some lines in file : System.cc, function : System::Shutdown(), around line : 517
- Added CLI support for bUseViewer in mono_tum.cc: parsed at line 39, declared at line 52, and passed to the System constructor at line 59.

## How to build
Clone the repository:
```
git clone https://github.com/eshan-sud/ORB_SLAM3 ORB_SLAM3
```

Install same required dependencies as original version. Then,
Execute:
```
cd ORB_SLAM3
chmod +x build.sh
./build.sh
```
This will create **libORB_SLAM3.so**  at *lib* folder and the executables in *Examples* folder.
