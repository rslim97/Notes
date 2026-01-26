np.random.rand(2,3,4) -> standard uniform
np.random.random((2,3)) -> random_sample from standard uniform
np.random.uniform(0,5,(2,3)) -> non-standard uniform distribution

np.random.randn(2,3,4) -> standard normal
np.random.normal(0,5,(2,3)) -> non-standard normal distribution

```console
$a1 = np.random.rand(5,10,2)
$b1 = np.random.rand(5,5,2)
$np.hstack((a1,b1)).shape
(5,15,2)
$np.concatenate((a1,b1),axis=1)
a2 = np.random.rand(10,5,2)
b2 = np.random.rand(5,5,2)
$np.vstack((a2,b2)).shape
(15,5,2)
$np.concatenate((a2,b2),axis=0).shape
(15,5,2)
```
np.nonzero(J) -> returns tuples of indices of J that are nonzero
np.maximum(x1,x2) -> returns he maximum of _x1_ and _x2_, element-wise. This is a scalar if both _x1_ and _x2_ are scalars.
np.max(J, axis=1) -> Maximum of _a_. If _axis_ is None, the result is a scalar value. If _axis_ is an int, the result is an array of dimension `a.ndim - 1`. If _axis_ is a tuple, the result is an array of dimension `a.ndim - len(axis)`.
np.where(J>t,J,0) -> fills the position where the boolean condition is true with elements of J, 0 otherwise.

Get indices of N maximum values in a numpy array:
```
n=5
arr=np.random.rand(2,3)
x, y = np.unravel_index(np.argsort(arr.ravel(), axis=None)[::-1][:n], arr.shape)
```
