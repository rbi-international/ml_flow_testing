# MLflow Experiment Tracking with DagsHub

This repository demonstrates how to track machine learning experiments using MLflow with DagsHub integration. The project trains a wine quality prediction model and logs all relevant metrics, parameters, and artifacts to DagsHub.

## Features

- MLflow experiment tracking with DagsHub integration
- Wine quality prediction using ElasticNet regression
- Secure authentication with environment variables
- Model logging and registration

## Prerequisites

- Python 3.7+
- DagsHub account (create one at [dagshub.com](https://dagshub.com) if you don't have one)
- Git

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/ml_flow_testing.git
   cd ml_flow_testing
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file in the project root directory with your DagsHub credentials:
   ```
   MLFLOW_TRACKING_USERNAME=your_dagshub_username
   MLFLOW_TRACKING_PASSWORD=your_dagshub_token
   ```

   To get your DagsHub token:
   - Go to your DagsHub profile settings
   - Navigate to "Applications"
   - Generate a new token with "repo" access
   - Copy and paste it into your `.env` file

4. Make sure to add `.env` to your `.gitignore` file to keep your credentials secure.

## Project Structure

```
ml_flow_testing/
├── .env                  # Environment variables (not committed to git)
├── .gitignore            # Git ignore file
├── README.md             # This file
├── requirements.txt      # Project dependencies
└── demo.py              # Main training script
```

## Usage

Run the training script with optional alpha and l1_ratio parameters:

```bash
python train.py 0.5 0.4
```

Default values (if not specified):
- alpha: 0.2
- l1_ratio: 0.3

## How It Works

1. The script loads environment variables from the `.env` file
2. Sets up MLflow tracking to point to your DagsHub repository
3. Loads and processes the wine quality dataset
4. Trains an ElasticNet regression model
5. Logs parameters (alpha, l1_ratio), metrics (RMSE, MAE, R²), and the model itself to DagsHub
6. Registers the model in the MLflow Model Registry (if available)

## Viewing Results

After running the script:

1. Go to your DagsHub repository
2. Navigate to the "Experiments" tab
3. View your tracked experiments, compare runs, and analyze results

## DagsHub Integration Explained

DagsHub extends Git to handle data, models, and experiments. The integration with MLflow allows you to:

- Track experiments in a centralized location
- Compare different runs with various parameters
- Version your models
- Share results with collaborators
- Create reproducible machine learning pipelines

## Customization

To use this with your own project:

1. Create a repository on DagsHub
2. Update the repository information in the code:
   ```python
   remote_server_uri = "https://dagshub.com/your-username/your-repo-name.mlflow"
   mlflow.set_tracking_uri(remote_server_uri)
   ```

3. Update your model training code while keeping the MLflow logging structure

## Troubleshooting

If you encounter authentication issues:
- Ensure your DagsHub token has the correct permissions
- Verify that your environment variables are loaded correctly
- Check that the repository path is correct in your tracking URI

## License

[MIT](LICENSE)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgements

- Wine Quality dataset from the UCI Machine Learning Repository
- MLflow documentation
- DagsHub for providing the experiment tracking platform