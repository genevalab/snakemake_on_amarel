# Snakemake on Amarel
Workshop on using the Snakemake workflow system on Amarel

Today we will be familiarizing ourselves with the basics of Snakemake, a workflow management system that enables reliable, scalable, and reproducible scientific workflows. We’ll work through a Software Carpentry tutorial to build a Snakemake workflow to perform a basic bioinformatics analysis.

Upon completion of the workshop students will have:
1. Gained a familiarity with the use and benefits of workflow management systems generally and Snakemake specifically
2. Completed a worked example using Snakemake to manage and perform basic bioinformatics analyses
3. Learned about extensions and options in Snakemake that could apply to their coding/scripting
   
This workshop is suitable for STEM trainees who 1) have a familiarity working with Bash or other command line shell environments and 2) have an active Amarel account prior to the start of the workshop. No familiarity with python, R, or bioinformatics is needed to participate. In this workshop, we will collectively work through a Software Carpentry tutorial in which we will each build a Snakemake workflow to perform some basic bioinformatics analysis.

Aside from the initial setup modifications listed below, we will be following this tutorial from [Software Carpentries](https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/).

# Getting started
The Software Carpentry tutorial was written assuming a linux workstation, therefore we have to make a few modifications in order to get started using Snakemake on Amarel. The next few sections replace the "Summary and Setup" instructions on the Carpentries tutorial. 

## First we need to connect to amarel and set up conda
Since everyone who signed up for this workshop already has an amarel account we only need to get connected via ssh. If you use a mac open terminal if on a PC use whichever tool you typically use to start an ssh session (putty, openssh, etc). Now connect using the command/address below, replacing [YOUR_NETID] with your actual netID. NOTE: we are using the ```amarelc``` login node today due to OARC maintenance. Trying to connect to other login nodes may fail.

```ssh [YOUR_NETID]@amarelc@hpc.rutgers.edu```

Once logged in, confirm you have an active conda install in your home directory by typing ```which conda```. Yours need not be an exact match to mine, but the output from that command should look something like```/projects/community/anaconda/2023.10/bd387/base/bin/conda```. If it does, then you have conda installed. If it doesn't, then you will need to set up conda before proceeding.

For those who need to install conda, I have laid out the steps to installing conda in your home directory [here](https://github.com/lizardroom/conda_on_amarel). Go to that repo, follow all the steps and return to this page to continue.

## Now that we have conda set up, we need to create an environment for the workshop
I'm simply transposing the instructions from Software Carpentry here, for convenience. Feel free to switch over to the that page at any time.

### First download the YAML file containing environment details

```wget https://carpentries-incubator.github.io/snakemake-novice-bioinformatics/files/conda_env.yaml```

### Next create the environment detailed in our YAML

```conda env update --file conda_env.yaml```

### This might take a minute, but when its done you can check if the environment was successfully created by activating it
```conda activate snakemake_carpentry```

If that worked, great! If not, ask for help as we'll need to get everyone to this point before proceeding. Once you've confirmed your environment is all set, you can deactivate it for now by running:

```conda deactivate```


###

