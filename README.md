# SAM 3 Export to ONNX and TFLITE

## Model

* Visit https://huggingface.co/facebook/sam3 and accept the license agreement
* Authenticate huggingface-cli
* The export script will automatically download the required files

## Requirements

onnx

```
torch 2.2.1
onnx 1.16.2
```

tflite

```
torch 2.4.0
ai-edge-torch 0.2.0
tf-nightly 2.18.0.dev20240811 for image mode
tf-nightly 2.18.0.dev20240905 for video mode
```

## Export and Inference

onnx

```
python3 export_image_predictor.py --framework onnx
python3 export_video_predictor.py --framework onnx
```

tflite

```
export PJRT_DEVICE=CPU
python3 export_image_predictor.py --framework tflite
python3 export_video_predictor.py --framework tflite
```

## Inference only

onnx

```
download_onnx_models.sh
python3 export_image_predictor.py --framework onnx --mode import
python3 export_video_predictor.py --framework onnx --mode import
```

tflite

```
download_tflite_models.sh
python3 export_image_predictor.py --framework tflite --mode import
python3 export_video_predictor.py --framework tflite --mode import
python3 export_image_predictor.py --framework tflite --mode import --image_size 512
python3 export_video_predictor.py --framework tflite --mode import --image_size 512
```

## Test

Replacing the complex tensor of RotaryEnc with matmul. To test this behavior, you can also run it with torch.

```
python3 export_video_predictor.py --framework torch
```

## Artifacts

The deliverables will be stored below.

```
output/*
model/*
```

