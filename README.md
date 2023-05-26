# protein_classification_altegrad_challenge

This project is part of the MVA class ALTEGRAD (Advanced Learning for Text and Graph Data).
The project focuses on applying machine learning and artificial intelligence techniques to a classification problem in the field of bioinformatics. Protein engineering using machine learning has gained significant attention recently. Proteins are essential biomolecules composed of long chains of amino acids, serving various functions in living organisms. They act as enzymes, provide structural support, and play a crucial role in the immune system. The sequence of amino acids forms a polypeptide, which then folds to create the protein's 3D structure, determining its chemical functionality. However, the folding process is not fully understood. The challenge involves analyzing **6,111 protein sequences and their graph representations** to classify them into **18 different classes** based on the protein's function within a cellular component. 


### Dataset
The dataset is available [here](https://drive.google.com/uc?export=download&confirm=pbef&id=14Vx7cbpw-jvxEHodDjGCfF5ChzuVW9RC) and is detailed in the **Challenge dataset** section in _Final_notebook_ALTEGRAD.ipynb_. Basically, a protein is described as a sequence of text symbols and as an undirected graph of linked nodes. The dataset also contains edges and nodes attributes describing the nature of the of the link between the amino-acids as well as their type and natural features (derived from the EXPASY protein scale https://web.expasy.org/protscale).

<div style="text-align: center;">
  <img src="https://github.com/rsebai/protein_classification_altegrad_challenge/assets/79949319/8d5dab7d-9d99-4a5a-9b47-625fa75c9fa5"
     width="50%" height="50%" >
</div>

### Approaches
#### On sequential data
To accomplish the classification task, the best performing models were based on transfer learning with **pre-trained language models applied to the sequential data**. The models used were 'Rostlab/prot_bert_bfd', "facebook/esm2_t12_35M_UR50D", and "facebook/esm2_t30_150M_UR50D" that are hosted in the Hugging Face hub. 

The first model, 'Rostlab/prot_bert_bfd', is a BERT-based model that has been fine-tuned on a large dataset of protein sequences and their corresponding functional domains. BERT, or "Bidirectional Encoder Representations from Transformers," is a powerful language model that can be fine-tuned for a variety of natural language processing tasks.

The second and third models, "facebook/esm2_t12_35M_UR50D" and "facebook/esm2_t30_150M_UR50D", are [ESM models](https://huggingface.co/docs/transformers/model_doc/esm) that have been trained with different number of parameters and on different dataset. These models were fine-tuned on our protein sequences classification task. 

#### On graph data
We also used Graph Neural Networks (GNN) to perform the classification task using the structural aspect of the proteins rather than the sequential data. GNNs were used for protein classification by representing the proteins structure as a graph, where the nodes represent amino acids and the edges represent the chemical bond between them. GNNs can learn to propagate information through the graph to classify the proteins based on their 3D structure. They are well-suited to handle graph-structured data and can capture long-range dependencies via message passing layers. Only the nodes' attributes were used in this project. An improvment of the result could be including edges' attributes as well. We used in this project two types of GNNs: Graph Convolutinal Networks (GCN) and Graph Attention Networks (GAT).

