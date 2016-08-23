---
layout: page
---

### V-1. Download example dataset and notebooks

- Login to FLUX and set up the same path we used yesterday when exploring genomic data formats
  <pre>
  export PATH=/home/hmkang/bioboot/bin:${PATH} 
  export PATH=/scratch/biobootcamp_fluxod/remills/anaconda/bin:${PATH}

- Navigate to your bootcamp scratch directory (cd /scratch/biobootcamp_fluxod/UNIQUENAME). If a directory with your uniquename does not exist, make it using

  <pre>
  mkdir /scratch/biobootcamp_fluxod/UNIQUENAME
  cd /scratch/biobootcamp_fluxod/UNIQUENAME
  
- Once in your directory, create a subdirectory for today's segment

  <pre>
  mkdir day4_cluster
  cd day4_cluster
  </pre>

- download the [data](https://github.com/bioboot/web-2016/raw/gh-pages/class-material/read_counts_by_region.tar.gz) for today to FLUX
  - Note that you can view a render of this [notebook](https://github.com/bioboot/web-2016/blob/gh-pages/class-material/read_counts_by_region.ipynb) directly on GitHub as well!

  <pre>
  wget https://github.com/bioboot/web-2016/raw/gh-pages/class-material/read_counts_by_region.tar.gz
  tar zxvf read_counts_by_region.tar.gz
  cd read_counts_by_region
  </pre>

- For this exercise, we will need to run Jupyter notebook on flux. Typically, you would need to start the notebook as a FLUX job, take note of the hostname and IP address, and set up an SSH tunnel to be able to use the notebook on your local computer. However, we can now make use of an internal University of Michigan tool called [ARC Connect](https://connect.arc-ts.umich.edu/) to do of all of this far us. Navigate to this URL and login with your UM account. When prompted, complete the 2-factor authentication. From the ARC Connect screen, choose:

  - Select *biobootcamp_fluxod* under Account
  - Select *Jupyter Notebook* under Sesson type.
  - All other values can remain at default
  - Press *Submit your job* and wait for it to be allocated (it might take a few minutes)
 
- Once the session is active, press *Open in Browser* to being your Jupyter session. Click on the "House" to take you to the root directory and navigate to to the folder you made earlier, /scratch/biobootcamp_fluxod/UNIQUENAME/day4_cluster/read_counts_by_region/ and load *read_counts_by_region.ipynb*. 

- Ipython notebook reminders:

  - Green box  - marks active cell. You are in EDIT mode.
  - Hit **escape** to exit mode mode and go to COMMAND mode.
  - In command mode:
    - **A** : insert new cell above
    - **B** : insert new cell below
    - **Enter** : edit the currently selected cell
    - **up/down arrow** : navigate up or down
  - In either:
    - **Shift-Enter** : run the current cell

  - Remember, you can run commands out of order in the notebook.
___
### For situations outside of UM where ARC Connect is not available, we have provided instructions for using SSH tunneling, as reference:

  - Start a notebook server 
  - Notes:
    1. you need to know which host you're on.   The command line prompt will show this (e.g., <B>flux-login3</B>)
    2. you need to know which port your instance of ipython listens to.  The first few lines of output from ipython notebook will list this for you.

  <pre>
  remills@<b>flux-login3</b>:/scratch/biobootcamp_fluxod/remills/biobootcamp$ ipython notebook --ip=<B>flux-login3</b> --no-browser

  [I 13:26:18.660 NotebookApp] Using MathJax from CDN: https://cdn.mathjax.org/mathjax/latest/MathJax.js
  [I 13:26:19.220 NotebookApp] The port 8888 is already in use, trying another random port.
  [I 13:26:19.473 NotebookApp] Serving notebooks from local directory: /scratch/biobootcamp_fluxod/kitzmanj
  [I 13:26:19.473 NotebookApp] 0 active kernels
  [I 13:26:19.473 NotebookApp] The IPython Notebook is running at: http://flux-login3:<b>8889</b>/
  [I 13:26:19.473 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
  </pre>

  - A word of warning: in general, running on the head node of the flux cluster is not a good practice, because the head node controls the job queue for the entire cluster. Instead you would want to enter the queue, login to a compute node, and do your work there.

  - Now, your own ipython server is running on flux.  But you will need to open a tunnel to get there.  The below command will securely connect port 8889 on the computer flux-login3 to port 9000 on my computer. 

   <pre>
   ssh -L localhost:9000:<b>flux-login3:8889</b> YOURNAME@flux-login.engin.umich.edu
   </pre>

  - Navigate to http://localhost:9000 and make a new notebook


