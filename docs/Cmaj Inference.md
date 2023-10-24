# Inference in Cmajor

In Cmajor, you may want to run inference on a machine learning model that has been trained for a real time application. Inference in Cmajor is made simple, with integration with the ONNX format. With our ONNX to Cmajor python script, a Cmajor patch is outputted, routing your model through the intermediate representation of ONNX operators that have been created in Cmajor.

ONNX operators are part of the ONNX Intermediate Representation (IR), which is a common format used for exchanging models. This format includes not only the model's architecture but also its weights and other metadata.

## What are ONNX Operators?

ONNX operators provide a standardised way to represent these operations, regardless of the deep learning framework used to define or train the model. This means that if you have a neural network model built in one framework (e.g. PyTorch or TensorFlow) and you want to run it on a different platform or framework, you can use ONNX to convert and execute the model seamlessly with Cmajor.

## Using the ONNX to Cmajor Python script

The command line options are given as follows:

```
    This script generates cmajor for the supplied ONNX model
    Options:

    -h                  Show the help
    --model [s]         Specifies the ONNX model to convert
    --patchDir [s]      Writes the output as a patch to the given directory

    If no patchDir is specified, a single cmajor file is output which depends on
    the Cmajor ml operators
```

to run this script, options are given as:

```shell
onnxToCmajor.py --model "path/to/your/model.onnx" --patchDir "path/to/output/patch"
```

this will output `model.cmajor`, `model.cmajorpatch` and `onnx.cmajor` to the given patch directory.

#### model.cmajor

`model.cmajor` contains all the nodes, connections and weights required for inference to run.

#### onnx.cmajor

`onnx.cmajor` contains all the operators generated in cmajor. This is where nodes in `model.cmajor` are defined.

#### model.cmajorpatch

As with all cmajor manifest files, this file describes the patch's properties and contains links to the other files in the patch.

### Currently supported ONNX Operators:

| Operator   |
|------------|
|`Tanh`|
|`Reshape`|
|`MatMul`|
|`Gemm`|
|`Add`|
|`Unsqueeze`|
|`Squeeze`|
|`Conv`|
|`GRU`|
|`Pad`|
|`Transpose`|
|`Constant`|
|`LSTM`|
|`Slice`|
|`Gather`|
|`Concat`|