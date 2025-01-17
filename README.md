
<p align="center">
        <a>
	    <img src='https://img.shields.io/badge/python-3.7%7C3.8%7C3.9%2B-blueviolet' alt='Python' />
	</a>
	<a href='https://xgen-timeseries.readthedocs.io/en/latest/?badge=latest'>
    	    <img src='https://readthedocs.org/projects/xgen-timeseries/badge/?version=latest' alt='Documentation Status' />
	</a>
	<a href='https://creativecommons.org/licenses/by/4.0/'>
	    <img alt="CC 4.0 - License" src="https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg">
	</a><br>
</p>

</p>
<p align="center">
 <a>
  <img src="docs/source/_static/logo.png"  width="300" height="100">
 </a><br>	
  <a href="https://xgentimeseries.github.io/xgen-timeseries/index.html"> ➡ Documentation </a>
</p>

# XGen: A Comprehensive Archive and an eXplainable Time Series Generation Framework for Energy [(arxiv paper)](https://arxiv.org/abs/2407.01003)
![An overview of XGen framework interacted with XGen Archive](docs/source/_static/overview.png)

**Note ⚠️**
- Currently, we updated some classes of our  framework, please use our last release (v0.2.1-alpha)

Why do you need XGen Time Series? 
- Convenient accessibility to energy datasets,
- Utilizing data augmentation to improve performance during training,
- Enhancing interpretability by explaining the nature of the augmentation generated

```
!pip install -u xgents
from xgents import XGenExplainer
explain = XGenExplainer(real_x=X, gen_model=[GTGAN,TimeGAN, RCGAN],
                        model="DeepAR", method="GRAD", metric="PGU") 
```
![leaderboard](docs/source/_static/leaderboard.png)

### Evaluation Meet Explainability

Visual methods for explaining attribution features are limited for large datasets. XGen incorporates explanation fidelity in XGenExplain with metrics like PGI and PGU [1], RIS, and ROS [2] (denoted as $\mathcal{M}^\text{PGU}$, $\mathcal{M}^\text{PGI}$, $\mathcal{M}^\text{RIS}$, and $\mathcal{M}^\text{ROS}$ respectively). It quantitatively assesses local explanation performance and model disparity between real **($\mathcal{X}_{R}$)** and generated **($\mathcal{X}_{G}$)** data through **($\delta \mathcal{M}$)**. Experiments show a significant link between lower $\delta \mathcal{M}^{PGU}$ (preferably lower), improved MAE, and RMSE in follow-up tasks. $\delta$ RMSE and $\delta$ MAE denote the absolute gaps in DeepAR prediction performance. This observation is further supported by Shaplet plots, detailed in Appendix G.

| Method        | MAE        | RMSE        | $\delta$ MAE      | $\delta$ RMSE      | $\delta \mathcal{M}^\text{PGU}$ GRAD   | $\delta \mathcal{M}^\text{PGU}$ DeepLift | $\delta \mathcal{M}^\text{PGU}$ LIME   |
|---------------|------------|------------|------------|------------|------------|--------------|------------|
| TimeVAE       | .587±.002  | .881±.079  | .515±.006  | .678±.079  | .552±.051  | .158±.008    | .522±.040  |
| GTGAN         | **.200±.010** | **.227±.006** | **.098±.010** | **.024±.006** | **.170±.011** | .065±.013    | **.145±.032** |
| TimeGAN       | .398±.020  | .588±.001  | .296±.020  | .385±.001  | .210±.003  | .060±.008    | .292±.041  |
| RCGAN         | .221±.070  | .361±.001  | .119±.070  | .158±.001  | .246±.013  | .149±.013    | .192±.003  |
| C-RNN-GAN     | .520±.017  | .780±.003  | .418±.017  | .577±.003  | .186±.002  | .059±.028    | .193±.007  |
| PSA-GAN       | .519±.007  | .778±.010  | .417±.007  | .575±.010  | .171±.003  | **.058±.001** | .160±.004  |
| WaveGAN       | .211±.012  | .316±.010  | .010±.012  | .113±.010  | .174±.304  | .137±.003    | .296±.002  |
| T-Forcing     | .522±.071  | .783±.004  | .420±.071  | .580±.004  | .174±.004  | .068±.001    | .375±.001  |
| Real          | .101±.002  | .203±.006  | -          | -          | -          | -            | -          |
| Real-GTGAN    | **.102±.006** | **.187±.010** | .000±.004  | .016±.010  | .001±.001  | .003±.008    | .006±.001  |

