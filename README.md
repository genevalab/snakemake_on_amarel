# Snakemake on Amarel
Workshop on using the Snakemake workflow system on Amarel

Today we will be familiarizing ourselves with the basics of Snakemake, a workflow management system that enables reliable, scalable, and reproducible scientific workflows. Use of workflow managers is becoming [increasingly common in Computational Biology](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1010705). We’ll work through a Software Carpentry tutorial to build a Snakemake workflow to perform a basic bioinformatics analysis.

Upon completion of the workshop students will have:
1. Gained a familiarity with the use and benefits of workflow management systems generally and Snakemake specifically
2. Completed a worked example using Snakemake to manage and perform basic bioinformatics analyses
3. Learned about extensions and options in Snakemake that could apply to their coding/scripting

Aside from the initial setup modifications listed below, we will be following this tutorial from [Software Carpentries](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/).

# Getting started
The Software Carpentry tutorial was written assuming a linux workstation, therefore we have to make a few modifications in order to get started using Snakemake on Amarel. The next few sections replace the ["Summary and Setup"](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/index.html) instructions on the Carpentries tutorial. 

## First we need to connect to amarel and set up conda
Since everyone who signed up for this workshop already has an amarel account we only need to get connected via ssh. If you use a mac open terminal if on a PC use whichever tool you typically use to start an ssh session (putty, openssh, etc). Now connect using the command/address below, replacing [YOUR_NETID] with your actual netID. NOTE: we are using the ```amarelc``` login node today due to OARC maintenance. Trying to connect to other login nodes may fail.

```ssh [YOUR_NETID]@amarelc@hpc.rutgers.edu```

Once logged in, confirm you have an active conda install in your home directory by typing ```which conda```. Yours need not be an exact match to mine, but the output from that command should look something like```/projects/community/anaconda/2023.10/bd387/base/bin/conda```. If it does, then you have conda installed. If it doesn't, then you will need to set up conda before proceeding.

For those who need to install conda, I have laid out the steps to installing conda in your home directory [here](https://github.com/lizardroom/conda_on_amarel). Go to that repo, follow all the steps and return to this page to continue.

## Now that we have conda set up, we need to create an environment for the workshop
I'm simply transposing the instructions from Software Carpentry here, for convenience. Feel free to switch over to the that page at any time.

#### First establish some settings for conda
We are going to edit the file ```~/.condarc``` in your home directory. If you just installed conda today this file will either not exist yet, or be empty. If you are an experienced conda user, you may already have settings established in this file. If you have anything else currently in that file, comment it out by adding ```#``` to the start of each line. 

To edit ```~/.condarc``` type:

``` nano ~/.condarc```

Now add this text to your ```~/.condarc``` file:

```
channels:
  - conda-forge
  - bioconda
solver: libmamba
channel_priority: strict
```
Exit conda by hitting ```Ctrl + X``` and save by typing ```Y``` and hitting ```Enter```.

#### Now we can download the YAML file containing environment details

```wget https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/files/conda_env.yaml```

#### Next create the environment detailed in our YAML

```conda env update --file conda_env.yaml```

#### This might take a minute, but when its done you can check if the environment was successfully created by activating it
```conda activate snakemake_carpentry```

#### If that worked, great! If not, ask for help as we'll need to get everyone to this point before proceeding. Once you've confirmed your environment is all set, you can deactivate it for now by running:

```conda deactivate```


## Final setup steps
#### Setting up your text editor
We'll be using a linux text editor to create and edit files on Amarel. The Carpentries tutorial mentions two, but on Amarel we only have access to ```nano``` so we'll use that one. It also gives instructions on how to encode configuration changes to the appearance of nano. You are welcome to make those changes to the nano configuration file (```~/.nanorc```), but I would suggest just loading plain, vanilla nano. If you want to use the options from the Carpentries tutorial, you can use the options below, which will make your nano editor appear the same as the tutorial without changing the configuration of your nano environment.

```nano -wiSOE -T 4 -Y python [FILE_YOU_WANT_TO_CREATE_OR_EDIT]```

#### Downloading data for the tutorial
The data for this tutorial is part of this repository, but to make it easier I am hosting it on Dropbox. You can download it to your home directory and unpack it via the following commands.

```
wget https://www.dropbox.com/scl/fi/n5prma461wvugxq6okjkh/data-for-snakemake-novice-bioinformatics.tar.xz
tar -xvaf data-for-snakemake-novice-bioinformatics.tar.xz
```

You should now have a directory called ```snakemake_data``` in your home directory

#### Starting an interactive session  
We're about to start actually working with the data, and so we should move our operations off the login node and onto a compute node. We are going to request interactive resources from the ```cmain``` partition on Amarel using the following command.

```srun -p cmain --cpus-per-task 1 --mem-per-cpu 10g --time 02:00:00 --reservation=maintenance-202510 --account=ccib --constraint=oarc --pty bash```

It might take a few seconds to a minute for you to be allocated resources.

#### Activate your environment inside your interactive session
The final preparation step is to activate our snakemake environment again, this time inside the interactive session we just created.

```conda activate snakemake_carpentry```

## Ok, we are done with the Amarel specific changes
Go to [Episode 1](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/01-introduction.html) of the Carpentries tutorial and being the exercises.
