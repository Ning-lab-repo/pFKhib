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
