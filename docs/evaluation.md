# Evaluation and reproducibility

The archived final fusion run (run_5) used 1,854,819 complete-case ticker/date observations and purged 373 labels crossing split boundaries. Eligible training, validation and test counts were 890,777, 458,427 and 505,242. Local models trained on 150,000 sampled training keys (seed 42). Shared validation coverage was January 22, 2014–January 30, 2017, with 147,905 keys.

The 25/75 numerical/chart vote was chosen on validation balanced accuracy, then evaluated on 501,205 historical test keys: accuracy 49.83%, balanced accuracy 49.46%, UP precision 51.78%, UP recall 57.72%, UP F1 54.59%. Test confusion counts (TN, FP, FN, TP): 98,595; 140,755; 110,701; 151,154.

The validation result was dominated by UP predictions (99.56%, versus 51.52% actual UP). Consequently, the modest improvement over the training-majority baseline does not demonstrate reliable predictive power. Earlier test inspection, chart-model selection overlap, revised macroeconomic data and universe selection limit conclusions. No trading profitability, calibration or statistical significance was established.

Original reproduction command: `python run_fusion_experiments.py --max-train 150000`. This command requires the original source and data; this documentation edition does not include every dependency or input. Archived environment versions: pandas 3.1.0, numpy 2.5.4, scikit-learn 1.9.1, xgboost 3.4.1. These are recorded values, not a tested installation specification.
