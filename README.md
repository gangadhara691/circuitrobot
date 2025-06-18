# Circuit Robot: An SO-ARM101 robotic arm trained to build electrical circuits

Team: Sandeep Kodam, Gangadhara Naga Sai G, Hildelith Leyser, Ronan Takizawa, Thanh Trung M.

Placed 1st for Hugging Face robotics hackathon in the Japan region and 4th globally. 

https://github.com/user-attachments/assets/512e074a-11ff-47ae-afe2-5da12c19473f

## Problem Statement
Most datasets related to training robots for electronic tasks are proprietary and closed. Proprietary restrictions limit the growth of open-source robotic intelligence.

## Solution
We present an open-source dataset to train the SO-ARM100 robotic arm from Huggingface for circuit connection. 

## Features
- **Open Alligator Clips:** Arm picks up and opens alligator clips
- **Battery Placement:** Arm picks up and drops a AA battery into a power source.
- **Turn on LED:** Arm connects power to LED lightbulb to switch on

## Datasets
- **Alligator Clips:** https://huggingface.co/datasets/LeRobot-worldwide-hackathon/141-Electrify-open_alligator
- **Battery Placement:** https://huggingface.co/datasets/LeRobot-worldwide-hackathon/141-Electrify-insertbattery

## Models
- **Alligator Clips:** https://huggingface.co/Ganga008/allegator_place_orange
- **Battery Placement:** https://huggingface.co/ronantakizawa/battery-placement

## Approach
- **Data Collection:** For battery placement and alligator clip opening, we collected 35 episodes of data, where each episode collected vision and kinetic information from the SO-ARM101
- **Imitation Learning:** We used a leader and follower SO-ARM101 to gather data on movements using its built-in camera and rotary parts (Vision, Kinetics).
- **Environment Setup**: For each episode, the arm was placed in a 40 cm x 40cm space.
  - For the battery placement, the battery was 14mm x 50mm, and its center was placed at (30cm, 20cm), and the battery holder was at (10cm, 20cm). The circuit used was called [Osoyoo Kids Science Lab Learning Kit](https://osoyoo.com/2018/08/22/user-manual-of-children-science-lab-learning-kit/). Each object in the item was taped to keep in place.
  - For the alligator clip opening, the alligator clip was at (30cm, 20cm) and the terminal at (10cm, 20cm). The clip was roughly 3cm x 2cm
- **Training:** We trained models using ACT and Diffusion learning methods based on the [training script provided by Huggingface](https://huggingface.co/docs/lerobot/il_robots#train-a-policy). Training was run on A100 and H100 GPUs.
- **Training Hyperparameters:**
  - **ACT:** 6 transformer blocks, 512 embedding dimension, 8 attention heads, 1e–4 learning rate, 64 as batch size, 100k steps of learning
  - **Diffusion:** 100 diffusion steps, 64 as batch size, 200k steps of learning
- **Evaluation:** The performance of building electrical circuits was not formally evaluated, but was assessed by loading the trained model onto a single SO-ARM101 using the Lerobot [evaluation script](https://huggingface.co/docs/lerobot/il_robots#train-a-policy). The battery placement had a low accuracy (10% accuracy), and the alligator clip opening had a medium accuracy (40% accuracy). The model trained on ACT demonstrated better results than diffusion, and the arm displayed more fluid motions. We think ACT had better motion than Diffusion because Diffusion overwhelmed the processor on the arm.
- **Next Steps:** With the limited time, we demonstrated a proof-of-concept robotic arm that can build electrical circuits. The arm demonstrated the ability to place batteries, open alligator clips, and construct functional electrical circuits that can power light bulbs. Since these activities were completed with low accuracy, we cannot conclude that our project was functional. To further improve our project, we need to collect more episodes to train a better model, and we need to color-code alligator clips so the SO-ARM101 can detect differences in objects more clearly (Green clips blended with the green colored terminal).






