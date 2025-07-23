# Mochi Worker for RunPod

This worker provides a RunPod serverless endpoint for Mochi, a text-to-video model from Kijai.

## Features

- Generate videos from text prompts using Mochi
- Customize video dimensions, number of frames, and other parameters
- Optimized for performance on RunPod infrastructure

## API Reference

### Input Parameters

```json
{
  "input": {
    "positive_prompt": "a cat playing with yarn, cute, fluffy, detailed fur",
    "negative_prompt": "",
    "width": 848,
    "height": 480,
    "seed": 42,
    "steps": 40,
    "cfg": 6,
    "num_frames": 31,
    "vae": {
      "enable_vae_tiling": false,
      "tile_sample_min_width": 312,
      "tile_sample_min_height": 160,
      "tile_overlap_factor_width": 0.25,
      "tile_overlap_factor_height": 0.25,
      "auto_tile_size": false,
      "frame_batch_size": 8
    }
  }
}
```

### Output

The worker returns a URL to the generated video.

## Local Development

### Prerequisites

- Docker
- NVIDIA GPU with CUDA support
- Git LFS

### Setup

1. Clone this repository
2. Copy `.env.example` to `.env` and configure as needed
3. Run `docker-compose up --build`

## Deployment

### RunPod

1. Create a new serverless template on RunPod
2. Use the Docker image `runpod/worker-mochi:latest`
3. Configure the template with appropriate GPU resources
4. Deploy the endpoint

## Models

This worker uses the following models:

- Mochi Preview DIT (BF16)
- Mochi Preview VAE Decoder (BF16)
- Google T5-v1.1-XXL Encoder Only (FP16)

## License

See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Kijai](https://github.com/kijai) for creating Mochi
- [ComfyUI](https://github.com/comfyanonymous/ComfyUI) for the backend framework
- [RunPod](https://runpod.io) for the serverless infrastructure