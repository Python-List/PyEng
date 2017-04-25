# File: noisy.py
* Warning: ComplexWarning: Casting complex values to real discards the imaginary part
  return array(a, dtype, copy=False, order=order)

* Cause of the warning: `plt.plot((recovered_signal[:500]))`
  * Actually it is caused when plt.plot call in lines.py at line 685 `y = np.asarray(yconv, np.float_)`, as it converts a listof complexes to the np.float_ type, thus discarding the imaginary part

* Solution: Not having done such math in a long time, the solution with discarding the imaginary part looks correct, so the
simplest would be to discard the imaginary part before feeding it to plt.plot with:
```python
reals = [i.real for i in recovered_signal[:500]]
```