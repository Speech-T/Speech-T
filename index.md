# Speech-T: Transducer for Text to Speech and Beyond

## Abstract

Neural Transducer (e.g., RNN-T) has been widely used in automatic speech recognition (ASR) due to its capabilities of efficiently modeling monotonic alignments between input and output sequences and naturally supporting streaming inputs. Considering that monotonic alignments are also critical to text to speech (TTS) synthesis and streaming TTS is also an important application scenario, in this work, we explore the possibility of applying Transducer to TTS. However, it is challenging because: 1) it is difficult to trade off the emission (continuous mel-spectrogram prediction) probability and transition (ASR Transducer predicts blank token to indicate transition to next input) probability when calculating the output probability lattice in Transducer; 2) it is not easy to learn the alignments between text and speech through the output probability lattice. We propose SpeechTransducer (Speech-T for short), a Transformer based Transducer model that 1) addresses the first challenge with a new forward algorithm which separates the transition prediction from the continuous mel-spectrogram prediction when deriving the loss function of Transducer, and 2) addresses the second challenge with a diagonal constraint in the probability lattice to help the alignment learning. Experiments on LJSpeech datasets demonstrate that Speech-T is more robust than the attention based autoregressive TTS model due to its inherent monotonic alignments between text and speech and can naturally support streaming TTS with good voice quality. Furthermore, we extend Speech-T to support both TTS and ASR together for the first time, which enjoys several advantages including fewer parameters as well as streaming synthesis and recognition in a single model.

## Audio Samples

All of the audio samples use Parallel WaveGAN (PWG) as vocoder. 

<!-- *This is best furthered by the avoidance of irrational swellings and spiky projections, and by the using of careful purity of line.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt1.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt1.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st1.wav" autoplay/></audio></td>
</tr>
</tbody></table> -->


*Even the Caslon type when enlarged shows great shortcomings in this respect.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt2.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt2.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st2.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*There is a grossness in the upper finishings of letters like the c, the a, and so on.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt3.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt3.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st3.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*In short, it happens to this craft, as to others, that the utilitarian practice, though it professes to avoid ornament.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt4.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt4.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st4.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*in reading the modern figures the eyes must be strained before the reader can have any reasonable assurance.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt5.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt5.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st5.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*One of the differences between the fine type and the utilitarian must probably be put down to a misapprehension of a commercial necessity.*

<table><thead>
<tr>
<th style="text-align: center">GT+Vocoder </th>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/gt6.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/tt6.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/audio/st6.wav" autoplay/></audio></td>
</tr>
</tbody></table>


## Robustness Test

*You can call me directly at four two five seven zero three seven three four four or my cell four two five four four four seven four seven four or send me a meeting request with all the appropriate information .*

<table><thead>
<tr>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/tt2.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/st2.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*C colon backslash o one two f c p a r t y backslash d e v one two backslash oasys backslash legacy backslash web backslash HELP*

<table><thead>
<tr>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/tt3.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/st3.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*src backslash mapi backslash t n e f d e c dot c dot o l d backslash backslash m o z a r t f one backslash e x five*

<table><thead>
<tr>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/tt4.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/st4.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*copy backslash backslash j o h n f a n four backslash scratch backslash M i c r o s o f t dot S h a r e P o i n t dot*

<table><thead>
<tr>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/tt5.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/st5.wav" autoplay/></audio></td>
</tr>
</tbody></table>


*zero zero zero zero zero zero zero zero two seven nine eight F three forty zero zero zero zero zero six four two eight zero one eight*

<table><thead>
<tr>
<th style="text-align: center">TransformerTTS</th>
<th style="text-align: center">Speech-T</th>
</tr></thead><tbody>
<tr>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/tt6.wav" autoplay/></audio></td>
<td style="text-align: center"><audio controls="controls" ><source src="static/robustness/st6.wav" autoplay/></audio></td>
</tr>
</tbody></table>