The correlation between high-quality generated data and reduced disparities in explanations holds consistent for the metrics $\mathcal{M}^\text{PGI}$, $\mathcal{M}^\text{RIS}$, and $\mathcal{M}^\text{ROS}$. This insight offers a means of assessing the generated data quality. Presently, XGen has matured to provide all these metrics, presenting them in a leaderboard format. This enables us to clearly observe that integrating this with augmentation or imputation will likely enhance model learning. We have also introduced additional downstream task models, catering to forecasting and disaggregation.


**XGen-Archive.** The framework provides an extensive archive of energy data specifically designed for forecasting and disaggregation tasks. With its user-friendly interface, utilizing the archive is straightforward. Here's an example of how to make use of this valuable resource (see [use_example](src/XGenTS/archive/use_example.ipynb)):

```
!pip install -u xgents
from xgents.datasets import load_dataset
dataset = load_dataset("archive/uk_dale", streaming=True)
# Alternatively, you can manually download the hdf5 file 
# from XGen archive and use ```load_dataset``` with "streaming=False".
```
By following these simple steps, you can leverage the power of the framework's energy data archive. Whether you need to forecast energy consumption or perform disaggregation analysis, this comprehensive dataset provides the necessary foundation for your tasks.

**XGen Time Series.** The framework also includes an extensive implementation of diverse generative models, all integrated within a unified platform. This integration allows for benchmark experiments and seamless model comparisons by training the models using a consistent autoencoding neural network architecture. Furthermore, the framework offers a unique "make your own generative time series" feature, enabling you to train any of these models using your own dataset and customize the neural networks according to your specific needs. This flexibility empowers you to tailor the models to your specific requirements and explore various possibilities in generative time series analysis.


