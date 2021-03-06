Scripts to setup a basic BLAST setup on a Jupyter server
========================================================

Outline:
1. Start a GCE instance
2. Set up the instance, run Jupyter notebook server
3. Open your Jupyter notebook on colab.research.google and connect it to a
   local runtime (i.e.: your GCE instance)


## 2. Set up instance
1. [`setup-blast.sh`](setup-blast.sh): Installs latest version of BLAST.
1. [`setup-aux-tools.sh`](setup-aux-tools.sh): Installs some helpful tools to
   run BLAST efficiently.
1. [`get-queries.sh`](get-queries.sh): Get sample query sequences from GCP, installs in `/blast/queries/contigs`.
1. [`get-blastdbs.sh`](get-blastdbs.sh): Installs BLAST databases in `/blast/db`
1. [`setup-jupyter-on-gce.sh`](setup-jupyter-on-gce.sh): Set up and Jupyter server on your instance 

## 3. ... Connect your colab.research.google to your Jupyter notebook server

1. Start jupyter server (if not done already): [`run-jupyter-on-gce.sh`](run-jupyter-on-gce.sh).
1. On your local machine, create an ssh tunnel, and then click on 'Connect to local runtime' (top right of the page in `colab.research.google`).

### How to set up the ssh tunnel?
* `ssh $IP -L 8888:localhost:8888`, or 
* `gcloud compute ssh --zone YOUR_ZONE YOUR_INSTANCE_NAME -- -L 8888:localhost:8888`    

* Authenticate: click on a link that looks like the one below (this is the
  output of step 3.1)
  http://localhost:8888/?token=6a79bffd168062a2254fa4731274d46730d13dee952478fc
    
Full instructions: https://research.google.com/colaboratory/local-runtimes.html
