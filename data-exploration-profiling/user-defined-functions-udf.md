---
description: User defined functions (UDFs) to help analyze data faster
---

# 🍧 User Defined Functions (UDF)

As part of our 0.9.4 release users can now define custom functions that show up under AutoStats. If the following code snippets are run in CNext you'll see additional AutoStats options pop up in the UI.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>UDFs for data analysis will show up underneath the AutoStats drop down.</p></figcaption></figure>

CNext will default load histograms and quantiles underneath AutoStats, but the following are provided as examples.&#x20;

```python
@register_udf(Config("histogram", OutputType.IMAGE, 
                     {Location.TABLE_HEADER: View(Position(1, 0)),
                     Location.SUMMARY: View(Position(0, 1))}))
def histogram(df_id, col_name):
    _df = globals()[df_id]
    plt.figure(figsize=(8,4))
    sns.histplot(_df[col_name], color="#3283FE")
    plt.xlabel(""); plt.ylabel(""); plt.show()
```

The following is an example for quantile stats.&#x20;

```python
@register_udf(Config("quantile", OutputType.IMAGE,
                     {Location.SUMMARY: View(Position(0, 0)), 
                      Location.TABLE_HEADER: View(Position(1, 0))}))
def quantile(df_id, col_name):
    _df = globals()[df_id]
    if _df[col_name].dtypes not in ["object"]:
        plt.figure(figsize=(10,2))
        sns.boxplot(data=_df, x=col_name, color="#3283FE")
        plt.xlabel(""); plt.ylabel(""); plt.show()
```

The following is an example for missing values for the df\_housing data frame (this is created from our sample dataset).&#x20;

```python
@register_udf(Config("missing values", OutputType.IMAGE,
                     {Location.SUMMARY: View(Position(0, 2), Shape(200, 50))}))
def missing_value(df_id, col_name):    
    _df = globals()[df_id]
    if str(type(df_housing)) == "<class 'cnextlib.dataframe.DataFrame'>":
        _df = _df.df
    if _df[col_name].isna().sum() > 0:
        plt.figure(figsize=(5,0.5))
        res = sns.heatmap(_df[[col_name]].isna().transpose(), fmt="g", 
                          cmap=sns.color_palette("Blues_r"), 
                          yticklabels=False, xticklabels=False, cbar=False) 
        for _, spine in res.spines.items():
            spine.set_visible(True)
            spine.set_linewidth(0.5)
        plt.show() 
```
