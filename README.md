# Crypto_Portfolio_Optimizer
Assembling optimized investment portfolios based on cryptocurrency.

---

## Technologies

This project leverages python 3.7 with the following:

* [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/) - JupyterLab is a web-based user interface designed for data analysis.

* [pandas](https://github.com/pandas-dev/pandas) - Flexible and powerful data analysis / manipulation library for Python.

* [matplotlib inline](https://github.com/matplotlib/matplotlib) - Comprehensive library for creating static, animated, and interactive visualizations in Python.

* [sklearn](https://github.com/scikit-learn/scikit-learn) - Simple and efficient tools for predictive data analysis.

---

### Installation Guide

Before running the application first install the following dependencies.

```python
  pip install jupyterlab
  pip install pandas
  pip install matplotlib
  pip install 
```

---

## Examples

**Plotting data using hvPlot.**
```
df_market_data.hvplot.line(
    width=800,
    height=400,
    rot=90
)

```
**Creating a DataFrame with scaled data, setting index, displaying data.**
```
df_market_data_scaled = pd.DataFrame(
    scaled_data,
    columns=df_market_data.columns)

df_market_data_scaled["coin_id"] = df_market_data.index

df_market_data_scaled = df_market_data_scaled.set_index("coin_id")

df_market_data_scaled.head()
```

**Setting k-values using range from 1 to 11, creating empty list, and creating a for loop to compute the inertia with each possible value of k.**
```
k = list(range(1,11))

inertia = []

for i in k:
    model = KMeans(n_clusters=i, random_state=0)
    model.fit(df_market_data_scaled)
    inertia.append(model.inertia_)
    
inertia
```

**Creating a dictionary with inertia data to plot the Elbow curve.**
```
elbow_data = {
    "k":k,
    "inertia":inertia
}

df_elbow_data = pd.DataFrame(elbow_data)
```

**Initializing the K-Means model using the best value for k, predicting clusters to group cryptocurrencies using scaled data, viewing reulting array of cluster values.**
```
model = KMeans(n_clusters=4)

model.fit(df_market_data_scaled)

clusters=model.predict(df_market_data_scaled)

print(clusters)

```

**Creating a scatter plot using hvPlot.**
```
df_market_data_scaled.hvplot.scatter(
    x="price_change_percentage_24h",
    y="price_change_percentage_7d",
    by="Clusters",
    hover_cols=["coin_id"],
    title="Scatter Plot of Cryptocurrencies k=4")
```

**Setting k-values using range from 1 to 11, creating empty list, and creating a for loop to compute the inertia_pca with each possible value of k_pca.**
```
k_pca=list(range(1,11))

inertia_pca=[]

for i in k_pca:
    model = KMeans(n_clusters=i, random_state=0)
    model.fit(df_market_data_pca)
    inertia_pca.append(model.inertia_)
    
inertia_pca

```

---

## Usage

To use the portfolio management application simply clone the repository and run the **crypto_investments.py** with:

```python
python crypto_investments.py
```

---

## Contributors

Brought to you by Robert Giannini.
LinkedIn: https://www.linkedin.com/in/robertgianninijr/

---

## License

MIT