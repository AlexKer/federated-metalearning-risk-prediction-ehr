# federated-metalearning-risk-prediction-ehr

### Title: Federated Meta-Learning for Risk Prediction with Limited Patient Electronic Health Records Using PySyft and SyferText (OpenMined)
### Original project funded by [Pomona College](https://www.pomona.edu) 
### Student: Alex Ker alex.ker@pomona.edu
### Mentor: Alan Aboudib, Márcio Porto

## Background and Problem

In recent years, as the Electronics Health Records (EHR) are becoming more readily available, healthcare data can be leveraged to gain insights to improve the quality of care delivery. Particularly, accurate predictive modelling of clinical risks, including the metrics of mortality, hospital readmission, chronic disease onset, condition exacerbation, for diseases across domains are crucial because it enables clinicians to identify risks early, and thus take appropriate steps.
However, training deep learning models to tackle this issue using the EHR is difficult, due to sparsity, noisiness, and temporality of the dataset. Furthermore, healthcare data are often limited, expensive, and new examples are hard to obtain. Take Alzheimer for example or any specific disease—there are only so many new cases each year across the globe, recorded in different manners and not all accessible. Thus, we only have a small number of examples of each condition in our EHR corpus to train such a predictive model for clinical risks, which results in poor performance.

## Solution and Task

Meta-learning is the process of learning how to learn. When humans learn new tasks, we use previous knowledge to adapt to unseen situations quickly. Meta-learning can be seen as a generalization to Transfer Learning. Transfer learning is when a pretrained model is fined-tuned for a target task, and this has demonstrated to be effective for similar medical problems. But Transfer Learning has an important downside: since the final layer of the network needs to be changed significantly for the new task, and the dataset is small, the model will severely overfit in the few-shot setting. This is exactly the problem we face in the EHR dataset or other healthcare contexts. Moreover, because Transfer Learning is typically pretrained on a large dataset of general examples, e.g. BERT, ImageNet, the network may not be exactly relevant to the target EHR task, and the benefits diminishes when the new task divulges from the original task.

Fortunately, Meta-Learning resolves this issue. Meta-Learning will learn a general initial representation for effective fine-tuning later i.e. when we adapt to a new task, good parameters can be achieved with few gradient updates. Specifically, when applied to the usecase of creating a good risk predictor, the Meta-Learner is trained on a set of related risk prediction tasks, and learns how a good predictor can be learned. Then the Meta-Learner is directly used to predict the target risk, with the limited samples of the target risk to further fine-tune on top of the great initialization.

The goal of this project use PySyft and SyferText to train models (CNN, LSTM), as discussed in [MetaPred: Meta-Learning for Clinical Risk Prediction with Limited Patient Electronic Health Records], using two learning schemes, MetaPred (as discussed in the above paper) and MAML [Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks], perhaps in addition to REPTILE+other optimization based methods. More generally, this project would demonstrate Meta-Learning applied to a worthwhile problem using private datasets and modeling techniques. While doing so, new features will be added to the OpenMined codebase to support Meta-Learning operations.

## Reference Material

MetaPred: Meta-Learning for Clinical Risk Prediction with Limited Patient Electronic Health Records
Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks
