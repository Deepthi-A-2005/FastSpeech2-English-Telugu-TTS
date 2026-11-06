# FastSpeech 2 English and Telugu Text-to-Speech

Bilingual TTS implementation using separate FastSpeech 2 configurations for English and Telugu with HiFi-GAN.

## Architecture

Text -> Tokenization -> FastSpeech 2 Encoder -> Variance Adaptor -> Length Regulator -> Decoder -> Mel Spectrogram -> HiFi-GAN -> Audio.

## Datasets

- English: Svarah
- Telugu: IndicTTS Telugu
- Acoustic model: FastSpeech 2
- Vocoder: HiFi-GAN

English source: 6,656 records, approximately 9.61 hours. A custom split was prepared from the available published test partition; it is not an official train/validation split.

Telugu prepared data: 1,368 records (1,167 training and 201 validation).

Telugu audio: 16 kHz, 80 mel channels, FFT 1024, hop 256, window 1024. Pitch estimated using PyWorld DIO and StoneMask. Duration labels use CTC-based alignment and a grapheme-duration heuristic, not manually verified phoneme alignment.

## Inference results

| Language | WAV files | Duration plots | Pitch plots | Energy plots |
|---|---:|---:|---:|---:|
| English | 5 | 5 | 5 | 5 |
| Telugu | 5 | 5 | 5 | 5 |
| Total | 10 | 10 | 10 | 10 |

## Telugu validation

| Metric | Value |
|---|---:|
| Total loss | 41812.8009 |
| Mel loss | 5.3236 |
| Mel postnet loss | 4.5816 |
| Pitch loss | 40476.0882 |
| Energy loss | 1326.2533 |
| Duration loss | 0.5543 |

Validation evaluated 201 samples in approximately 8.3 minutes. High pitch and energy losses indicate areas requiring improvement.

## Training limitations

The assignment specifies approximately five hours of training and one hour of validation per language. Available logs do not establish completion of these full wall-clock durations. Telugu training logs contain recorded points through step 90. English training-loss logs were unavailable. Dataset audio duration is not model-training time.

## Repository folders

- src/: source code
- configs/English/: English configuration
- configs/Telugu/: Telugu configuration and vocabulary
- results/English/: English audio and plots
- results/Telugu/: Telugu audio and plots
- results/English_validation/: English validation
- results/Telugu_validation/: Telugu validation
- report/: technical report

## Installation

Run: pip install -r requirements.txt

Check configuration paths and checkpoint locations before training or inference.

Large datasets, checkpoints, vocoder weights and feature arrays are excluded. Store them separately or use Git LFS.

## References

1. Ren et al., FastSpeech 2: Fast and High-Quality End-to-End Text to Speech, ICLR 2021.
2. Kong et al., HiFi-GAN: Generative Adversarial Networks for Efficient and High Fidelity Speech Synthesis, NeurIPS 2020.

Add the exact dataset and reference implementation URLs used in the project before final submission.
