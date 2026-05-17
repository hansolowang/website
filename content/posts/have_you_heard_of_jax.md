---
title: "Have You Heard of Jax"
date: 2022-11-22
draft: true
---

Jax can be envisioned as `numpy` with built in `autograd`, `vmal`, `pmap` and jit capabilities. This alone makes it one of the most versatile and powerful numerical methods library that handles multidimensional data. Jax makes it simple to write standard numpy code and immediately be able to

- Compute the gradient of a function via `jax.grad`
- Just-in-time compile a function to run efficiently with `jax.jit`
- Automagically vectorize a function with `jax.vmap`

# jax.grad
`jax.grad` takes a function and returns a new function that computes the gradient of the original function. The input function must have a scalar output.

Similarly, `jax.value_and_grad` returns a new function that evaluates both f and the gradient of f and returns them as a two-element tuple.
```python
import jax
def tanh(x: float):
    return (jnp.exp(z) - jnp.exp(-z)) / (jnp.exp(z) + jnp.exp(-z))

tanh_grad = jax.grad(tanh)
tanh_value_grad = jax.value_and_grad(tanh)

x_batch = jnp.arange(0,1,0.01)

g = tanh_grad(x)
v, g = tanh_value_grad(x)
```

Jax has a useful [`check_grads`](https://github.com/google/jax/blob/e50ef1b38366fbbc77d676d536e0dcde07c20af0/jax/_src/public_test_util.py#L261) function to check the gradients from automatic differentation against finite difference.


# jax.jit
Python is an interpreted language, which means that statements are executed one at a time. Code is sending one operation at a time to the compiler, each statement must execute and return a value before the interpretor runs the next.  

By jit compiling your code with `jax.jit`, jax sends the code to XLA for compilation. Operations may be rearranged or transformed to make the execution more efficient. 

For example

```python
import jax.numpy as jnp
def tanh(z: float):
	return (jnp.exp(z) - jnp.exp(-z)) / (jnp.exp(z) + jnp.exp(-z))
```

The above code has 4 or more distinct `jax.numpy` operations: `jax.exp`, `jnp.subtract`, `jnp.divide`, and `jnp.sum`, each of these executes individually in sequence, and each returns its output in a freshly-allocated buffer that is passed to the next operation. 

When you jit compile it, XLA can fuse  and re-arrange operations, and only needs to allocate one single buffer for the final output.
```python
tanh_jit = jax.jit(tanh)
```

# jax.vmap
`jax.vmap` is like map by Python but adds vectorization. You can express your computation for a single example, and then use vmap to run the computation for multiple examples at a time (aka adding batch dimension). This can help with performance as well.

```python
import jax
import jax.numpy as jnp

def squared_error(x, y):
    return (x - y)**2

x_batch = jnp.array([[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]])
y_batch = jnp.array([[4.0, 5.0, 6.0], [1.0, 2.0, 3.0]])

# Use vmap to vectorize the squared_error function
squared_errors = jax.vmap(squared_error)(x_batch, y_batch)

# The above vmap is equivalent to:
squared_errors = []
for x, y in zip(x_batch, y_batch):
    squared_errors.append(squared_error(x, y))
squared_errors = np.array(squared_errors)
```

# Gotchas
Jax works great for numerical problems but there are some [gotchas](https://jax.readthedocs.io/en/latest/notebooks/Common_Gotchas_in_JAX.html) to be aware of.