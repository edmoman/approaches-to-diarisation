NOTE: Apparently, [according to its own creators](https://github.com/audeering/w2v2-how-to/issues/31#issuecomment-1662719286), the model was not the wisest of choices. 

To address such shortcoming, I have forked CMU MOSEI:

https://github.com/mirix/messaih

The fork is tailored towards Speech Emotion Recognition (SER).

The idea now would be training a model on messAIh and see how it behaves on a real-life scenario.


___

I have added a new script that computes sentence-wise  [VAD/PAD](https://en.wikipedia.org/wiki/PAD_emotional_state_model) values using the [audEERING model](https://huggingface.co/audeering/wav2vec2-large-robust-12-ft-emotion-msp-dim). 

It takes as inputs the WAV and SRT files produced by the diarisation script located in the upper level folder. 

This script (test_emotions.py) works with Python 3.11 and possibly previous versions and the requirements should be straightforward to install.

It then attempts to translate the VAD values into [Ekman basic emotions](https://www.paulekman.com/universal-emotions/) and produces a new set of SRT files annotated with the predominant emotion.

The conversion from VAD into Ekman and the selection of the predominant emotion have not been properly calibrated yet but, in my humble opinion, the procedure already yields useful enough results.

Namely, a conversation segment rich in negatively-flagged sentences typically deserves further inspection.

Each emotion paradigm has a different scope of applicability and I therefore deemed useful being able to translate from one into another.

Moreover, language models trained on VAD values seem to offer superior accuracies as compared to models trained on categorical frameworks. 

This work is loosely inspired by:

[https://doi.org/10.3390/electronics10212643](https://doi.org/10.3390/electronics10212643)
