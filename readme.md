BERT Based QA System on kaggleQA Data set
=======================================

This repository demonstrates BERT for downstream Question Answering Task on KaggleQA Dataset
 https://www.kaggle.com/rtatman/questionanswer-dataset
 
It gives step by step instructions to use Bert with default pretrained weights and hypere parameters, due to complexity of task and space, its tested on one example only

How to use these scripts?
=========================
The main script for this project is `run_squad.py`. To use this file to run prediction, make sure you have 
1) one input json file with the following format:
```python
{
  "data": [
    {
      "paragraphs": [
        {
          "context": "This is the text of document",
          "id": "Unique identifier to recognize document, etc: title of document",
          "qas": [
            {
              "question": "Question 1",
              "answers": "Answer 1 (This is optional, only useful when u want to train BERT QA model on this dataset)",
              "id": "Unique identifier to recognize this pair of question and answer."
            }
          ]
        }
      ]
    }
  ]
}
```
* There is a ipynb notebook, `pre_process_squad.ipynb` which might be useful to help you convert you dataset to this specific format if your dataset is similar to the structure of this dataset:https://www.kaggle.com/rtatman/questionanswer-dataset

2) pretrained-weights are downloaded from BERT official github: https://github.com/google-research/bert#pre-trained-models, downloaded files should be put into folder pretrained-weights

After that, run the following command from Terminal:

`python run_squad.py --bert_config_file='pretrained-weights/uncased_L-12_H-768_A-12/bert_config.json' --output_dir='output/' --predict_file='input/test.json' --init_checkpoint='pretrained-weights/uncased_L-12_H-768_A-12/bert_model.ckpt' --vocab_file='pretrained-weights/uncased_L-12_H-768_A-12/vocab.txt' --do_predict`

to generate a output json file `predictions.json` inside output directory. 
(See `usage_example/` if the above instruction is still not clear for you)this folder contains one example for training and testing




