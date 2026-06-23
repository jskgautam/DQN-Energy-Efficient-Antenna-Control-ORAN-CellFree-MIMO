Energy-Efficient Antenna Sleep Mode Control in O-RAN Networks using Deep Reinforcement Learning: Deep Q-Network (DQN) prototype for energy-aware antenna control in O-RAN Cell-Free Massive MIMO networks.

The Problem Statement:
In Cell-Free Massive MIMO networks, many small radio units (O-RUs) work together to serve all users jointly. But running all antennas all the time is simply wasteful in terms of energy. Task: which antennas can be safely switched ON/OFF without dropping any user below their minimum guaranteed data rate?

My approach:
A parametric DQN agent that learns to decide, at every step, how many antennas each O-RU should keep active, balancing two competing objectives:
1. Serve every user with at least 20 Mbps (SE_min = 1.0 bit/s/Hz)
2. Keep total network power as low as possible

Network configuration (reduced dimension and simplified reward scheme relative to original paper): 
number of O-RUs L=2, Number of antennas per O-RUs N=4, Number of users K=2

Result:
1. ~50% power saving compared to full Antennas ON baseline (P_max = 12.0 W)
2. Spectra Efficiency violation rate reduced from 60% to ~10% over training.
3. Agent learned to use optimized number of antennas onto O-RUs

Comment on DQN implementation:
The algorithm is parametric: just changing L (number of O-RUs) in the config, to scale the problem automatically. Best performance when L is less than 4. After L = 4, we could use a more complex algorithm like Proximal Policy Optimisation (PPO), which is fully implemented in the main paper, reference below.

Reference and inspired by the 2026 research paper:
EARL: Energy-Aware Adaptive Antenna Control with Reinforcement Learning in O-RAN Cell-Free Massive MIMO Networks
Zilin Ge, Ozan Alp Topal, Irshad Ahmad Meer, Pei Xiao, Cicek Cavdar — KTH Royal Institute of Technology
arXiv:2602.12841 — February 2026
GitHub: github.com/jskgautam



Disclaimer: I tried my best to implement based on my skills and self-understanding. If you notice any errors in the implementation or have any suggestions for improvement, please notify me.
