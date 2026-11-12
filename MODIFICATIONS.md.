# Technical Modifications

## Overview

This project extends the original
[Price-Optimization repository](https://github.com/dlifeofjay/Price-Optimization)
by making unit cost independently adjustable.

The original trained machine learning model was retained.

## 1. Original Cost Assumption

The original application assumed unit cost was 70% of selling price.

`cost = price * 0.7`

This meant the estimated cost changed automatically whenever the selling price changed.

## 2. Modified Backend

I updated the pricing function to accept an additional input:

`price_optim(data, unit_cost)`

I then changed the profit calculation to:

`profit = (price - unit_cost) * new_demand`

This allows profit to be calculated using a user-selected unit cost rather than a fixed percentage.

## 3. Frontend Integration

I added a Cost per Unit slider to the Streamlit dashboard.

The selected value is passed to the Python backend when the user runs an optimization.

The backend recalculates estimated profits using the selected unit cost, and the dashboard displays the updated results and graphs.

## 4. What Stayed the Same

The pretrained machine learning model and preprocessing pipeline were not retrained or replaced.

Changing unit cost affects the estimated profit calculation, not the model's demand predictions.

## 5. Result

These modifications allowed me to test how different unit costs affect estimated profitability and price recommendations without editing Python code for every experiment.

This document describes my modifications to the original project. It is not a complete standalone implementation.

## Attribution

Original application: [dlifeofjay/Price-Optimization](https://github.com/dlifeofjay/Price-Optimization)

Full credit for the original application and pretrained model belongs to its creator.
