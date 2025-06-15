# Circuit Robot: An SO-ARM101 robotic arm that is trained to connect circuits

https://github.com/user-attachments/assets/512e074a-11ff-47ae-afe2-5da12c19473f

## Problem Statement
Most datasets related to training robots for electronic tasks are proprietary and closed. The confidentiality of datasets limits growth in open-source robotic intelligence.

## Solution
We present an open-source dataset to train the SO-ARM100 robotic arm from Huggingface for circuit connection. 

### Features
- **Open Alligator Clips:** Arm picks up and opens alligator clips
- **Battery Placement:** Arm picks up and drops a AA battery into a power source.
- **Turn on LED:** Arm connects power to LED lightbulb to switch on

## Datasets
- **Alligator Clips:** https://huggingface.co/datasets/Techiiot/pick_allegator_battery_final_v4
- **Battery Placement:** https://huggingface.co/ronantakizawa/battery-placement

## Models
- **Alligator Clips:** https://huggingface.co/Ganga008/allegator_place_orange
- **Battery Placement:** https://huggingface.co/ronantakizawa/battery-placement

## Approach
- **Imitation Learning:** Use a leader and follower SO-ARM101 to gather data on movements (Vision, kinetics)
-  **Training:** Train models using ACT and diffusion with 100k+ steps

## Circuit Structure 
Circuit name: Osoyoo Kids Science Lab Learning Kit: https://osoyoo.com/2018/08/22/user-manual-of-children-science-lab-learning-kit/
- **Space:** 40cm x 40cm
- **Battery:** AA Batteries 14mm x 50mm