Additionally, the library integrates popular experiment monitoring tools such as [wandb](https://wandb.ai/), [mlflow](https://mlflow.org/), and [comet-ml](https://www.comet.com/signup?utm_source=XGen&utm_medium=partner&utm_campaign=AMS_US_EN_SNUP_XGen_Comet_Integration) 🧪. It also allows for easy model sharing and loading from the [HuggingFace Hub](https://huggingface.co/XGenTimeSeries) 🤗 with just a few lines of code.


**Note**
> Your ```XGen Time Series``` now supports distributed training using PyTorch's DDP (Distributed Data Parallel). With this new feature, you can now train your preferred Generative Time Series models faster and on custom datasets, all with just a few lines of code. This allows for improved scalability and accelerated training across multiple GPUs or even distributed systems.
> To showcase the enhanced performance, we have conducted a comprehensive benchmarking analysis. You can find the detailed results in the benchmark section of our documentation. This benchmark highlights the significant speed-up achieved by leveraging the distributed training capabilities of XGen Time Series.
> Take advantage of XGen 0.2's distributed training support and experience accelerated training for your Generative Time Series models. Visit our documentation and explore the benchmark section to learn more about the performance improvements and how to make the most out of this latest release.


## Quick access:
- [Installation](#installation)
- [Implemented models](#available-models) / [Implemented samplers](#available-samplers)
- [ESS Dataset: A Novel Curated Dataset for Fine-grained Analysis XGen-ESS](https://xgentimeseries.github.io/xgen-timeseries/ess_datasets/index.html)
- [Reproducibility statement](#reproducibility) / [Results flavor](#results)
- [Model training](#launching-a-model-training) / [Data generation](#launching-data-generation) / [Custom network architectures](#define-you-own-autoencoder-architecture) / [Distributed training](#distributed-training-with-XGen)
- [Model sharing with 🤗 Hub](#sharing-your-models-with-the-huggingface-hub-) / [Experiment tracking with `wandb`](#monitoring-your-experiments-with-wandb-) / [Experiment tracking with `mlflow`](#monitoring-your-experiments-with-mlflow-) / [Experiment tracking with `comet_ml`](#monitoring-your-experiments-with-comet_ml-)
- [Tutorials](#getting-your-hands-on-the-code) / [Documentation](https://XGen.readthedocs.io/en/latest/)
- [Contributing 🚀](#contributing-) / [Issues 🛠️](#dealing-with-issues-%EF%B8%8F)
- [Citing this repository](#citation)

# Installation

To install the latest stable release of this library run the following using ``pip``

```bash
$ pip install -u xgents
``` 

To install the latest github version of this library run the following using ``pip``

```bash
$ pip install git+https://github.com/XgenTimeSeries/xgen-timeseries
``` 

or alternatively you can clone the github repo to access to tests, tutorials and scripts.
```bash
$ git clone https://github.com/XgenTimeSeries/xgen-timeseries
```
and install the library
```bash
$ cd xgen-timeseries
$ pip install -e .
``` 

## Available Models

Below is the list of the models currently implemented in the library.


|               Models               |                                                                                    Training example                                                                                    |                     Paper                    |                           Official Implementation                          |
|:----------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------:|:--------------------------------------------------------------------------:|
| PSA-GAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/XgenTimeSeries/xgen-timeseries/blob/master/tutorials/PSA_GAN_in_XGenTimeSeries.ipynb) |                    [link](https://arxiv.org/abs/2108.00981)                             |   -
| WaveGAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                    [link](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9053795)                             |                        -                                                 |
| TimeGAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                    [link](https://arxiv.org/pdf/1706.02633.pdf)                             |                               [tensorflow](https://github.com/flaviagiammarino/time-gan-tensorflow)                                              |
| GT-GAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                      [link](https://arxiv.org/pdf/1706.02633.pdf)                           |                                    [tensorflow](https://github.com/ratschlab/RGAN/blob/master/model.py)                                    |
| RCGAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                      [link](https://arxiv.org/pdf/1706.02633.pdf)                           |                               -                                          |
| Professor Forcing                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                       [link](https://arxiv.org/pdf/1706.02633.pdf)                          |                                   -                                      |
| RGAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                    [link](https://arxiv.org/pdf/1706.02633.pdf)                             |                            -                                          |
| PROBGAN                   | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |                    [link](http://www.wanghao.in/paper/ICLR19_ProbGAN.pdf)                             |                              -                                        |



**See [reconstruction](#Reconstruction) and [generation](#Generation) results for all models**

## Reproducibility

We validate the implementations by reproducing some results presented in the original publications when the official code has been released or when enough details about the experimental section of the papers were available. 

## Training Step

To launch a model training, you only need to call a `TrainingPipeline` instance. 

```python
from XGen.pipelines import TrainingPipeline
from XGen.models import CCGAN, CCGANConfig
from XGen.trainers import BaseTrainerConfig

# Set up the training configuration
my_training_config = BaseTrainerConfig(output_dir='my_model',
                    num_epochs=50,
                    learning_rate=1e-3,
                    per_device_train_batch_size=200,
                    per_device_eval_batch_size=200,
                    train_dataloader_num_workers=2,
                    eval_dataloader_num_workers=2,
                    steps_saving=20,
                    optimizer_cls="AdamW",
                    optimizer_params={"weight_decay": 0.05, "betas": (0.91, 0.995)},
                    scheduler_cls="ReduceLROnPlateau",
                    scheduler_params={"patience": 5, "factor": 0.5})

# Set up the model configuration 
my_xgen_config = XGenConfig(input_dim=(28, 3600),
                            (features_time, time_sequence_szie)
                            latent_dim=10)
# Build the model
my_xgen_model = XGenModel(model_config=my_xgen_config)

# Build the Pipeline
pipeline = TrainingPipeline(training_config=my_training_config,
                            model=my_model)

# Launch the Pipeline
pipeline(
    train_data=your_train_data, # must be torch.Tensor, np.array or torch datasets
    eval_data=your_eval_data # must be torch.Tensor, np.array or torch datasets
    )
```

At the end of training, the best model weights, model configuration and training configuration are stored in a `final_model` folder available in  `my_model/MODEL_NAME_training_YYYY-MM-DD_hh-mm-ss` (with `my_model` being the `output_dir` argument of the `BaseTrainerConfig`). If you further set the `steps_saving` argument to a certain value, folders named `checkpoint_epoch_k` containing the best model weights, optimizer, scheduler, configuration and training configuration at epoch *k* will also appear in `my_model/MODEL_NAME_training_YYYY-MM-DD_hh-mm-ss`.

##  Training on XGen Time Series datasets
We also provide a training script example [here](https://github.com/XgenTimeSeries/xgen-timeseries/tree/main/examples/scripts/training.py) that can be used to train the models on benchmarks datasets (Ukdale, Refit, Redd    ).

```bash
python training.py --dataset ukdale --model_name TimeGAN --model_config 'configs/ae_config.json' --training_config 'configs/base_training_config.json'
```

See [README.md](https://github.com/XgenTimeSeries/xgen-timeseries/tree/main/examples/scripts/README.md) for further details on this script

## Generate new Time Series

### Using the `TimeGenerationPipeline`

The easiest way to launch a data generation from a trained model consists in using the built-in `TimeGenerationPipeline` provided in XGen. Say you want to generate 100 samples using a `MAFSampler` all you have to do is 1) relaod the trained model, 2) define the sampler's configuration and 3) create and launch the `TimeGenerationPipeline`.


### Samplers Modules

You can launch the data generation process from a trained model directly with the sampler. For instance, to generate new data with your sampler, run the following.

```python
from XGen.models import AutoModel
from XGen.samplers import NormalSampler
# Retrieve the trained model
my_trained = AutoModel.load_from_folder(
    'path/to/your/trained/model')

# Define your sampler
my_samper = NormalSampler(model=my_trained_xgen)
# Generate samples
gen_data = my_samper.sample(num_samples=50,
                        batch_size=10,
                        output_dir=None,
                        return_gen=True)
```
If you set `output_dir` to a specific path, the generated time series will be saved as `.csv`.


## Your own Model architecture for forecasting or Energy Dissagregation 
 
XGen provides you the possibility to define your own neural networks within the generative models. For instance, say you want to train a Wassertstein AE with a specific encoder and decoder, you can do the following:

```python
from XGen.models.nn import BaseEncoder, BaseDecoder
from XGen.models.base.base_utils import ModelOutput
class My_Encoder(BaseEncoder):
    def __init__(self, args=None): # Args is a ModelConfig instance
        BaseEncoder.__init__(self)
        self.layers = my_nn_layers()
        
    def forward(self, x:torch.Tensor) -> ModelOutput:
        out = self.layers(x)
        output = ModelOutput(
            embedding=out # Set the output from the encoder in a ModelOutput instance 
        )
        return output

class My_Decoder(BaseDecoder):
    def __init__(self, args=None):
        BaseDecoder.__init__(self)
        self.layers = my_nn_layers()
        
    def forward(self, x:torch.Tensor) -> ModelOutput:
        out = self.layers(x)
        output = ModelOutput(
            reconstruction=out # Set the output from the decoder in a ModelOutput instance
        )
        return output

        my_encoder = My_Encoder()
        my_decoder = My_Decoder()
```

And now build the model

```python
from XGen.models import WAE_MMD, WAE_MMD_Config
# Set up the model configuration 
my_wae_config = model_config = WAE_MMD_Config(
    input_dim=(1, 28, 28),
    latent_dim=10)
   
# Build the model
my_wae_model = WAE_MMD(
    model_config=my_wae_config,
    encoder=my_encoder, # pass your encoder as argument when building the model
    decoder=my_decoder # pass your decoder as argument when building the model
    )
```

## Distributed Training with `XGen`
As of `v0.1.0`, XGen now supports distributed training using PyTorch's [DDP](https://pytorch.org/docs/stable/notes/ddp.html). 

To do so, you can build a python script that will then be launched by a launcher (such as `srun` on a cluster). The only thing that is needed in the script is to specify some elements relative to the distributed environment (such as the number of nodes/gpus) directly in the training configuration as follows

```python
training_config = BaseTrainerConfig(
    num_epochs=10,
    learning_rate=1e-3,
    per_device_train_batch_size=64,
    per_device_eval_batch_size=64,
    train_dataloader_num_workers=8,
    eval_dataloader_num_workers=8,
    dist_backend="nccl", # distributed backend
    world_size=8 # number of gpus to use (n_nodes x n_gpus_per_node),
    rank=5 # process/gpu id,
    local_rank=1 # node id,
    master_addr="localhost" # master address,
    master_port="12345" # master port,
    )
```

See this [example script](https://github.com/XgenTimeSeries/xgen-timeseries/blob/main/examples/scripts/distributed_training_imagenet.py) that defines a multi-gpu training on time series dataset. Please note that the way the distributed environment variables (`world_size`, `rank`    ) are recovered may be specific to the cluster and launcher you use. 

### Benchmark

Below are indicated the training times for a CCGAN with `XGen`:

|  | Train Data | 1 GPU | 4 GPUs | 2x4 GPUs |
|:---:|:---:|:---:|:---:|---|
| UK DALE | Energy data from UK households | 7h 30min | 3h 12min | 1h 58min |
| REDD | Energy data from US households | 9h 14min | 4h 26min | 2h 53min |
| REFIT | Energy data from UK households | 6h 51min | 3h 02min | 1h 47min |


For each dataset, we provide the benchmarking scripts [here](https://github.com/XgenTimeSeries/xgen-timeseries/tree/main/examples/scripts)


## Sharing your models with the HuggingFace Hub 🤗
XGen also allows you to share your models on the [HuggingFace Hub](https://huggingface.co/models). To do so you need:
- a valid HuggingFace account
- the package `huggingface_hub` installed in your virtual env. If not you can install it with 
```
$ python -m pip install huggingface_hub
```
- to be logged in to your HuggingFace account using
```
$ huggingface-cli login
```

### Uploading a model to the Hub
Any XGen model can be easily uploaded using the method `push_to_hf_hub`
```python
model.push_to_hf_hub(hf_hub_path="your_hf_username/your_hf_hub_repo")
```
**Note:** If `your_hf_hub_repo` already exists and is not empty, files will be overridden. In case, 
the repo `your_hf_hub_repo` does not exist, a folder having the same name will be created.

### Downloading models from the Hub
Equivalently, you can download or reload any XGen's model directly from the Hub using the method `load_from_hf_hub`
```python
from XGen.models import AutoModel
downloaded = AutoModel.load_from_hf_hub(hf_hub_path="path_to_hf_repo")
```

## Monitoring your experiments with `wandb` 🧪
XGen also integrates the experiment tracking tool [wandb](https://wandb.ai/) allowing users to store their configs, monitor their trainings and compare runs through a graphic interface. To be able use this feature you will need:
- a valid wandb account
- the package `wandb` installed in your virtual env. If not you can install it with 
```
$ pip install wandb
```
- to be logged in to your wandb account using
```
$ wandb login
```

### Use `WandbCallback` for logs
Launching an experiment with time-real logs with `wandb` in XGen Time Series is pretty simple. The only thing a user needs to do is create a `WandbCallback` instance: 

```python
# Create your callback
from XGen.trainers.training_callbacks import WandbCallback
callbacks = [] # the TrainingPipeline expects a list of callbacks
wandb_callback = WandbCallback() # Build the callback
wandb_callback.setup(
    training_config=your_training_config, # training config
    model_config=your_model_config, # model config
    project_name="wandb_project", # your and project
    entity_name="wandb_entity", # your wandb entity
    )
callbacks.append(wandb_callback) # Add it to the callbacks list
```

```python
pipeline = TrainingPipeline(
    training_config=config,
    model=model)

pipeline(train_data=train_dataset,
    eval_data=eval_dataset,
    callbacks=callbacks)

# You can log to https://wandb.ai/your_wandb_entity/your_wandb_project to monitor your training
```
See the detailed tutorial 

## Monitoring your experiments with `mlflow` 🧪
XGen also integrates the experiment tracking tool [mlflow](https://mlflow.org/) allowing users to store their configs, monitor their trainings and compare runs through a graphic interface. To be able use this feature you will need:
- the package `mlfow` installed in your virtual env. If not you can install it with 
```
$ pip install mlflow
```

### Creating a `MLFlowCallback`
Launching an experiment monitoring with `mlfow` in XGen is pretty simple. The only thing a user needs to do is create a `MLFlowCallback` instance   

```python
# Create you callback
from XGen.trainers.training_callbacks import MLFlowCallback
callbacks = [] # the TrainingPipeline expects a list of callbacks
mlflow_cb = MLFlowCallback() # Build the callback 
# SetUp the callback 
mlflow_cb.setup(
    training_config=your_training_config, # training config
    model_config=your_model_config, # model config
    run_name="mlflow_cb_example", # specify your mlflow run
    )
callbacks.append(mlflow_cb) # Add it to the callbacks list
```
   and then pass it to the `TrainingPipeline`.
```python
pipeline = TrainingPipeline(
    training_config=config,
     model=model)
    
pipeline(train_data=train_dataset,
    eval_data=eval_dataset,
   	callbacks=callbacks # pass the callbacks to the TrainingPipeline and you are done!
    )
```
you can visualize your metric by running the following in the directory where the `./mlruns`
```bash
$ mlflow ui 
```
See the detailed tutorial 

## Monitoring your experiments with `comet_ml` 🧪
XGen also integrates the experiment tracking tool [comet_ml](https://www.comet.com/signup?utm_source=XGen&utm_medium=partner&utm_campaign=AMS_US_EN_SNUP_XGen_Comet_Integration) allowing users to store their configs, monitor their trainings and compare runs through a graphic interface. To be able use this feature you will need:
- the package `comet_ml` installed in your virtual env. If not you can install it with 
```
$ pip install comet_ml
```

### Creating a `CometCallback`
Launching an experiment monitoring with `comet_ml` in XGen is pretty simple. The only thing a user needs to do is create a `CometCallback` instance   

```python
# Create you callback
from XGen.trainers.training_callbacks import CometCallback
callbacks = [] # the TrainingPipeline expects a list of callbacks
comet_cb = CometCallback() # Build the callback 
# SetUp the callback 
comet_cb.setup(training_config=training_config, # training config
            model_config=model_config, # model config
            api_key="your_comet_api_key", # specify your comet api-key
            project_name="your_comet_project", # specify your wandb project
            )
callbacks.append(comet_cb) # Add it to the callbacks list

```
   and then pass it to the `TrainingPipeline`.
   
```python
pipeline = TrainingPipeline(
    training_config=config,
    model=model
    )

pipeline(train_data=train_dataset,
    eval_data=eval_dataset,
    callbacks=callbacks # pass the callbacks to the TrainingPipeline and you are done!
    )
# You can log to https://comet.com/your_comet_username/your_comet_project to monitor your training
```
See the detailed tutorial 

## Generation data (Uk-DALE Dataset) 

![An overview of XGen framework interacted with XGen Archive](docs/source/_static/Uk-DALE.png)

## Dealing with issues 🛠️

If you are experiencing any issues while running the code or request new features/models to be implemented please [open an issue on github](https://github.com/XgenTimeSeries/xgen-timeseries/issues).

## Contributing 🚀

You want to contribute to this library by adding a model, a sampler or simply fix a bug ? That's awesome! Thank you! Please see [CONTRIBUTING.md](https://github.com/XgenTimeSeries/xgen-timeseries/tree/main/CONTRIBUTING.md) to follow the main contributing guidelines.


# References

[1] Fairness via Explanation Quality https://arxiv.org/abs/2205.07277

[2] Randomized Input Sampling for Explanation of Black-box Models https://arxiv.org/abs/1806.07421


# Citation

If you find this work useful or use it in your research, please consider citing using:

```
@software{Oublal_XGen_Time_Series_2023,
author = {Oublal, Khalid and Ladjal, Said and Benhaiem, David and le-borgne, Emmanuel and Roueff, François},
month = jun,
title = {{XGen Time Series}},
url = {https://xgentimeseries.github.io/},
version = {0.1.2},
year = {2023}
}
```
