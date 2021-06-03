+++
date = 2021-06-03T23:35:23+08:00
title = "Speech-T: Transducer for Text to Speech and Beyond"
tags = ["Speech"]
categories = ["Speech synthesis"]

+++

## Abstract

Neural Transducer (e.g., RNN-T) has been widely used in automatic speech recognition (ASR) due to its capabilities of efficiently modeling monotonic alignments between input and output sequences and naturally supporting streaming inputs. Considering that monotonic alignments are also critical to text to speech (TTS) synthesis and streaming TTS is also an important application scenario, in this work, we explore the possibility of applying Transducer to TTS. However, it is challenging because: 1) it is difficult to trade off the emission (continuous mel-spectrogram prediction) probability and transition (ASR Transducer predicts blank token to indicate transition to next input) probability when calculating the output probability lattice in Transducer; 2) it is not easy to learn the alignments between text and speech through the output probability lattice. We propose SpeechTransducer (Speech-T for short), a Transformer based Transducer model that 1) addresses the first challenge with a new forward algorithm which separates the transition prediction from the continuous mel-spectrogram prediction when deriving the loss function of Transducer, and 2) addresses the second challenge with a diagonal constraint in the probability lattice to help the alignment learning. Experiments on LJSpeech datasets demonstrate that Speech-T is more robust than the attention based autoregressive TTS model due to its inherent monotonic alignments between text and speech and can naturally support streaming TTS with good voice quality. Furthermore, we extend Speech-T to support both TTS and ASR together for the first time, which enjoys several advantages including fewer parameters as well as streaming synthesis and recognition in a single model.

## Audio Samples

All of the audio samples use Parallel WaveGAN (PWG) as vocoder. 

*Were the leaders in this luckless change, though our own Baskerville, who was at work some years before them, went much on the same lines.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="../audio/fastspeech2/audio/gt_recording_2/0000000004.mp3" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="../audio/fastspeech2/audio/gt_pwg_2/0000000004.mp3" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="../audio/fastspeech2/audio/transtts_2/0000000004.mp3" autoplay/></audio></td>
</tr>
</tbody></table>

