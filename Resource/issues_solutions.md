# Issues and Solutions met

## Tensorflow

1. - [Issue]:train_and_evaluate AttributeError: 'NoneType' object has no attribute 'merge_call'
   - [Solution]: Can't, 1.10 issueshttps://github.com/tensorflow/tensorflow/issues/21412
   - [Detail]:  
   ```python
   File
   "/usr/local/lib/python2.7/dist-packages/tensorflow/python/estimator/estimator.py", line 1474, in _evaluate_build_graph
    model_fn_lib.LOSS_METRIC_KEY] = metrics_lib.mean(estimator_spec.loss)
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/metrics_impl.py", line 376, in mean
      mean_t = distribute_lib.get_tower_context().merge_call(
    AttributeError: 'NoneType' object has no attribute 'merge_call'
    ```
2. - [Issue]: memory issues
   - [Solution]: 
   1) check network, especially fc layer. 
   2) check channels_first and channels_last 
   3) input shape is too large, resize. 
   4) check optimizer like Adam
   5) check batch size
   - [Detail]:
   ```python
    2018-08-06 05:47:33.110207: W tensorflow/core/framework/op_kernel.cc:1295] OP_REQUIRES failed at constant_op.cc:75 : Resource exhausted: OOM when allocating tensor of shape [32256512,512] and type float
    2018-08-06 05:47:57.037241: E tensorflow/core/common_runtime/executor.cc:696] Executor failed to create kernel. Resource exhausted: OOM when allocating tensor of shape [32256512,512] and type float
            [[Node: block_output_fc1/kernel/Adam/Initializer/zeros = Const[dtype=DT_FLOAT, value=Tensor<type: float shape: [32256512,512] values: [0 0 0]...>, _device="/job:localhost/replica:0/task:0/device:GPU:0"]()]]
    ```
3. - [issue] loss is very big > 20, can not overfit with very small dataset  
   - [Solution] add reshape after tf.one_hot:
   ```python
    label = tf.one_hot(label, NUM_CLASSES)
    label = tf.reshape(label, [NUM_CLASSES])
   ```
4. - [issue] tensorflow.python.framework.errors_impl.NotFoundError: Failed to create a NewWriteableFile:
   - [Solution] change a location not used.
   - [Detail] as below:
   ```python
    Exception in thread Thread-16:Traceback (most recent call last):
    File "D:\ProgramData\Anaconda3\envs\tensorflow362\lib\threading.py", line 916, in _bootstrap_inner
      self.run()
    File "D:\ProgramData\Anaconda3\envs\tensorflow362\lib\threading.py", line 864, in run
      self._target(*self._args, **self._kwargs)
    File "build_medical_data.py", line 264, in _process_dicom_files_batch
      writer = tf.python_io.TFRecordWriter(output_file)
    File "D:\ProgramData\Anaconda3\envs\tensorflow362\lib\site-packages\tensorflow\python\lib\io\tf_record.py", line 112, in __init__
      compat.as_bytes(path), compat.as_bytes(compression_type), status)
    File "D:\ProgramData\Anaconda3\envs\tensorflow362\lib\site-packages\tensorflow\python\framework\errors_impl.py", line 519, in __exit__
      c_api.TF_GetCode(self.status.status))
    tensorflow.python.framework.errors_impl.NotFoundError: Failed to create a NewWriteableFile: D:\\tmp\\ct\\ouput\train-00028-of-00032.tfrecords : ϵͳ\udcd5Ҳ\udcbb\udcb5\udcbdָ\udcb6\udca8\udcb5\udcc4·\udcbe\udcb6\udca1\udca3
    ; No such process
    ```
5. - [issue] RuntimeError: Use DistributionStrategy.update() to modify a MirroredVariable.
   - [solution]
        tf 1.9 not support accuracy, disable it in distribution mode. 
   - [detail]
   ```python
     File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/metrics_impl.py", line 409, in accuracy
    name or 'accuracy')
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/metrics_impl.py", line 332, in mean
      update_total_op = state_ops.assign_add(total, math_ops.reduce_sum(values))
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/state_ops.py", line 187, in assign_add
      return ref.assign_add(value)
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/contrib/distribute/python/values.py", line 313, in assign_add
      return self.get(device=_get_update_device()).assign_add(*args, **kwargs)
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/contrib/distribute/python/values.py", line 285, in _get_update_device
      "Use DistributionStrategy.update() to modify a MirroredVariable.")
    RuntimeError: Use DistributionStrategy.update() to modify a MirroredVariable.
   ```

6. - [issue] tensorflow.python.framework.errors_impl.InvalidArgumentError: Number of ways to split should evenly divide the split dimension, but got split_dim 0 (size = 26) and num_split 8
   - [solution] make sure num of labels % num_gpus == 0
   - [detail]
   ```python
    File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/estimator/estimator.py", line 453, in evaluate
        input_fn, hooks, checkpoint_path)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/estimator/estimator.py", line 1348, in _evaluate_build_graph
        features, labels, model_fn_lib.ModeKeys.EVAL, self.config)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/estimator/estimator.py", line 1107, in _call_model_fn
        model_fn_results = self._model_fn(features=features, **kwargs)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/contrib/estimator/python/estimator/replicate_model_fn.py", line 230, in replicated_model_fn
        features, labels, len(devices), device=consolidation_device)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/contrib/estimator/python/estimator/replicate_model_fn.py", line 504, in _split_batch
        label_shards = array_ops.split(labels, number_of_shards)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/array_ops.py", line 1315, in split
        axis=axis, num_split=num_or_size_splits, value=value, name=name)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/ops/gen_array_ops.py", line 7793, in split
        "Split", split_dim=axis, value=value, num_split=num_split, name=name)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/framework/op_def_library.py", line 787, in _apply_op_helper
        op_def=op_def)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/framework/ops.py", line 3414, in create_op
        op_def=op_def)
      File "/usr/local/lib/python2.7/dist-packages/tensorflow/python/framework/ops.py", line 1740, in __init__
        self._traceback = self._graph._extract_stack()  # pylint: disable=protected-access

    InvalidArgumentError (see above for traceback): Number of ways to split should evenly divide the split dimension, but got split_dim 0 (size = 26) and num_split 8
            [[Node: split_inputs/split_1 = Split[T=DT_INT64, num_split=8, _device="/job:localhost/replica:0/task:0/device:CPU:0"](split_inputs/split/split_dim, IteratorGetNext:1)]]
            [[Node: split_inputs/split_1/_31 = _Recv[client_terminated=false, recv_device="/job:localhost/replica:0/task:0/device:GPU:5", send_device="/job:localhost/replica:0/task:0/device:CPU:0", send_device_incarnation=1, tensor_name="edge_444_split_inputs/split_1", tensor_type=DT_INT64, _device="/job:localhost/replica:0/task:0/device:GPU:5"]()]]
   ```

7. - [issue]
   - [solution]
   - [detail]
   ```python
   
   ```

8. - [issue]
   - [solution]
   - [detail]
   ```python
   
   ```

## Caffe

## Pytorch