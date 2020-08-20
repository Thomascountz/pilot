# L1 Norm

**L1 Norm, Mean Absolute Error:** Take the mean of the absolute value of the differences.

$$
\text{MAE}(y, \hat{y}) = \frac{1}{n_{\text{samples}}} \sum_{i=0}^{n_{\text{samples}}-1} \left| y_i - \hat{y}_i \right|
$$

L1 Norm's slope isn't continuous near the minimum—it's slope doesn't get smaller as it approaches the minimum. This is because of the V-shape formed by taking the absolute value.

```python
from sklearn.metrics import mean_absolute_error
```

{% hint style="info" %}
[sklearn.metrics.mean\_absolute\_error - scikit-learn 0.23.1 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)
{% endhint %}

```python
import numpy as np

def l1_norm(y, yhat): 
    """
    Mean absolute error regression loss
    Parameters
    ----------
    y    : array-like of shape (n_samples,) or (n_samples, n_outputs)
        Ground truth (correct) target values.
    yhat : array-like of shape (n_samples,) or (n_samples, n_outputs)
        Estimated target values.
   
    Returns
    -------
    loss : float 
      
    Examples
    --------
    >>> y = np.array([3, -0.5, 2, 7])
    >>> yhat = np.array([2.5, 0.0, 2, 8])
    >>> l1_norm(y, yhat)
    0.5
    >>> y = np.array([[0.5, 1], [-1, 1], [7, -6]])
    >>> yhat = np.array([[0, 2], [-1, 2], [8, -5]])
    >>> l1_norm(y, yhat)
    0.75
    """
    return np.absolute((y - yhat)).mean()
```

