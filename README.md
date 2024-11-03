# Local AI Installation

## Running AI from the Command Line

1.  On Windows, open the command prompt and run: `wsl --install`.
2.  Go to [https://ollama.com/download/linux](https://ollama.com/download/linux) to get the following command to install Ollama.
3.  Run:  
    `curl -fsSL https://ollama.com/install.sh | sh`
4.  Download the AI model:  
    `ollama pull llama2`  
    You can also download other models from [https://ollama.com/library](https://ollama.com/library), e.g., `ollama pull llama3.2`.
5.  Run the model:  
    `ollama run llama2`
6.  Done! You can now start using the AI.

## Installing the UI

1.  Install Docker in WSL. Follow the steps at Docker's documentation for Ubuntu. `docker pull ghcr.io/open-webui/open-webui:git-5ae6d05` ([https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)).
2.  Install Open WebUI:  
    `sudo docker pull ghcr.io/open-webui/open-webui`
    Reference: Open WebUI GitHub Repository ([https://github.com/open-webui/open-webui/pkgs/container/open-webui](https://github.com/open-webui/open-webui/pkgs/container/open-webui))
3.  Run the following command to start Open WebUI:  
    `sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:git-5ae6d05`
    
4.  Open your browser and go to [http://127.0.0.1:8080/](http://127.0.0.1:8080/), then create an admin account.
5.  If you have multiple models installed, you can select them from the top menu.
6.  Done!

## Monitoring NVIDIA Loading

1.  Start WSL with the Ubuntu distribution:  
    `wsl -d Ubuntu`
2.  Run the following command to watch GPU usage:  
    `watch -n 0.5 nvidia-smi`
