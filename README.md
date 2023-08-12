# Makeit.ai
This is a generative AI tool for synthetic data. It borrows heavily from the generator-discriminator network proposes by https://github.com/LeonGuertler/draGAN
The goal here is to gather as much knowledge as possible from the experiments with generated data.
A discrete loss like the f1 score or roc score can be optimized by draGAN which converts the discrete loss into a continous loss for the generator.
The generator learns to generate samples that do not only mimic distribution of data but optimize a given metric.
During sample generation, a low depth decision tree makes a plot of the model's decision procedure. This could help the modeller focus on the most important features at generation time.
For image data, 3d channel images can be unfurled into a 1d space with the generative model trained on subsets of the data
Because the model is trained in splits, knowledge can be aggregated across splits by viewing the plots for each split
Parameters that can be tweaked:
The number of samples to generate
Early stopping conditions for when generative samples no longer improve model performance for a set maximum number of iterations
The batch size for which forward and backward passes are generated
