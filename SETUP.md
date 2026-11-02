# Set up your lab: Linux for AI-ML Systems

When you finish, you will have a real Linux terminal with the course labs ready for Modules 1 to 3: a model server to explore, a training job to rescue and an inference server to keep alive. It takes about 10 minutes, one time.

## What you need

- A Linux shell. Any computer works: GitHub Codespaces in your browser, WSL Ubuntu on Windows, or a Multipass Ubuntu VM on a Mac.
- A free GitHub account, if you use Codespaces.
- Python 3 and git. Both are already on Codespaces and Ubuntu 24.04. The labs use only bash, Python 3 and standard Linux tools, so there is nothing to `pip install`.
- About 1 GB of free disk. The labs are scaled down on purpose: 1 MB in the lab stands for 1 GB on a real server.
- **No GPU needed.** Module 3 reads a sample `nvidia-smi` output instead.
- **No API keys needed.** The token in Module 2 is a fake lab token.

## Step 1 · Pick where to run it

### Option A: GitHub Codespaces (easiest, any computer)
1. Sign in to github.com and open this repo.
2. Click **Code > Codespaces > Create codespace on main**.
3. Wait about a minute for the terminal at the bottom. Python 3 and git are already installed.

### Option B: Windows (WSL / Ubuntu)
1. Open **PowerShell as Administrator** and run:
```powershell
wsl --install -d Ubuntu-24.04
```
2. Restart your computer, then open **Ubuntu** from the Start menu and create a Linux username and password.
3. Install the tools:
```bash
sudo apt update
sudo apt install -y git unzip python3
```

### Option C: Mac (Multipass VM)
1. Install Homebrew first (https://brew.sh), then Multipass, and start an Ubuntu VM:
```bash
brew install --cask multipass
multipass launch 24.04 --name ailab
multipass shell ailab
```
2. Inside the VM, install the tools:
```bash
sudo apt update
sudo apt install -y git unzip python3
```

## Step 2 · Get the lab files

Download [linux-for-ai-ml-lab.zip](downloads/linux-for-ai-ml-lab.zip) from the `downloads/` folder of this repo. Put it in your Linux home folder:

- **Codespaces:** the file is already there. Run `cp downloads/linux-for-ai-ml-lab.zip ~`
- **WSL:** your Windows Downloads folder is visible from Ubuntu. Change `YOURNAME` to your Windows user name:
```bash
cp /mnt/c/Users/YOURNAME/Downloads/linux-for-ai-ml-lab.zip ~
```
- **Mac with Multipass:** run this on your Mac, not inside the VM:
```bash
multipass transfer ~/Downloads/linux-for-ai-ml-lab.zip ailab:
```

Then unzip it and go into the folder:
```bash
cd ~
unzip linux-for-ai-ml-lab.zip
cd linux-for-ai-ml
```

## Step 3 · Install and check

There is nothing else to install. Run the health check from the `linux-for-ai-ml` folder:

```bash
bash setup/doctor.sh
```

You should see `[ OK ]` lines for the Linux kernel, the distro, your shell, Python 3, git and free disk, then `No GPU here - that's fine. Module 3 uses a sample nvidia-smi file.` and `If every line says OK, you are ready.` If a line says `[WARN]`, the fix is printed on the same line.

## Step 4 · Quick test for each module

Start each test from the `linux-for-ai-ml` folder (`cd ~/linux-for-ai-ml`).

**Module 1 · The Machine Under Your Model**
```bash
cd modules/module-1/scripts && python3 make_server.py && cd ~/ai-server && cat README-FIRST.txt
du -sh * | sort -h
```
You should see `Built /home/<you>/ai-server`, then `Your mission: find three problems.` The size list ends with `25M checkpoints` and `39M models`. You will solve the three missions in the session.

**Module 2 · Feed the Model**
```bash
cd modules/module-2/scripts && python3 make_job.py && cd ~/train-job && python3 train.py
```
You should see `PRE-FLIGHT  Space - Owner - Secret`, then three `FAIL` lines (SPACE, OWNER, SECRET) and `Pre-flight failed.` That is correct: this job is broken on purpose, and you fix it in the session.

**Module 3 · Keep It Running**
```bash
cd modules/module-3/scripts
python3 serve.py &
python3 load.py --requests 2 --tokens 1000
kill $(cat server.pid)
tail -1 logs/server.log
```
You should see `serve.py running as PID ... on http://127.0.0.1:8080`, then `request  1: ok   cache=8 MB` and `request  2: ok   cache=16 MB`. The last log line ends with `shutting down cleanly`. Press Enter if your prompt looks stuck.

To start Module 1 or 2 over, run its script again with `--reset`, for example `python3 make_server.py --reset`.

## If something goes wrong

- **`[WARN] Not Linux`**: you are on plain macOS or Windows. Use Codespaces, WSL or Multipass (Step 1).
- **`python3 missing` or `git missing`**: run `sudo apt install -y python3 git`, as the doctor suggests.
- **`unzip: command not found`** or **`cannot find linux-for-ai-ml-lab.zip`**: run `sudo apt install -y unzip`, and check the zip is in your home folder with `ls ~`.
- **`... already exists. Use --reset to rebuild it.`**: the lab was built before. Add `--reset` to rebuild it fresh.
- **Module 3 `request 1: FAILED ... is the server still running?`** or **`Address already in use`**: start `python3 serve.py &` first, or stop an old one with `kill $(cat server.pid)` in `modules/module-3/scripts`.
- **Stuck for 15 minutes?** Switch to Codespaces. It runs in your browser, and the course works the same there.

## Official guides

- GitHub Codespaces: https://docs.github.com/codespaces
- Install WSL (Microsoft): https://learn.microsoft.com/windows/wsl/install
- Ubuntu on WSL (Canonical): https://documentation.ubuntu.com/wsl
- Install Multipass (Canonical): https://canonical.com/multipass/install
- Homebrew: https://brew.sh
