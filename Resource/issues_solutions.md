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

## Caffe

## Pytorch