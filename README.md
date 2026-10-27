# MAAI901 Individual Project

## Comparing MobileNetV3 and MobileViT-XSS against increasing levels of image corruption on the EuroSAT dataset
## Repository Contents

- **`MAAI901_Individual_Project_Notebook.ipynb`** — Main Jupyter notebook containing the code, explanations, training procedure, evaluations, and visualisations.
- **`EuroSAT_Robustness_Efficiency/`** — Folder containing the experiment outputs generated during execution, including trained model checkpoints, evaluation results, CSV files, and visualisations.

The output folder contains the artefacts produced by the experiment. Depending on the execution environment and Google Drive configuration, the notebook may need to be run again to regenerate these outputs.

## Environment and Execution

### Platform Requirements

This notebook was developed and tested using **Google Colab with an NVIDIA L4 GPU**. It is designed to run in Google Colab rather than as a standalone notebook on a local computer.

### Google Drive

The notebook uses Google Drive to store and access experiment files, including trained model checkpoints, evaluation results, CSV files, and visualisations.

Before running the notebook:

1. Open `MAAI901_Individual_Project_Notebook.ipynb` in Google Colab.
2. Ensure you are signed in to a Google account with access to Google Drive.
3. Mount Google Drive when prompted by the notebook.
4. Ensure sufficient storage is available for the dataset, model checkpoints, and generated results.
5. Select an available GPU runtime under **Runtime → Change runtime type → T4 GPU, L4 GPU, or another compatible GPU**, if available. The original experiment was conducted using an NVIDIA L4 GPU.

**Important:** The notebook uses Google Drive paths under `/content/drive/MyDrive/EuroSAT_Robustness_Efficiency`. If you run it using your own Google account, the notebook may create this folder in your Drive. Existing checkpoints and outputs stored in another user's Drive will not automatically be accessible to you.

### Installing Dependencies

The notebook includes a dependency-installation cell near the beginning.

Run this cell before executing the remaining notebook cells:

```python
%pip install -q timm scikit-learn pandas numpy matplotlib seaborn Pillow tqdm
```

Google Colab already provides PyTorch and torchvision in its standard environment. The installation cell therefore installs the additional libraries required by the project without unnecessarily replacing those existing packages.

If any dependency installation or import fails, restart the runtime if necessary and rerun the notebook from the beginning.

### Execution Instructions

- Run all notebook cells in order, starting from the beginning.
- Execute the dependency-installation cell before running the experiment.
- If prompted, authorise access to Google Drive.
- The notebook downloads or accesses the EuroSAT dataset and trains/evaluates MobileNetV3-Small and MobileViT-XXS.
- Training checkpoints and experiment outputs are saved to the configured Google Drive project directory.
- Allow the training and evaluation cells to finish before reviewing the final results.

If the notebook is run from scratch, training and evaluation may take longer than simply loading existing results. The exact duration depends on the available accelerator and runtime conditions.

### Experiment Outputs

The notebook generates and saves experiment artefacts, including:

- Dataset class and split distributions.
- Dataset split indices and metadata.
- Training configuration and training summaries.
- Best model checkpoints for MobileNetV3-Small and MobileViT-XXS.
- Clean-test classification metrics and confusion matrices.
- Corruption robustness results for all tested corruption types and severity levels.
- Robustness summaries and accuracy/F1 visualisations.
- Model efficiency metrics, including parameter counts, checkpoint sizes, inference latency, and throughput.
- A final comparison table summarising both models.

These outputs are stored in the `EuroSAT_Robustness_Efficiency` project folder in Google Drive when the notebook is executed with the configured directory.

### Hardware and Reproducibility

The reported experiment was conducted using an **NVIDIA L4 GPU in Google Colab**. Training times and inference benchmarks may differ depending on the GPU model, runtime availability, software versions, and execution environment.

Google Colab does not guarantee access to a particular GPU. Results may therefore differ slightly when the notebook is executed on different hardware or under different runtime conditions.

For reproducibility, execute all cells in order and retain the same dataset split, random seeds, model configurations, corruption settings, and evaluation settings.

The experiment uses a fixed random seed for the dataset split. However, exact reproducibility is not guaranteed across all hardware and software configurations.

## Models Evaluated

- **MobileNetV3-Small:** A lightweight convolutional neural network.
- **MobileViT-XXS:** A compact hybrid convolutional and transformer-based architecture.

Both models use ImageNet-pretrained weights and are fine-tuned for the ten-class EuroSAT classification task.

## Corruption Experiments

The experiment evaluates three types of image corruption:

- **Gaussian noise:** Standard deviations of 10, 25, and 50 in the original RGB pixel-value space.
- **Salt-and-pepper noise:** Corruption amounts of 0.01, 0.03, and 0.06.
- **Rotation:** Angles of 5°, 15°, and 30°.

The models are evaluated on the clean test set and on each corrupted test condition.

## License and Dataset Attribution

The EuroSAT dataset was introduced by Helber et al. Please refer to the original publication when using or discussing the dataset:

Helber, P., Bischke, B., Dengel, A., & Borth, D. (2019). *EuroSAT: A Novel Dataset and Deep Learning Benchmark for Land Use and Land Cover Classification*. IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, 12(7), 2217–2226. https://doi.org/10.1109/JSTARS.2019.2918242

Please consult the dataset's distribution terms and the relevant model and software licences before redistributing associated materials.
