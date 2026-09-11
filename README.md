Huihui-Qwen vLLM Deployment

Production-ready deployment kit for running the Huihui-Qwen3.8-27B-abliterated model using vLLM and Docker. This configuration includes custom XML tool parsing (qwen3_xml) to support native function-calling and web-search skills without hanging or breaking token streams.
Prerequisites

    Linux environment with an NVIDIA GPU (Ampere architecture or newer recommended)

    NVIDIA Driver installed and active

    Docker installed with the NVIDIA Container Toolkit configured

One-Command Deployment

To set up and launch the server immediately with a single command, use the unified deploy.sh script:
Bash

curl -sSL https://raw.githubusercontent.com/yanbo12338/abliterated-qwen-server/main/deploy.sh | bash

Alternatively, if you have cloned the repository locally, run:
Bash

chmod +x deploy.sh && ./deploy.sh

Repository Scripts

    deploy.sh - Full automated installer: pulls the latest vLLM image, creates cache volumes, boots the container, and optionally streams live logs.

    start.sh - Starts the container using optimized vLLM parameters and tool-call parsers.

    start_w_logs.sh - Launches the model and provides an interactive prompt (y/n) to open live server logs.

    stop.sh - Gracefully stops and removes the running container.

Manual Setup & Usage

    Clone the repository:
    Bash

    git clone https://github.com/YOUR_USERNAME/huihui-qwen-vllm.git
    cd huihui-qwen-vllm

    Make scripts executable:
    Bash

    chmod +x *.sh

    Run for the first time:
    Bash

    ./deploy.sh

    Manage the server:

        Start: ./start.sh

        Stop: ./stop.sh

API Endpoint Reference

Once running, the vLLM server exposes an OpenAI-compatible API at http://localhost:8000/v1.

Test the deployment using curl:
Bash

curl http://localhost:8000/v1/models
