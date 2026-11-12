# Reproducing the AI Pricing Simulator Experiments

## Original Project

This project is a replication and extension of [Price-Optimization by dlifeofjay](https://github.com/dlifeofjay/Price-Optimization).

The original project provides the pretrained demand prediction model, preprocessing pipeline, and Streamlit application.

My experiments used that original model with modifications to the profit calculations and dashboard.

## Technical Setup

The simulator was run locally using Python 3.11, Streamlit, NumPy, and the dependencies included in the original project's `requirements.txt`.

To set up the original application:

1. Download the original repository.
2. Open the project folder in VS Code.
3. Create and activate a Python virtual environment.
4. Install the dependencies with `pip install -r requirements.txt`.
5. Ensure the pretrained model and preprocessing files have downloaded correctly, including any files managed through Git LFS.
6. Run the Streamlit application using `streamlit run app.py`.

**Important:** The original repository does not include my modifications. To reproduce the modified results, the unit-cost changes described below must also be implemented locally.

## My Technical Modifications

The original simulator calculated unit cost as 70% of the selling price.

I modified the backend to calculate profit using an independently selected unit cost:

`profit = (price - unit_cost) * new_demand`

I also added a Cost per Unit slider to the Streamlit dashboard and passed its value into the `price_optim(data, unit_cost)` function.

The trained demand prediction model was not modified or retrained.

## Experiment 1 — Changing Unit Cost

**Settings:**

- Optimization Goal: Profit
- Week: 1
- Store Branch ID: 55
- Meal ID: 1885
- Starting Price: $130
- Email Promotions: True
- App Homepage Promotions: True
- Discount: 10%
- Product Category: Beverages
- Product Cuisine: Thai
- Maximum Price Increase: 20%

**Test:** Change only the unit cost from $60 to $120 and run the optimization again.

| Result | $60 Cost | $120 Cost |
|---|---:|---:|
| Recommended Price | $156 | $156 |
| Predicted Demand | 1,601 | 1,601 |
| Estimated Profit | $153,736.32 | $57,651.12 |

The recommended price remained unchanged, while estimated profit decreased significantly.

## Experiment 2 — Expanding the Price Range

Starting Price: $130

| Result | 20% Limit | 50% Limit |
|---|---:|---:|
| Highest Tested Price | $156 | $195 |
| Recommended Price | $156 | $195 |
| Predicted Demand | 1,601 | 1,598 |

The simulator generated 20 candidate prices for each scenario using NumPy's `linspace` function.

Expanding the price range changed the recommended price. In both tests, the simulator selected the highest price available.

The original 50% screenshot does not display the unit-cost setting, so this comparison should not be interpreted as a fully verified controlled cost experiment.

## Model Evaluation

The Evaluation Dashboard compares actual demand with predicted demand from the evaluation dataset.

The results showed that the model followed many demand patterns but did not always predict the exact outcomes.

This suggests that the simulator can support pricing experiments, but its recommendations need real-world validation.

## Limitations

- Results depend on the trained model and selected price range.
- Predicted demand is not guaranteed future demand.
- Estimated profit excludes fixed business costs.
- Changing prices in a prediction model does not establish how customers would respond in a real experiment.
- The original model's training procedure was not independently reproduced.

## Reproduction and Attribution Note

This repository currently documents the experiment methodology and results; it does not contain a complete runnable copy of the modified simulator.

The original code and pretrained model belong to the original creator. Full credit goes to [dlifeofjay](https://github.com/dlifeofjay/Price-Optimization).
