# Makeit.ai
This is a generative AI tool for synthetic data. It borrows it's core architecture from the generator-discriminator network proposed by https://github.com/LeonGuertler/draGAN
A discrete loss like the f1 score or roc score can be optimized by draGAN which converts the discrete loss into a continous loss for the generator.
The generator learns to generate samples that do not only mimic distribution of data but optimize a given metric.
During sample generation, a low depth decision tree makes a plot of the model's decision procedure. This could help the modeller focus on the most important features at generation time.
For image data, 3d channel images can be unfurled into a 1d space with the generative model trained on subsets of the data.
Because the model is trained in splits, knowledge can be aggregated across splits by viewing the plots for each split
Parameters that can be tweaked:
The number of samples to generate,
Early stopping conditions for when generative samples no longer improve model performance for a set maximum number of iterations,
The batch size for which forward and backward passes for generator and discriminator networks are computed.
Knowledge from low depth decision trees can help optimize downstream workloads by focusing more on the strongest relationships and leveraging custom feature importance plots within the generation loop (just below the tree plots)
This generative scheme is especially useful for imbalanced datasets like fault detection settings or anomaly detection<img width="528" alt="Screenshot 2023-09-29 005132" src="https://github.com/Israel-Orere/Makeit.ai/assets/83463364/23c0f606-7ef1-4340-a507-b59595bf8301">
<img width="602" alt="Screenshot 2023-09-29 005053" src="https://github.com/Israel-Orere/Makeit.ai/assets/83463364/3b65942a-3288-4429-8c1f-4f9048d99616">


Update: Archhitecture modifications
An adversarial discriminator module has been added to the generation pipeline. The  adversarial module minimizes the distribution shift between the real and synthetic data. The lamda parameter controls the level of this minimization. Higher lamda values mean higher penalties/losses for the generator for generating data with a distribution far removed from the real data. This might have the negative impact of reducing the base model's performance on the downstream task. 
Hence, the generator must solve two problems: 1. generate data that improves performance on doenstream task. 2. Generated data distribution must be close enough to real data distribution to a tolerance limit imposed by the user-supplied lamda parameter.
