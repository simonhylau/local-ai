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

## Adding Stable Diffusion
### Install pyenv on wsl
1. Install prerequest. Run:
   `sudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git`
2. Install pyenv. Run:
   `curl https://pyenv.run | bash`
3. Setup pyenv. Run:
   `export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"`
4. Refresh terminal. Run:
   `source .bashrc`
### Install python 3.10
1. Install python 3.10 for pyenv. Run:
   `pyenv install 3.10`
2. Set python 3.10 as default. Run:
   `pyenv global 3.10`

### Install AUTOMATIC1111
1. Create directory. Run:
   `mkdir stabledeffusion`
2. Run:
   `cd stabledeffusion`
3. Download installer. Run:
   `wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh`
4. Make it executable. Run:
   `chmod +x webui.sh`
5. Start install. Run:
   `./webui.sh --listen --api`
6. Browse http://127.0.0.1:7860/ to generate images locally. 
### Add AUTOMATIC1111 to Open WebUI
1. Go to the Admin Panel in Open WebUI.
2. Select Settings -> Images.
3. Choose AUTOMATIC1111 for the Image Generation Engine.
4. Enter http://127.0.0.1:7860/ for the Base URL.
5. Check the Image Generation (Experimental) option.
6. Done! You should now see the image generation icon in the chat.

   

