# pybombs-x310-radio-redo-test
Custom Pybombs(2.0) Recipes

##Purpose
This repo is currently for testing the install of the  (rfnoc-)radio-redo branches of gr-ettus (and optionally uhd), along with (the maint branch of) gnuradio to be used in conjunction with the Ettus USRP X310.

This repository will not be maintained, and should be ignored, really.
Instead, For something that works, see the references at the bottom.


##Recipes
| File | Description |
| ----------------------- | ------------------------------------------------------------------------------ |
|x310-rfnoc-devel-rpc.lwr | assumes you already have the rfnoc-devel branch of UHD installed manually      |
|x310-radio-redo-rpc.lwr  | assumes you already have the rfnoc-radio-redo branch of UHD installed manually |
|x310-radio-redo-all.lwr  | use this one to install all dependencies, or with a custom prefix              |



##Installation (tested on Ubuntu 14.04, 16.04)
######Begin:
```
sudo apt install python-pip
sudo -E pip install git+https://github.com/gnuradio/pybombs.git
pybombs recipes add ettus https://github.com/EttusResearch/ettus-pybombs.git
pybombs recipes add gr-recipes git+https://github.com/gnuradio/gr-recipes.git
pybombs recipes add gr-etcetera git+https://github.com/gnuradio/gr-etcetera.git
pybombs recipes add rpc-github https://github.com/rcollins0618/pybombs-x310-radio-redo-test.git
pybombs config makewidth 8      # or something like 1/2 of $(nproc)
```
######Default Prefix (If UHD (rfnoc-radio-redo) is already installed in default (/usr/local) prefix):
```
sudo pybombs prefix init /usr/local -a radio-redo -R x310-radio-redo-rpc
```
######Custom Prefix (Else, if Custom Prefix desired... (untested, experimental, probably wrong)):
```
mkdir ~/<custom_prefix>
pybombs prefix init ~/<custom_prefix_directory> -a radio-redo -R x310-radio-redo-all
```
######Continue:
```
source <chosen_install_prefix>/setup_env.sh
gnuradio-companion &
```
######Done.


###References

* RFNoC + PyBOMBS:

    [ettus-pybombs](https://github.com/EttusResearch/ettus-pybombs)
    
    [usrp-users, RFNoC + PyBOMBS suggestion](http://permalink.gmane.org/gmane.comp.hardware.usrp.e100/19586)

* PyBOMBS:

    [PyBOMBS README](https://github.com/gnuradio/pybombs/blob/master/README.md)

    [PyBOMBS wiki](http://gnuradio.org/redmine/projects/pybombs/wiki)

    [PyBOMBS Config notes](https://lists.gnu.org/archive/html/discuss-gnuradio/2016-03/msg00537.html)

* RFNoC:

    [Getting Started](https://github.com/EttusResearch/uhd/wiki/RFNoC:-Getting-Started)

    [Ettus KB - RFNoC](https://kb.ettus.com/RFNoC)

    [Ettus KB - RFNoC Getting Started Guide](https://kb.ettus.com/RFNoC_Getting_Started_Guides)

