# Issues and Solutions met

## Tensorflow

1. 
> - [Issue]:train_and_evaluate AttributeError: 'NoneType' object has no attribute 'merge_call'
> - [Solution]: Can't, 1.10 issues
https://github.com/tensorflow/tensorflow/issues/21412
> - [Detail]:  File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/estimator/estimator.py", line 1474, in _evaluate_build_graph
    model_fn_lib.LOSS_METRIC_KEY] = metrics_lib.mean(estimator_spec.loss)
  File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/metrics_impl.py", line 376, in mean
    mean_t = distribute_lib.get_tower_context().merge_call(
AttributeError: 'NoneType' object has no attribute 'merge_call'

2.
> - [Issue]:
> - [Solution]:
> - [Detail]:
## Caffe

## Pytorch