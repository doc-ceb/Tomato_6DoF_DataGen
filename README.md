# Tomato_6DoF_DataGen

Generate ground-truth data for tomato pose estimation using a stereo rig, COLMAP, FoundationStereo, and FoundationPose.

## Pipeline overview

1. **Collect stereo observations** of a tomato plant from multiple viewpoints.
2. **Estimate camera-to-camera relative poses** with COLMAP from the captured observations.
3. For selected distinct tomato views:
   - run **FoundationStereo** on the stereo pair to recover a point cloud,
   - provide a scanned tomato model + reference-image mask + reconstructed point cloud to **FoundationPose**,
   - obtain a candidate tomato pose with respect to that camera.
4. **Repeat pose registration for at least 3 views**.
5. **Optimize the tomato world pose** by combining:
   - relative camera poses from COLMAP, and
   - tomato poses estimated in each camera frame.
