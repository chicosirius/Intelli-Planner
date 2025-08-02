# Intelli-Planner

The repo is the official implementation for our AAAI2026 submission: **Intelli-Planner: Advancing Participatory and Customized Urban Planning with Knowledge-Enhanced Reinforcement Learning**.

## Overview

![](pic/framework.jpg)

To integrate the world knowledge capabilities of large language model (LLM) with the search proficiency of reinforcement learning (RL), we propose a **stylized urban planning framework**. This framework, based on the Actor-Critic (AC) paradigm, utilizes LLM for planning objectives formulation, enhances policy network through single-agent guidance, and obtains schemes satisfying various stakeholders through multi-agents scoring. Additionally, we introduce a five-dimensional evaluation system for a comprehensive and detailed quantification assessment of the final planning scheme.

Specifically, the high-level objectives are first provided by LLM based on the given planning style and basic demographic and geographic statistical data of the community. Then, we train our Intelli-Planner through RL enhanced with LLM’s knowledge to learn according to the given objectives. We propose a five-dimensional evaluation system to measure the quality of the final scheme, including *service*, *ecology*, *economy*, *equity*, and *satisfaction* with simulated different stakeholders. The ultimate framework achieves outstanding planning outcomes in three communities with different styles in Beijing, Chicago, and Madrid.

## Data

- The land parcels data in **Beijing, Chicago and Madrid** used in this paper are in `\data`.
- Or you can select the community block of your interest using OpenStreetMap (OSM), QGIS, or other software, and call `\utils\data_preprocessing.py` for preprocessing. The visualization of plots can be rendered by calling `\utils\visualize_regions.py`.

<img src="pic/land_statistics.jpg" style="zoom:60%;" />

![](pic/cities.jpg)

## Usage

#### Environment

- Python >= 3.9
- torch == 2.1.0 + cu118

#### Dependencies

1. Install Pytorch with the correct CUDA version.
2. Use the `pip install -r requirements.txt` command to install all of the Python modules and packages used in this project.

#### Model Training and Inference

1. Add your OPENAI API KEY into `\LLM\agent.py`.

2. Here, we take the Beijing community as an example for model training.

   a. Combined with the demographic and geographic statistics of Beijing's community, as well as our desired planning style, we can obtaine the planning objectives for each functional type. See the last section for specific prompts.

   b. Modify the `'shp_file_path'`, `'geo_info_path'`, and `'city_name'`  in the `'train.py'` file to BEIJING.

   c. Fill in our planning goals in the `envs/urban_config.py`.

   ```
   python train.py
   ```


3. Finally, we were able to get the final planning results and indicators in the `\ckpt` folder.

## Results

The table below illustrates the results of our framework's planning in three neighborhoods: Beijing, Chicago, and Madrid.
![](pic/results.jpg)


We set different planning styles in the Beijing community to generate planning schemes based on various demand orientations:

![](pic/style.jpg)

