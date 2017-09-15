# Requirements
  * TensorFlow v1.3+
  * NLTK v3.2.4+

# Installation

```
$ sh setup.sh
```

# Data processing (included in setup.sh)

```
$ python3 data_preprocessing.py --file datasets/SQuAD/train-v1.1.json --mode train
$ python3 data_preprocessing.py --file datasets/SQuAD/dev-v1.1.json --mode dev
```

# rNet Model
  * train

```
$ python3 run.py --config=configs/SQuAD_encoder_layer_2_encoder_size_32_layer_1_cudnn_rnn_gpu_2.json --logdir=output
```

  * infer

```
$ python3 run.py --config=configs/SQuAD_encoder_layer_2_encoder_size_32_layer_1_cudnn_rnn_infer.json --logdir=output --inference_out=output/inference_out.txt
$ python3 generate_candidates.py --file_id datasets/SQuAD/dev/id.txt --source datasets/SQuAD/dev/src/sources.txt --target output/inference_out.txt
```

  * eval

```
$ python3 eval_SQuAD.py datasets/SQuAD/dev-v1.1.json output/candidates.json
```