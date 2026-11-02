#                                              IIT-G_Internship Summary
##                                Time Series Forecasting on Wind Power Generation Data

1.Chronos Model - 
Aim: Demonstrate and evaluate the performance of the Chronos model (amazon/chronos-t5-small) for zero-shot time
series forecasting on wind power generation data, assessing forecasting effectiveness without any task-specific training
via Mean Squared Error (MSE), Mean Absolute Error (MAE), and inference latency.

✦ KEY RESULT:
Results are consolidated in results_chronos_wind.csv and visualized as MSE vs. forecast horizon. As the
forecast horizon increases, both MSE and MAE tend to rise, indicating longer-term predictions are more
challenging. MSE for a 24-step horizon is approximately 0.051, rising to about 0.076–0.077 for horizons of
192 and 336 steps. Inference latency also increases with horizon length due to the larger number of
prediction steps and chunking operations.

2.PatchTST Model - 
Aim: Demonstrate the performance of the PatchTST model on wind power generation data for multi-horizon forecasting,
comparing performance under two data availability scenarios — the full dataset versus a significantly smaller (10%)
portion of training data — across various forecast horizons.

✦ KEY RESULT:
Results are consolidated in results_patchtst_wind.csv. MSE generally increases as the forecast horizon
grows, indicating longer-term predictions are more challenging. The model trained with the full dataset
(train_frac = 1.0) consistently achieves a significantly lower MSE than the model trained on only 10% of the
data (train_frac = 0.1), underscoring the importance of data volume for forecasting accuracy — confirmed
visually by the full-data curve sitting well below the low-data curve.

3.Data Efficiency Comparison — PatchTST and Chronos - 
Aim: Conduct a data efficiency comparison between PatchTST and Chronos, evaluating how each model performs under
varying data availability and across different forecast horizons — training PatchTST on full and reduced datasets, and
testing Chronos in zero-shot settings with full and short context lengths — to understand robustness and predictive
accuracy.

✦ KEY RESULT:
Results are consolidated in results_data_efficiency_comparison.csv. PatchTST with full data generally
achieves the lowest MSE overall; PatchTST with 10% data outperforms Chronos with a short context.
Chronos with full context performs reasonably well but degrades more sharply at longer horizons compared
to PatchTST. As a zero-shot model, Chronos requires no training time, but shows higher inference latency
and significantly more parameters than PatchTST — highlighting trade-offs between model complexity,
data efficiency, and performance.
