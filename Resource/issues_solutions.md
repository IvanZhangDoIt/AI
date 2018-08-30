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
> - [Issue]: memory issues
> - [Solution]: 
   1) check network, especially fc layer. 
   2) check channels_first and channels_last 
   3) input shape is too large, resize. 
   4) check optimizer like Adam
   5) check batch size
> - [Detail]:
>> 2018-08-06 05:47:33.110207: W tensorflow/core/framework/op_kernel.cc:1295] OP_REQUIRES failed at constant_op.cc:75 : Resource exhausted: OOM when allocating tensor of shape [32256512,512] and type float
2018-08-06 05:47:57.037241: E tensorflow/core/common_runtime/executor.cc:696] Executor failed to create kernel. Resource exhausted: OOM when allocating tensor of shape [32256512,512] and type float
         [[Node: block_output_fc1/kernel/Adam/Initializer/zeros = Const[dtype=DT_FLOAT, value=Tensor<type: float shape: [32256512,512] values: [0 0 0]...>, _device="/job:localhost/replica:0/task:0/device:GPU:0"]()]]

3. - [issue] loss is very big > 20, can not overfit with very small dataset  
   - [Solution] add reshape after tf.one_hot:
   ```python
    label = tf.one_hot(label, NUM_CLASSES)
    label = tf.reshape(label, [NUM_CLASSES])
   ```

## Caffe

## Pytorch