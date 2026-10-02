# Tree-Based Models Project (CS 4372, HW2)

Authors: TODO name (`netid`) and TODO name (`netid`)

This project builds and compares four tree models on a UCI or Kaggle dataset: a plain decision tree,
a random forest, AdaBoost, and XGBoost. Each is tuned with `GridSearchCV`, visualized, and evaluated on
one untouched test set. The notebook contains the code, outputs, plots, interpretations, and
hyperparameter experiment logs. The report uses a simple LaTeX `article` layout with a separate cover
page and contains no code snippets.

> **Status: scaffold.** The structure, section prompts, report layout, and file names are in place.
> The analysis itself is yours to write. Replace every `TODO` in the notebook, report, and this README.

## Files

- `Trees_Models.ipynb` - the analysis notebook (run top to bottom)
- `Trees_Models_Report.tex` - report source (every `\todo{...}` marks text to write)
- `Trees_Models_Report.pdf` - compiled report (create it with the commands below)
- `references.bib` - report bibliography
- `requirements.txt` - Python dependencies
- `figs/` - figures produced by the notebook and used by the report
- `results/` - CSV experiment logs and result tables produced by the notebook

## Suggested workflow

1. Choose a dataset and decide classification vs regression (see the note below), then fill in the
   "Analysis info" cell in the notebook and the metadata block at the top of the `.tex` file.
2. Host the data file publicly (for example a GitHub repository, then use its **raw** URL) and set
   `DATA_URL`, `COLUMNS`, and `TARGET` in the notebook's settings cell. Do not submit the dataset itself.
3. Work through the notebook one section at a time. After each section, write its interpretation in the
   notebook's text cell while the results are fresh.
4. Re-run with **Kernel > Restart & Run All** before moving on to the report.
5. Fill in the report using your notebook interpretations, then compile it.

## Run the notebook

Python 3.11 or later is recommended.

```bash
python -m pip install -r requirements.txt
jupyter notebook Trees_Models.ipynb
```

Open the notebook and choose **Kernel > Restart & Run All**. Run it from this project directory so the
generated figures remain under `figs/` and the experiment logs remain under `results/`. The notebook reads
the data from a public URL, so no local dataset path is required:

TODO: paste the public data URL here.

Optional: `sklearn.tree.plot_tree` needs nothing extra, but Graphviz-based tree drawings (`graphviz`,
`xgboost.plot_tree`) also need the Graphviz program installed on your system
(<https://graphviz.org/download/>). A full run may take several minutes depending on the size of your grids.
Results are reproducible with the fixed `RANDOM_STATE` set in the notebook.

## Compile the report

A standard TeX Live or MiKTeX installation with `pdflatex`, `bibtex`, and the common packages named in
the report preamble is sufficient.

```bash
pdflatex Trees_Models_Report.tex
bibtex Trees_Models_Report
pdflatex Trees_Models_Report.tex
pdflatex Trees_Models_Report.tex
```

Keep `references.bib` and the `figs/` directory beside the `.tex` file when compiling. Figures that do not
exist yet show as grey placeholder boxes, so the report compiles at every stage.

## Planned figures

The notebook saves these names and the report expects them (edit both if you rename one):

| File | Content |
| --- | --- |
| `01_distributions` | Attribute distributions |
| `02_target_and_categoricals` | Target distribution and categorical relationships |
| `03_correlation_heatmap` | Training-set correlation heatmap |
| `04_target_correlations` | Predictor-target correlations |
| `05_feature_selection` | Evidence for the chosen attributes |
| `06_dt_tuning`, `07_dt_tree` | Decision tree tuning and the best tree |
| `08_rf_tuning`, `09_rf_tree_and_importance` | Random forest tuning, one tree, importances |
| `10_ada_tuning`, `11_ada_stump_and_importance` | AdaBoost tuning, a boosted tree, importances |
| `12_xgb_tuning`, `13_xgb_tree_and_importance` | XGBoost tuning, a tree, importances |
| `14_confusion_matrices` | Confusion matrices for the four models |
| `15_roc_curves` | ROC curves |
| `16_pr_curves` | Precision-recall curves |
| `17_model_comparison` | Headline test metrics across models |

## Planned result files

`feature_selection_log.csv`, `dt_experiment_log.csv`, `rf_experiment_log.csv`, `ada_experiment_log.csv`,
`xgb_experiment_log.csv`, and `model_comparison.csv`, all written to `results/`.

## Classification or regression?

The assignment allows either, but its required result analysis (confusion matrix, precision, recall,
F-statistic, ROC, and precision-recall curves) only exists for classification. The scaffold is therefore
written for a classification task. If you choose regression, swap in the regressor classes, change the
scoring metric, and replace those diagnostics with regression equivalents (residual plots, error
distributions, predicted-vs-actual plots). Check with the instructor on Canvas if unsure.

## Reproducibility notes

TODO: replace with notes specific to your dataset, for example how headers were handled, which rows were
removed and by what rule, how the split was made, and how preprocessing was kept inside training folds.
The notebook ends with a reproducibility checklist you can use as a starting point.
