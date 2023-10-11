# IACM
"Debugged" Code from (https://github.com/facebookresearch/vocoder-benchmark) with Results; original wav files from 
https://github.com/mikerapt/WaveRNN-PyTorch/tree/main/inference.

Here are the synthesized files using Wavenet vocoder with the best configuration for LJ Speech (μ-law compression on the input waveform,
as well as normal loss for the loss function) as reported in the corresponding paper:

"For each of the vocoders, we start from the original configuration provided in the respective open-source implementation.
However for WaveNet, there are different configurations that we can choose from. They vary in terms of input types and
loss functions that can be used. For the input, we can use either raw waveform or pre-processed waveform using μ-law compression. 
For the loss function, there are two different options we can choose from: Mixture of Logistics (MoL-loss) and a single Gaussian 
distribution (normal-loss). We run different versions of the WaveNet model using each of the possible configurations and report 
the one with the best performance. We found that on LJ Speech and VCTK, it is better to use μ-law compression on the input waveform, while
for LibriTTS, raw waveform input achieves the best results. For the loss function, using normal-loss helps to increase the overall
performance"
