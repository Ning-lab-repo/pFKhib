# pFKhib
prediction of Functional lysine 2-hydroxyisobutyrylation (pFKhib) sites 

We developed a novel protein language model (PLM)-based framework called "prediction of Functional Khib sites" (pFKhib). This framework captures intricate patterns in protein sequences, enabling more accurate and efficient predictions of functional Khib sites. We defined the 2-hydroxyisobutyrylation site peptide (HSP) as a 2-hydroxyisobutyrylation residue with m residues upstream and n residues downstream, utilizing HSP (10, 10) for training in this study. First, we trained a pre-trained model named pFKhib-pre. We encoded the HSP (10, 10) peptide into 11 types of 1D feature vectors, each associated with a specific DNN model to predict a score, resulting in 11 scores for each Khib site. We then used an integrated DNN to summarize these scores into a final score. Finally, we fine-tuned the pFKhib-pre model through few-shot transfer learning to develop the pFKhib model, which predicts the functionality of Khib sites.
# Requirements
The main requirements are listed below:

* Python 3.8
* Numpy
* Scikit-Learn
* matplotlib
* Keras
* Pandas
# The description of the pFKhib source
* after_cd_hit.py
  
  The code is used for turning FASTA format sequences after being deredundant by CD-HIT into HSP (10,10) peptides.
* encoding_10features.py
  The code is used for encoding an HSP (10,10) peptide into 10 kinds of 1D feature vectors (PseAAC, CKSAAP, OBC, AAindex, ACF, GPS, PSSM, ASA, SS, and BTA) for DNN training.
* transformer.py
  The code is used for training the transformer model to generate the 11th feature vector, also named transformer.
* transformer_feature.py
  The code is utilizing the transformer trained above for encoding an HSP (10, 10) peptide into a 128D feature vector which is also named transformer.
* DNN.py
  The code is 11 fully connected neural network frameworks of 11 types of featurese for model pre-training. Pre-training is applied to predict whether a lysine site is a 2-hydroxyisobutyrylation site.
* integrated_DNN.py
  The code is a fully connected neural network framework that can summarize the 11 scores and make a final prediction for model training and evaluation. Integrated_DNN will not participate in transfer learning.
* transfer_learning.py
  The code is for 11 DNNs' transfer learning to apply these DNNs to predict whether a Khib site is functional.
* predict.py
  The code is to use pFKhib containing 11 DNNs and the integrated DNN we mentioned above to use 11 features generated from a group of HSP (10, 10) peptides (Khib sites) to score them and predict whether each of them is functional.
* evaluate.py
  The code is used for getting the Sensitivity, Specificity, and ROC auc scores of 11 DNNs and integrated DNN.
* ROC.py
  The code is used to draw 11 ROC curves of the pFKhib model consisting of 11 parallel DNNs and integrated DNN.
