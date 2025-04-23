# A VSCode devcontainer to play with Zenoh

Prerequisites on your host:

  - Visual Studio Code
  - Docker
  - Git

## Setup

Clone this repo with its submodules:

```bash
git clone --recursive https://github.com/JEnoch/zenoh_devcontainer.git
```

Open the cloned directory with Visual Studio Code.  
A notification should appear at the bottom right of VSCode proposing to reopen the project in a container - click on it. If the notification doesn't show up, click on the blue icon with `><` symbols in the bottom left corner and choose "repoen in a container" in the proposed commands.

VSCode will download a Ubuntu Docker image, install Zenoh in it and create a container with the project directory mounted as `/workspaces/zenoh_devcontainer`.  
Open one or more `bash` terminal in VSCode to play with Zenoh.


## Running the Zenoh router

In a `bash` terminal run:

```bash
zenohd
```

By default the router listens on TCP port 7447. The Docker container is configured to forward this port to your host.

## Running the Python examples

Open as many `bash` terminal examples as you want and run `cd zenoh-python/examples/` in each.  
Then run one of the `z_*.py` script per-terminal. For instance:

```bash
python3 z_sub.py
```

```bash
python3 z_pub.py
```

## Building and running the C examples

In a `bash` terminal, run:
```bash
cd /workspaces/zenoh_devcontainer/
mkdir build
cd build
cmake ../zenoh-c/examples
cmake --build .
```

Then run the examples built in this directory. For instance:

```bash
./z_sub
```

```bash
./z_pub
```
