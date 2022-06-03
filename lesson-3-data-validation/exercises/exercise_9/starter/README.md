# Exercise 8 

Using pytest fixtures for non-deterministic testing.

The `mlflow` approach fails with:
```
mlflow run -P reference_artifact=exercise_6/data_train.csv:latest -P sample_artifact=exercise_6/data_test.csv:latest -P ks_alpha=0.5 .
```
```
2022/06/03 16:25:12 INFO mlflow.projects.utils: === Created directory /var/folders/qd/b5vt_vps4rggfvjx_6vjpllm0000gn/T/tmp89kb1if_ for downloading remote URIs passed to arguments of type 'path' ===
2022/06/03 16:25:12 INFO mlflow.projects.backend.local: === Running command 'source /Users/bkozdemb/.local/miniforge3/bin/../etc/profile.d/conda.sh && conda activate mlflow-7398531e5288219e428182dc4d6601ae57991d39 1>&2 && pytest -s -vv . --reference_artifact exercise_6/data_train.csv:latest \
                --sample_artifact exercise_6/data_test.csv:latest \
                --ks_alpha 0.5' in run with ID '4e05606007f0482c99420421868b1939' === 
ImportError while loading conftest '/private/var/tmp/nd0821-c2-build-model-workflow-exercises/lesson-3-data-validation/exercises/exercise_9/starter/conftest.py'.
conftest.py:3: in <module>
    import wandb
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/__init__.py:38: in <module>
    from wandb import sdk as wandb_sdk
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/sdk/__init__.py:12: in <module>
    from .wandb_init import init  # noqa: F401
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/sdk/wandb_init.py:29: in <module>
    from .backend.backend import Backend
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/sdk/backend/backend.py:17: in <module>
    from ..interface import interface
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/sdk/interface/interface.py:18: in <module>
    from wandb.proto import wandb_internal_pb2 as pb
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/proto/wandb_internal_pb2.py:15: in <module>
    from wandb.proto import wandb_telemetry_pb2 as wandb_dot_proto_dot_wandb__telemetry__pb2
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/wandb/proto/wandb_telemetry_pb2.py:34: in <module>
    _descriptor.FieldDescriptor(
/Users/bkozdemb/.local/miniforge3/envs/mlflow-7398531e5288219e428182dc4d6601ae57991d39/lib/python3.9/site-packages/google/protobuf/descriptor.py:560: in __new__
    _message.Message._CheckCalledFromGeneratedFile()
E   TypeError: Descriptors cannot not be created directly.
E   If this call came from a _pb2.py file, your generated code is out of date and must be regenerated with protoc >= 3.19.0.
E   If you cannot immediately regenerate your protos, some other possible workarounds are:
E    1. Downgrade the protobuf package to 3.20.x or lower.
E    2. Set PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python (but this will use pure-Python parsing and will be much slower).
E
E   More information: https://developers.google.com/protocol-buffers/docs/news/2022-05-06#python-updates
2022/06/03 16:25:13 ERROR mlflow.cli: === Run (ID '4e05606007f0482c99420421868b1939') failed ===
```

Running `pytest` directly passes.

```
pytest -s -vv . --reference_artifact exercise_6/data_train.csv:latest --sample_artifact exercise_6/data_test.csv:latest --ks_alpha 0.5
```
```
wandb: Currently logged in as: koz (use `wandb login --relogin` to force relogin)
wandb: wandb version 0.12.17 is available!  To upgrade, please run:
wandb:  $ pip install wandb --upgrade
wandb: Tracking run with wandb version 0.10.31
wandb: Syncing run super-morning-4
wandb:  View project at https://wandb.ai/koz/exercise_9
wandb:  View run at https://wandb.ai/koz/exercise_9/runs/2bbcal06
wandb: Run data is saved locally in /private/var/tmp/nd0821-c2-build-model-workflow-exercises/lesson-3-data-validation/exercises/exercise_9/starter/wandb/run-20220603_162622-2bbcal06
wandb: Run `wandb offline` to turn off syncing.

============================================================================= test session starts ==============================================================================
platform darwin -- Python 3.9.12, pytest-7.1.2, pluggy-1.0.0 -- /Users/bkozdemb/.local/miniforge3/envs/mlops/bin/python3.9
cachedir: .pytest_cache
rootdir: /private/var/tmp/nd0821-c2-build-model-workflow-exercises/lesson-3-data-validation/exercises/exercise_9/starter
plugins: anyio-3.6.1, hydra-core-1.0.6
collected 1 item                                                                                                                                                               

test_data.py::test_kolmogorov_smirnov PASSED

============================================================================== 1 passed in 3.33s ===============================================================================

wandb: Waiting for W&B process to finish, PID 1215
wandb: Program ended successfully.
wandb:                                                                                
wandb: Find user logs for this run at: /private/var/tmp/nd0821-c2-build-model-workflow-exercises/lesson-3-data-validation/exercises/exercise_9/starter/wandb/run-20220603_162622-2bbcal06/logs/debug.log
wandb: Find internal logs for this run at: /private/var/tmp/nd0821-c2-build-model-workflow-exercises/lesson-3-data-validation/exercises/exercise_9/starter/wandb/run-20220603_162622-2bbcal06/logs/debug-internal.log
wandb: Synced 6 W&B file(s), 0 media file(s), 0 artifact file(s) and 0 other file(s)
wandb: 
wandb: Synced super-morning-4: https://wandb.ai/koz/exercise_9/runs/2bbcal06
```