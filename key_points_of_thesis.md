## Teleoperation System
Two sets of robot arms(Almost the same version)
Use joint-space mapping for teleoperation
3D printed component
## Imitation Learning Algorithm
Action Chunk: Sequences of actions and execute as a unit
Predict k timesteps within a time
    1. Reduce effective horizon
    2. Tackle temporally correlated confounders
Temporal ensembling
> Implement with Transformer/Train as conditinal VAE
**Action Chunk with Transformers (ACT)**

Low-cost system



**Tackle this from both Hardware and Software**
BC -> Compounding Errors -> Solution: Allow additional on-policy interactions and expert corrections.

Expert annotation(time consuming)/inject noise to obtain more data(result in failure)

**Five Principles of system**
    1. Low-cost
    2. Vesatile: can be applied in a wide range of fine manipulation tasks
    3. User-friendly
    4. Repairable
    5. Easy to build

VIperX arm: Modular. Dynamixel motors...

3D printed fingers/Grip tape -> Good visibility/Robust Grip


**Task-space Mapping**
Leader -> WidowX | Follower -> ViperX
> Joint-space mapping

**Pipeline of training ACT**
    1. Collect human demonstrations (Joint Positions) as the leader
    2. Observations: Followers' current joint positions/image feed from 4 cameras

**Action Chunking and Temoral Ensemble**
    1. Pixel-to-action polices
    2. Every k steps, the agent receives an abservation -> generates the next k actions.
    3. Query the policy at every timestep
**Focus on regions where high precision matters**
    1. Train policy as a generative model (Conditional Variational Autoencoder)

**Model**
    1. Encoder: predicts the mean and variance of the style variable z's distribution
    2. Decoder: the policy, conditions to predict the action sequence.

    Transformer -> synthesize information and generate new sequences
    Encode
        input: current joint positions, demonstration data (target action sequence with length k)


**Processing Flow**
    1. Policy process the images with ResNet18 backbones. (480*640*3 -> 15*20*512)
    2. Flatten (15*20*512 -> 300*51)