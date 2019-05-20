<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tft.scale_to_z_score_per_key" />
<meta itemprop="path" content="Stable" />
</div>

# tft.scale_to_z_score_per_key

``` python
tft.scale_to_z_score_per_key(
    x,
    key=None,
    elementwise=False,
    name=None,
    output_dtype=None
)
```

Returns a standardized column with mean 0 and variance 1, grouped per key.

Scaling to z-score subtracts out the mean and divides by standard deviation.
Note that the standard deviation computed here is based on the biased variance
(0 delta degrees of freedom), as computed by analyzers.var.

#### Args:

* <b>`x`</b>: A numeric `Tensor` or `SparseTensor`.
* <b>`key`</b>: A Tensor or `SparseTensor` of dtype tf.string.  If `x` is a
      `SparseTensor`, `key` must exactly match `x` in everything except
      values.
* <b>`elementwise`</b>: If true, scales each element of the tensor independently;
      otherwise uses the mean and variance of the whole tensor.
      Currently, not supported for per-key operations.
* <b>`name`</b>: (Optional) A name for this operation.
* <b>`output_dtype`</b>: (Optional) If not None, casts the output tensor to this type.


#### Returns:

A `Tensor` or `SparseTensor` containing the input column scaled to mean 0
and variance 1 (standard deviation 1), grouped per key.
That is, for all keys k: (x - mean(x)) / std_dev(x) for all x with key k.
If `x` is floating point, the mean will have the same type as `x`. If `x` is
integral, the output is cast to tf.float32.

Note that TFLearn generally permits only tf.int64 and tf.float32, so casting
this scaler's output may be necessary.