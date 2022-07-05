# experiment-run-jupyterlab-on-sherlock
How might I run an interactive jupyterlab session on Sherlock?

```shell
module load physics gdal
module load python/3.9.0
python3 -m venv pyenv
source pyenv/bin/activate
pip install jupyter jupyterlab
jupyter lab --ip=0.0.0.0 --port=8888

# In my case, applications were already running on this node on port 8888, so I got assigned 8890 instead.
# This is the computer I was running jupyter lab on:
# http://sh03-ln05.stanford.edu:8890/lab?token=000000000000000000000000000000000000000000000000

# In a separate shell:
ssh -L8890:sh03-ln05.stanford.edu:8890 <user>@sh03-ln05.stanford.edu

# Then, point my browser to this to open jupyterlab:
https://127.0.0.1:8890/lab?token=000000000000000000000000000000000000000000000000

# Note that the above networking stuff doesn't need to be over the VPN, but be
sure to keep it consistent throughout the session.  If you start with the VPN
but disconnect partway through, you'll need to re-SSH in to the jupyterlab session.
```
