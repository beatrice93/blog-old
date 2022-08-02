Here are a few papers of interest I found in my arXiv feed. I'll add more if there are more this week.

## [Scrutinizing Shipment Records To Thwart Illegal Timber Trade](https://arxiv.org/pdf/2208.00493.pdf)

The authors of this paper used machine learning to detect potential fraudulent timber shipments, based on shipment information: code (what kind of wood was shipped), weight, volume, ports of loading and unloading, origin and destination...

### Problem 
This is an anomaly detection task. One of the main issues with using existing approaches is dimensionality: 
 - some of the categorical features (code, origin, destination...) have many possible values
 - the authors did not want to discretize the continuous features (weight, volume...)

Another issue is that most clustering approaches make assumptions about the shape, size and/or number of clusters, which was not really possible here.

### Model
The model chosen has two parts: an autoencoder and a density estimation network. Autoencoders are useful for anomaly detection: if an autoencoder does not manage to decode an observation, then it is most likely anomalous. However, an autoencoder can generalize *too well*; in which case, it will be able to encode/decode any observation.
Hence the other part: the density estimation network. This is built to directly estimate the likelihood of the data instance being drawn from the underlying distribution. The density estimation network uses a variation of noise contrastive estimation, to learn the distribution of the data by comparing it to a noise distribution. The noise distribution is itself generated from the data, by taking samples and adding noise to them. This ensures the negative samples (drawn from the noise distribution) still "look like" positive samples, while being "a little bit different". The support, mean, variance etc are slightly altered.

### Comments
Obviously evaluation is hard, since the data is unlabeled. The authors claim their model performs better on several benchmark datasets. One interesting feature is that they say it is not as sensitive to hyperparameters as other SOTA models, which is a desirable feature since it is impossible to search hyperparameters without a labeled validation set.
