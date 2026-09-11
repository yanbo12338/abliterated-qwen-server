Here is the corrected and polished version of your README.md file, fixing directory paths, script names, and cloning commands so everything works smoothly for anyone using your repository:
Markdown

# Huihui-Qwen vLLM Deployment

Production-ready deployment kit for running the **Huihui-Qwen3.8-27B-abliterated** model using vLLM and Docker. This configuration includes custom XML tool parsing (`qwen3_xml`) to support native function-calling and web-search skills without hanging or breaking token streams.

## Prerequisites

* Linux environment with an NVIDIA GPU (Ampere architecture or newer recommended)
* NVIDIA Driver installed and active
* Docker installed with the [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) configured

## One-Command Deployment

To set up, install prerequisites, and launch the server immediately with a single command, run the master install script:

```bash
curl -sSL [https://raw.githubusercontent.com/yanbo12338/abliterated-qwen-server/main/install.sh](https://raw.githubusercontent.com/yanbo12338/abliterated-qwen-server/main/install.sh) | bash

Alternatively, if you have already cloned the repository locally, run:
Bash

chmod +x deploy.sh && ./deploy.sh

Repository Scripts

    install.sh - Automated bootstrap installer: checks for Docker, clones the repository, makes scripts executable, and triggers the deployment.

    deploy.sh - Full automated installer: pulls the latest vLLM image, creates cache volumes, boots the container, and optionally streams live logs.

    start.sh - Starts the container using optimized vLLM parameters and tool-call parsers.

    start_w_logs.sh - Launches the model and provides an interactive prompt (y/n) to open live server logs.

    stop.sh - Gracefully stops and removes the running container.

Manual Setup & Usage

    Clone the repository:
    Bash

    git clone [https://github.com/yanbo12338/abliterated-qwen-server.git](https://github.com/yanbo12338/abliterated-qwen-server.git)
    cd abliterated-qwen-server

    Make scripts executable:
    Bash

    chmod +x *.sh

    Run for the first time:
    Bash

    ./deploy.sh

    Manage the server:

        Start: ./start.sh or ./start_w_logs.sh

        Stop: ./stop.sh

API Endpoint Reference

Once running, the vLLM server exposes an OpenAI-compatible API at http://localhost:8000/v1.

Test the deployment using curl:
Bash

curl http://localhost:8000/v1/models
