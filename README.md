# Miner Manager for ethOS
This **_OFFICIAL_** miner manager will install, update, or revert these unsupported miners to ethOS version **1.3.3**

### List of currently supported miners [click name to get miner specific information]
- [AMD] - [cast-xmr](https://github.com/glph3k/cast_xmr) - Hard Linked v1.7.1
- [AMD] - [teamredminer](https://bitcointalk.org/index.php?topic=5027811.0) - Latest
- [AMD] - [xcash-amd](https://github.com/X-CASH-official/XCASH_AMD_Miner) - Custom Compiled v1 (miner only, run manually in /opt/miners/xcash-amd/)
- [AMD] - [xmrig-amd](https://github.com/xmrig/xmrig-amd) - Latest
- [AMD] - [wildrig-multi](https://bitcointalk.org/index.php?topic=5023676.0) - Latest
- [NVIDIA] - [cryptodredge](https://bitcointalk.org/index.php?topic=4807821.0) - Latest
- [NVIDIA] - [grin-miner](https://github.com/mimblewimble/grin-miner) - Custom Compiled v1.0.2 (AMD limited to a single GPU)
- [NVIDIA] - [nbminer](https://bitcointalk.org/index.php?topic=5099379.0) - Latest (miner only, run manually in /opt/miners/nbminer/)
- [NVIDIA] - [nodecore-pow-cuda-miner](https://github.com/VeriBlock/nodecore-pow-cuda-miner#command-line-arguments) - Latest (miner only, run manually in /opt/miners/nodecore-pow-cuda-miner/)
- [NVIDIA] - [t-rex](https://bitcointalk.org/index.php?topic=4432704.0) - Latest
- [NVIDIA] - [zilminer](https://github.com/DurianStallSingapore/ZILMiner) - Latest (miner only, run manually in /opt/miners/zilminer/)
- [AMD,NVIDIA] - [bminer](https://www.bminer.me/) - Hard Linked v15
- [AMD,NVIDIA] - [energiminer](https://bitcointalk.org/index.php?topic=4912743.0) - Custom Compiled v2.2.1
- [AMD,NVIDIA] - [gminer](https://github.com/develsoftware/GMinerRelease) - Latest
- [AMD,NVIDIA] - [gringoldminer](https://github.com/mozkomor/GrinGoldMiner) - Latest (miner only, run manually in /opt/miners/gringoldminer/)
- [AMD,NVIDIA] - [grinpro](https://grinpro.io/) - Hard Linked v1.2
- [AMD,NVIDIA] - [lolminer](https://bitcointalk.org/index.php?topic=4724735.0) - Latest
- [AMD,NVIDIA] - [nodecore-pow-amd-cuda-miner](https://github.com/monkins1010/nodecore-pow-AMD-cuda-miner#command-line-arguments) - Custom Compiled v2.0a (miner only, run manually in /opt/miners/nodecore-pow-amd-cuda-miner/)
- [AMD,NVIDIA] - [phoenixminer](https://bitcointalk.org/index.php?topic=2647654.0) - Hard Linked v4.1c
- [AMD,NVIDIA] - [ubqminer](https://bitcointalk.org/index.php?topic=1763606.0) - Latest
- [AMD,NVIDIA] - [xcash-all](https://github.com/X-CASH-official/XCASH_ALL_Miner) - Custom Compiled v1
- [AMD,NVIDIA] - [xmr-stak](https://github.com/fireice-uk/xmr-stak) - Custom Compiled v2.8.3 - hashrate reporting fix for multiple threads
- [AMD,CPU,NVIDIA] - [soliditysha3miner](https://github.com/lwYeo/SoliditySHA3Miner) - Latest

### ONLY ONE ADDITIONAL MINER CAN BE INSTALLED AT A TIME
ethOS files are overwritten for the installation of each miner even though miners can be left in place with (update).
Some miner dependencies will prevent other miners from starting you can completely uninstall a miner using the information [here](README.md#uninstalling).

## Getting Started
Following these instructions will install the chosen miner and its integration files on your ethOS machine. Each miner integration is stored in a branch of github for you to review.

### Prerequisites
You need to be running ethos 1.3.3 to install a miner with this script.

### Installing the miners
This script was designed for ease of use. You can run a single command to install, update, or remove any miner on this repo and any dependencies with it.

[Below](#installing-the-miner-manager-optional) are instructions to install the miner-manager its-self if you think you will use it often, or you can skip installing the manager and just run the script from the github repo in which case the command would look like **NON WORKING EXAMPLE**

`bash <(curl -s https://raw.githubusercontent.com/cynixx3/third-party-miner-installer-for-ethos/master/miner-manager) miner action`

**NOTICE: YOU SET THE LAST TWO WORDS** to what you want to do. Where the miner is the name of the miner branch in this repo and the actions are install, update, or revert
IE for a full **install of phoenixminer example** or an update of all files run:

`bash <(curl -s https://raw.githubusercontent.com/cynixx3/third-party-miner-installer-for-ethos/master/miner-manager) phoenixminer install`

### Updating
The miner can be easily updated when new releases are out by just changing the action argument to "update"
IE to only **update the energiminer example** program to the latest release run:

`bash <(curl -s https://raw.githubusercontent.com/cynixx3/third-party-miner-installer-for-ethos/master/miner-manager) energiminer update`

### UnInstalling
The miner can be easily uninstalled by changing the action argument to "revert"
IE to **uninstall wildrig-multi example** run:

`bash <(curl -s https://raw.githubusercontent.com/cynixx3/third-party-miner-installer-for-ethos/master/miner-manager) wildrig-multi revert`

## ethOS Config Sample
Here is an example of how to add ubqminer to ethos. These instructions will apply to any miner simply by changing "ubqminer" to the miner you want.

### Set the miner
You can use the miner on your local config or globally on a remote config
```
globalminer ubqminer
```
OR in a remote config to set just one rig
```
miner c94e13 ubqminer
```
Where `c94e13` is your EthOS rig hostname. You can get **your** miners hostname by running the terminal command `hostname`

### Set your pool and wallet
for local configs or remote configs to apply globally use
```
proxywallet walletORusername
proxypool1 pool.com:port
proxypool2 pool.com:port
poolpass1 x
poolpass2 x
```
OR to make it specific to this miner program in a remote config
```
ubqminer=proxywallet walletORusername
ubqminer=proxypool1 pool.com:port
ubqminer=proxypool2 pool.com:port
ubqminer=poolpass1 x
ubqminer=poolpass2 x
```
OR to make it specific to this rig
```
rigwallet c94e13 walletORusername
rigpool1 c94e13 pool.com:port
rigpool2 c94e13 pool.com:port
rigpoolpass1 c94e13 x
rigpoolpass2 c94e13 x
```

NOTES:
Some miners allow you to use a single cpu thread, for these you can set
```
globalminer ubqminer-single
```
Some miners depend on a fallback pool, others do not use them. Best practice is to set both to avoid errors.

## Manual config sample
ethOS requires several file changes in order to intergrate a miner into its config and hash reporting features, when this code has not been created you can manually run a miner. In this example we will use grinpro, but you can suppliment it with the miner of your choosing.

First stop ethOS from trying to manage a miner, run `disallow && minestop`, then go to the miner folder `cd /opt/miners/grinpro` and run the miner `./GrinProMiner` to check that its working and to make any firt run configurations. This process will close when you disconnect from ssh and it will not start with ethOS. Exit the miner with the key combination `ctrl+c` 

Once you get the miner to run and know the start command in order to mine add it to custom.sh [nano guide](http://ethosdistro.com/kb/#editing-files)
```
nano /home/ethos/custom.sh
```
Add the following line with the information you discovered, above "exit 0" (you can also start the miner with this command)
```
screen -dmS miner /opt/miners/grinpro/GrinProMiner ignore-config=true stratum-address=eu-west-stratum.grinmint.com stratum-port=4416 stratum-tls=true stratum-login=logina@example.com nvidia=0 amd=0:0 2>&1 /var/run/ethos/miner.output

```
The `2>&1 /var/run/ethos/miner.output` allows you to use `show miner` even in manual mode. Add any miner flags just as your pool or [miner](http://paste.ethosdistro.com/emozeriyog.tex) instructs. That's all you need to do.

Screen is a linux program that runs an interactive terminal session that you can run independently, connect, and disconnect from. To connect to the miner session and interact with it use 
```
screen -x
```
To disconnect from a screen session without killing the miner use the key combination `ctrl+a d` where you press ctrl and a a the same time, release, then press d. Using the ctrl+c key combination will kill the miner, not the screen session and create an interesting situation where rebooting is the easiest fix (alternative is `ctrl+a k y`, checking for live sessions with `screen -ls` and killing them if found, then restarting the miner with the `screen -dmS ...` command above.)

### Installing the miner-manager (optional)
If you plan to use this often you can download the miner-manager script, give it execute permissions. To install simply copy paste the command:
```
sudo wget https://raw.githubusercontent.com/cynixx3/third-party-miner-installer-for-ethos/master/miner-manager -O /usr/bin/miner-manager
sudo chmod +x /usr/bin/miner-manager
```
and use it with `miner-manager miner action` To update the manager script just repeat the first command.

### Farms
You are limited to installing 30 miners an hour as this script makes 2 API querries per install. With authenticated requests you get enough to install on 2,500 miners per hour per user.

See [GitHub API Documentation](https://developer.github.com/v3/#rate-limiting) for more information.

To authenticate, simply either use a file (/home/ethos/.gituser) or use the variables after installing the manager. These environmental variables are currently:

- GITHUB_USERNAME
- GITHUB_PASSWORD

## Development
If you are a developer please check the [developers](https://github.com/cynixx3/third-party-miner-installer-for-ethos/blob/master/DEVELOPERS.md) guide for information on how to add your miner to ethos and / or this repo.

### Contributing
Any setting changes to the miner-manager (like an updated release) should be made to the miner.settings file in each miners branch of this repo.

If you got a new miner working using these tools or just improved an intergration please submit a pull request with a new branch for the miner you added.

## Authors
* **cYnIxX3** - *Initial work* - [cYnIxX3](https://github.com/cynixx3) <== MVP
~~~
~ If you found this script useful please donate BitCoin to:
~ BTC 1G6DcU8GrK1JuXWEJ4CZL2cLyCT57r6en2
~ or Ethereum to:
~ ETH 0x42D23fC535af25babbbB0337Cf45dF8a54e43C37
~~~

### Contributors
* **unsivil** - *added and integrated several miners* - [unsivilaudio](https://github.com/unsivilaudio)
* **Kahlid74** - *added cryptodredge* - [Phaelon74](https://github.com/phaelon74)
* **virusHQ** - *ported ubqminer* - [virusHQ](https://github.com/VirusHQ/ethos-ubqminer)
* **amnesium** - *ported grin-miner* - [amnesium](https://github.com/amnesium/grin-miner-ethos)
* **asluchevskiy** - *ported t-rex* - [asluchevskiy](https://github.com/asluchevskiy/ethos-t-rex)
* **Virosa** - *improved grin-miner, added bminer* - [Virosa](https://github.com/Virosa)
* **HTCang** - *ported gminer* - [HTCang](https://github.com/htcang)

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
