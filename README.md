# SLAM-Octomap-3D-Mapping
![result](result.gif)

Reconstruction of small indoor scenes from **RGB-D** input is a classic first step toward full-scale SLAM.  
This repo provides three self-contained C++ demos that turn a short sequence of color / depth frames plus ground-truth poses into richer spatial representations:

| Demo | Output | Key libs |
|------|--------|----------|
| **Point-cloud mapping** (`pointcloud_mapping.cpp`) | raw XYZ-RGB cloud + voxel-grid filtering | OpenCV, PCL |
| **Surfel mapping** (`surfel_mapping.cpp`) | MLS–smoothed surfel cloud + greedy-projection triangulation | PCL |
| **OctoMap mapping** (`octomap_mapping.cpp`) | probabilistic occupancy octree at 1 cm resolution | OctoMap |

> **Goal of my project** – Give newcomers(and myself) a minimal, readable reference on how to go **from images → pose → map** without the overhead of a full robotics framework (ROS, Pangolin, etc.).  
> All three programs are single-file and under 300 LOC each.

---

## Quick start

```bash
# 1) clone / unzip
git clone https://github.com/Aanya-Loomba/Slam-Octomap-3D-Mapping.git
cd Slam-Octomap-3D-Mapping

# 2) configure & build
mkdir build && cd build
cmake ..
make -j$(nproc)

# 3) run any demo (expects to be executed from build/)
./pointcloud_mapping    # or ./surfel_mapping / ./octomap_mapping
