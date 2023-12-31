# IACM
"Debugged" Code from (https://github.com/facebookresearch/vocoder-benchmark) with Results; original wav files from 
https://github.com/mikerapt/WaveRNN-PyTorch/tree/main/inference as well as LJ Speech. 
There is an echo-like noise in the synthesized wav files.

Here are the synthesized files using Wavenet vocoder with the best configuration for LJ Speech (μ-law compression on the input waveform,
as well as normal loss for the loss function) as reported in the corresponding paper:

"For each of the vocoders, we start from the original configuration provided in the respective open-source implementation.
However for WaveNet, there are different configurations that we can choose from. They vary in terms of input types and
loss functions that can be used. For the input, we can use either raw waveform or pre-processed waveform using μ-law compression. 
For the loss function, there are two different options we can choose from: Mixture of Logistics (MoL-loss) and a single Gaussian 
distribution (normal-loss). We run different versions of the WaveNet model using each of the possible configurations and report 
the one with the best performance. We found that on LJ Speech and VCTK, it is better to use μ-law compression on the input waveform, while
for LibriTTS, raw waveform input achieves the best results. For the loss function, using normal-loss helps to increase the overall
performance". Actually, the loss function for WaveNet with pre-processed waveform using μ-law compression was Mixture of Logistics (MoL-loss).


I had to change the loss function for waveRNN from cross entropy to discretized_mix_logistic_loss since the waveforms were pre-processed 
using μ-law compression. In addition, cross entropy loss resulted in NaN for such input:
loss_func = F.cross_entropy if voc_model.mode == 'RAW' else discretized_mix_logistic_loss
