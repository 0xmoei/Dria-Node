![image](https://github.com/user-attachments/assets/28d801d4-b863-4f55-af14-cdbcc65c10b4)

# Dria Node

## Install Dependecies
```console
# Docker
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo chmod +x /usr/local/bin/docker-compose

# Docker version check
docker --version
```
```
# Ollama
curl -fsSL https://ollama.com/install.sh | sh
```

## Install Dria
```
cd $HOME
curl -L -o dkn-compute-node.zip https://github.com/firstbatchxyz/dkn-compute-launcher/releases/latest/download/dkn-compute-launcher-linux-amd64.zip
```
```
unzip dkn-compute-node.zip
```
```
cd dkn-compute-node
```

## Run Dria Node
```
./dkn-compute-launcher
```
1. Enter your DKN wallet Secret key (Your metamask Private Key without `0x`)
2. Pick a Model


* Before picking your models, Check the team's guide:

> Model types team suggests to complete most tasks:
> 
![Screenshot_386](https://github.com/user-attachments/assets/b87f4a64-4c02-4a8f-b4b9-208f072634d0)


> Model recommendations based on your resource capacity
> 
![Screenshot_387](https://github.com/user-attachments/assets/245da204-9a41-4027-98aa-b14af0c17f64)



* I've picked two models (`Ollama` and `OpenAI`) by writing `3,23`
* `OpenAI` doesn't need system resources and it's only API, if you have chosen it, get your API [here](https://platform.openai.com/api-keys)
* `Ollama` downloads and runs a local model host locally in your server, No cost, but it use your system resources

![Screenshot_390](https://github.com/user-attachments/assets/df7d8096-ff34-4f5a-8a2b-0f2030952506)

3. Skip Jina & Serper API key by pressing Enter

4. Now your node will start Downloading Models files and Testing them
**each model must pass its test and it only depends on your system specification**

> Error: If you had any **port** conflicts, you must change the ports in `.env` file or use this: `nano $HOME/dkn-compute-node/.env`

When the Node started logging, Head back to the first lines of the logs and check if both `Ollama` and `OpenAI` passed their tests and see their name in front of `using models` like mine in the following picture:

![Screenshot_389](https://github.com/user-attachments/assets/7d016234-817e-4eef-9542-e256b4f68b7c)

*If you didn't pass any of the Models:*
> - I've chosen lightest `Ollama` model but if it didn't pass the test for you, you can ignore and continue using `OpenAI`
> 
> - Since I wanted to use `Ollama` too because it's free, so I had to stop some of my other running dockers, then restart the Dria script to pass the test (Testing `Ollama` highly depends on your system resources, after testing is passed, it keeps running with very low resources)
> 
> - If you wanted to restart the node to *change* Models, you can clear `DKN_MODELS=` variable in `.env` file or use `nano $HOME/dkn-compute-node/.env`, then rerun Dria using `./dkn-compute-launcher`
>   
> 

## Re-run Dria Node
Now you ensured that your Models passed the test and your node is running, you should re-run your node to start it in a screen. press `Ctrl+C` and exit the node

```
screen -S dria
```
```
./dkn-compute-launcher
```

![image](https://github.com/user-attachments/assets/7ca9f116-50e5-4649-b924-ba4c37b7832c)

![image](https://github.com/user-attachments/assets/5582a204-c232-4f31-9c9f-d215cd0004f3)

You can minimze the screen with `CTRL+A+D`


## Earn Node-Keeper Role
Join [Discord](https://discord.gg/dria) and Fill the [Form](https://docs.google.com/forms/d/e/1FAIpQLSeK090ejc4dg5x1ztb_yAOxGz5o1V8JUqDa-o3AwV1Lq7NpMA/viewform
) to receive role

![image](https://github.com/user-attachments/assets/4850511f-e9f7-4d5a-9270-2a2613439cc1)

#

They will soon add a dashboard to track your progress


To open your screen:`screen -r dria`
To minimize your screen:`CTRL+A+D`

