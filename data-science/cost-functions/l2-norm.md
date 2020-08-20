# L2 Norm

**L2 Norm, Mean Squared Error:** Take the mean of the square of the differences.

$$
\text{MSE}(y, \hat{y}) = \frac{1}{n_\text{samples}} \sum_{i=0}^{n_\text{samples} - 1} (y_i - \hat{y}_i)^2.
$$

```python
from sklearn.metrics import mean_squared_error
```

{% hint style="info" %}
[sklearn.metrics.mean\_squared\_error - scikit-learn 0.23.1 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)
{% endhint %}

```python
import numpy as np

def l2_norm(y, yhat): 
    """
    Mean squared error regression loss
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
    >>> l2_norm(y, yhat)
    0.375
    >>> y = np.array([[0.5, 1], [-1, 1], [7, -6]])
    >>> yhat = np.array([[0, 2], [-1, 2], [8, -5]])
    >>> l2_norm(y, yhat)
    0.708333...
    """
    return (y - yhat)**2).mean()
```

